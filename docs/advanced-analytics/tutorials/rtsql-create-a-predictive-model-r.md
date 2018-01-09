---
title: "Создать прогнозную модель (R в быстрый запуск SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
dev_langs:
- R
- SQL
ms.assetid: 6eb78a80-5791-438f-9ca6-d142ab5d9bb1
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 19b041df85b3ee1de97e8b5e62295608786a0f0a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="create-a-predictive-model-r-in-sql-quickstart"></a>Создать прогнозную модель (R в быстрый запуск SQL Server)

На этом этапе вы узнаете, как обучить модель с помощью R, а также как сохранить ее в таблицу в SQL Server. Мы будем использовать простую модель регрессии, которая может прогнозировать тормозную дистанцию автомобиля на основе его скорости. Вы воспользуетесь `cars` набора данных, включенных с помощью R, так как он является небольшим и простым для понимания.

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

+ Некоторые пользователи предпочитают использовать временные таблицы, но имейте в виду, что некоторые клиенты R отключить сеансы между обработкой пакетов.

+ В среду выполнения R включено множество наборов данных (больших и маленьких). Чтобы получить список наборов данных, установленных с R, введите `library(help="datasets")` в командной строке R.

## <a name="create-a-regression-model"></a>Создание модели регрессии

Данные о скорости автомобиля содержат два численных столбца — `dist` и `speed`. В них указаны значения для разных скоростей. С помощью этих данных вы создадите модель линейной регрессии, описывающую связь между скоростью автомобиля и дистанцией торможения.

Требования к созданию линейной модели несложные.

+ Определите формулу, отображающую связь между зависимой (`speed`) и независимой переменной (`distance`).

+ Предоставьте входные данные, которые будут использоваться для обучения модели.

> [!TIP]
> Если вам требуется линейной модели в памяти, рекомендуется это руководство, в котором описывается процесс подгонку модели с помощью rxLinMod: [подгонки линейной модели](https://docs.microsoft.com/r-server/r/how-to-revoscaler-linear-model)

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

Затем сохранить модель для повторного обучения или использовать его для прогноза. Выходные данные пакета R, с помощью которого создается модель, обычно являются **двоичным объектом**. Это означает, что таблица, в которой хранится модель, должна содержать столбец типа **varbinary**.

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

Обратите внимание, что при выполнении этого кода во второй раз, появится эта ошибка.

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

Предположим, что необходимо обучить модель и сразу же просмотреть таблицу с коэффициентами из нее. Вы можете создать таблицу коэффициентов в качестве основного результирующего набора и вывести обученную модель в переменную SQL. Можно немедленно повторно использовать модель, вызвав переменную или модели может сохранять в таблицу, как показано ниже.

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
VALUES (' latest model', @model)
```

**Результаты**

![rslq_basictut_coefficients](media/rslq-basictut-coefficients.PNG)

### <a name="summary"></a>Сводка

Помните, эти правила для работы с параметрами SQL и R переменных в `sp_execute_external_script`:

+ Все параметры SQL, сопоставленный в R-сценария, необходимо указать по имени в  _@params_  аргумент.
+ Чтобы вывести какой-либо из этих параметров, добавьте ключевое слово OUTPUT в список _@params_.
+ Как только вы перечислите сопоставленные параметры, последовательно укажите сопоставление параметров SQL с переменными R сразу же после создания списка _@params_.

## <a name="next-lesson"></a>Следующее занятие

Теперь, когда у вас есть модель, вы узнаете, как использовать ее для получения прогнозов и построить график с результатами.

[Получение прогнозов с помощью модели и построение графика с результатами](../tutorials/rtsql-predict-and-plot-from-model.md)


