---
title: Краткое руководство по созданию прогнозную модель с помощью языка R в SQL Server машинного обучения | Документация Майкрософт
description: В этом кратком руководстве вы научитесь создавать модели на языке R, используя данные SQL Server, чтобы построить прогнозов.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7ca2fcac5bef63a4abf2449b56c25a600b9255c3
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086826"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>Краткое руководство: Создание модели прогнозирования с помощью языка R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве будет показан процесс обучения модели с помощью R и затем сохранить модель в таблицу в SQL Server. Мы будем использовать простую модель регрессии, которая может прогнозировать тормозную дистанцию автомобиля на основе его скорости. Вы будете использовать `cars` набора данных, включенных в R, так как он является небольшим и простым для понимания.

## <a name="prerequisites"></a>предварительные требования

Предыдущего краткого руководства, [Hello World в R и SQL](rtsql-using-r-code-in-transact-sql-quickstart.md), сведения и ссылки по настройке среды R, необходимые для этого краткого руководства.

## <a name="create-the-source-data"></a>Создание исходных данных

Сначала необходимо создать таблицу, чтобы сохранить данные для обучения.

```sql
CREATE TABLE CarSpeed ([speed] int not null, [distance] int not null)
INSERT INTO CarSpeed
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'car_speed <- cars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'car_speed'
```

+ Иногда полезно использовать временные таблицы, но имейте в виду, что некоторые клиенты R отключать сеансы между пакетами.

+ В среду выполнения R включено множество наборов данных (больших и маленьких). Чтобы получить список наборов данных, установленных с R, введите `library(help="datasets")` в командной строке R.

## <a name="create-a-regression-model"></a>Создание модели регрессии

Данные о скорости автомобиля содержат два численных столбца — `dist` и `speed`. В них указаны значения для разных скоростей. С помощью этих данных вы создадите модель линейной регрессии, описывающую связь между скоростью автомобиля и дистанцией торможения.

Требования к созданию линейной модели несложные.

+ Определите формулу, отображающую связь между зависимой (`speed`) и независимой переменной (`distance`).

+ Предоставьте входные данные, которые будут использоваться для обучения модели.

> [!TIP]
> Если вам требуется средство обновления линейных моделей, мы рекомендуем это руководство, в котором описывается процесс компоновки модели с помощью функции rxLinMod: [компоновке линейных моделей](https://docs.microsoft.com/r-server/r/how-to-revoscaler-linear-model)

Чтобы создать модель, необходимо определить формулу внутри кода R, а затем передать данные в качестве входных параметров.

```sql
DROP PROCEDURE IF EXISTS generate_linear_model;
GO
CREATE PROCEDURE generate_linear_model
AS
BEGIN
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'lrmodel <- rxLinMod(formula = distance ~ speed, data = CarsData);
        trained_model <- data.frame(payload = as.raw(serialize(lrmodel, connection=NULL)));'
    , @input_data_1 = N'SELECT [speed], [distance] FROM CarSpeed'
    , @input_data_1_name = N'CarsData'
    , @output_data_1_name = N'trained_model'
    WITH RESULT SETS ((model varbinary(max)));
END;
GO
```

+ Первый аргумент для функции rxLinMod — это параметр *formula*, где дистанция является значением, зависимым от скорости.
+ Входные данные хранятся в переменной `CarsData`, которая заполняется SQL-запросом. Если вы не присвоите имя входным данным, по умолчанию будет использоваться имя переменной _InputDataSet_.

## <a name="create-a-table-for-storing-the-model"></a>Создание таблицы для хранения модели

Затем сохраните модель, чтобы можно было переобучить и использовать его для прогнозирования. Выходные данные пакета R, с помощью которого создается модель, обычно являются **двоичным объектом**. Это означает, что таблица, в которой хранится модель, должна содержать столбец типа **varbinary**.

```sql
CREATE TABLE stopping_distance_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null);
```

## <a name="save-the-model"></a>Сохранение модели

Для сохранения модели выполните приведенную ниже инструкцию Transact-SQL, чтобы вызвать хранимую процедуру, создать модель и сохранить ее в таблице.

```sql
INSERT INTO stopping_distance_models (model)
EXEC generate_linear_model;
```

Обратите внимание на то, что если вы запустите этот код еще раз, вы получаете эту ошибку:

```
Violation of PRIMARY KEY constraint...Cannot insert duplicate key in object dbo.stopping_distance_models
```

Чтобы предотвратить данную ошибку, изменяйте имя для каждой новой модели. Например, вы можете изменить имя на более описательное, а также включить тип модели, день ее создания и т. д.

```sql
UPDATE stopping_distance_models
SET model_name = 'rxLinMod ' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
WHERE model_name = 'default model'
```

## <a name="output-additional-variables"></a>Дополнительные переменные выходных данных

Обычно выходные данные R из хранимой процедуры [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ограничены одним кадром данных. (Это ограничение может быть снято в будущем.)

Однако в дополнение к кадрам данных могут возвращаться выходные данные других типов, например скалярные переменные.

Предположим, что необходимо обучить модель и сразу же просмотреть таблицу с коэффициентами из нее. Вы можете создать таблицу коэффициентов в качестве основного результирующего набора и вывести обученную модель в переменную SQL. Можно сразу же повторно использовать модель, вызвав переменную, или может сохранить модель в таблицу, как показано ниже.

```sql
DECLARE @model varbinary(max), @modelname varchar(30)
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
        speedmodel <- rxLinMod(distance ~ speed, CarsData)
        modelbin <- serialize(speedmodel, NULL)
        OutputDataSet <- data.frame(coefficients(speedmodel));'
    , @input_data_1 = N'SELECT [speed], [distance] FROM CarSpeed'
    , @input_data_1_name = N'CarsData'
    , @params = N'@modelbin varbinary(max) OUTPUT'
    , @modelbin = @model OUTPUT
    WITH RESULT SETS (([Coefficient] float not null));

-- Save the generated model
INSERT INTO [dbo].[stopping_distance_models] (model_name, model)
VALUES ('latest model', @model)
```

**Результаты**

![rslq_basictut_coefficients](media/rslq-basictut-coefficients.PNG)

### <a name="summary"></a>Сводка

Помните, эти правила для работы с параметрами SQL и переменными R в `sp_execute_external_script`:

+ Все параметры SQL, сопоставленные со скриптом R, необходимо указать по имени в  _\@params_ аргумент.
+ Чтобы вывести какой-либо из этих параметров, добавьте ключевое слово OUTPUT в  _\@params_ списка.
+ Как только вы Перечислите сопоставленные параметры, укажите сопоставление по одной строке, параметров SQL с переменными R сразу же после  _\@params_ списка.

## <a name="next-steps"></a>Следующие шаги

Теперь, когда у вас есть модель, Заключительное краткое руководство, вы узнаете, как для получения прогнозов и отображения результатов.

> [!div class="nextstepaction"]
> [Краткое руководство: Predict and plot и из модели](../tutorials/rtsql-predict-and-plot-from-model.md)