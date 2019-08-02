---
title: Краткое руководство по созданию прогнозной модели с помощью языка R
description: В этом кратком руководстве описано, как создать модель на языке R с помощью SQL Server данных для построения прогнозов.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f902bd7325e84f07d50196c19338d9c05b3503d8
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715445"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>Краткое руководство. Создание прогнозной модели с помощью R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы узнаете, как обучить модель с помощью R, а затем сохранить модель в таблице в SQL Server. Модель — это простая обобщенная линейная модель (GLM), которая прогнозирует вероятность того, что транспортный автомобиль передается вручную. Вы будете использовать набор `mtcars` данных, входящий в состав R.

## <a name="prerequisites"></a>предварительные требования

Предыдущее краткое руководство, [Проверка наличия R в SQL Server](quickstart-r-verify.md), содержит сведения и ссылки для настройки среды R, необходимой для этого краткого руководства.

## <a name="create-the-source-data"></a>Создание исходных данных

Сначала необходимо создать таблицу, чтобы сохранить данные для обучения.

```sql
CREATE TABLE dbo.MTCars(
    mpg decimal(10, 1) NOT NULL,
    cyl int NOT NULL,
    disp decimal(10, 1) NOT NULL,
    hp int NOT NULL,
    drat decimal(10, 2) NOT NULL,
    wt decimal(10, 3) NOT NULL,
    qsec decimal(10, 2) NOT NULL,
    vs int NOT NULL,
    am int NOT NULL,
    gear int NOT NULL,
    carb int NOT NULL
);
```

Затем вставьте данные из сборки в набор данных `mtcars`.

```SQL
INSERT INTO dbo.MTCars
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'MTCars <- mtcars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'MTCars';
```

+ Некоторые пользователи предпочитает использовать временные таблицы, но имейте в виду, что некоторые клиенты R отключают сеансы между пакетами.

+ В среду выполнения R включено множество наборов данных (больших и маленьких). Чтобы получить список наборов данных, установленных с R, введите `library(help="datasets")` в командной строке R.

## <a name="create-a-model"></a>Создание модели

Данные о скорости автомобиля содержат два столбца: numeric, лошадиные (`hp`) и Weight (`wt`). На основе этих данных вы создадите обобщенную линейную модель (GLM), которая оценивает вероятность того, что транспортный автомобиль перемещается вручную.

Чтобы построить модель, необходимо определить формулу в коде R и передать данные в качестве входного параметра.

```sql
DROP PROCEDURE IF EXISTS generate_GLM;
GO
CREATE PROCEDURE generate_GLM
AS
BEGIN
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'carsModel <- glm(formula = am ~ hp + wt, data = MTCarsData, family = binomial);
        trained_model <- data.frame(payload = as.raw(serialize(carsModel, connection=NULL)));'
    , @input_data_1 = N'SELECT hp, wt, am FROM MTCars'
    , @input_data_1_name = N'MTCarsData'
    , @output_data_1_name = N'trained_model'
    WITH RESULT SETS ((model VARBINARY(max)));
END;
GO
```

+ Первым аргументом для `glm` является параметр *формулы* , который `am` `hp + wt`определяет, как зависит от.
+ Входные данные хранятся в переменной `MTCarsData`, которая заполняется SQL-запросом. Если вы не присвоите имя входным данным, по умолчанию будет использоваться имя переменной _InputDataSet_.

## <a name="create-a-table-for-the-model"></a>Создание таблицы для модели

Затем сохраните модель, чтобы ее можно было переучить или использовать для прогнозирования. Выходные данные пакета R, с помощью которого создается модель, обычно являются **двоичным объектом**. Таким образом, таблица, в которой хранится модель, должна содержать столбец типа **varbinary (max)** .

```sql
CREATE TABLE GLM_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
```

## <a name="save-the-model"></a>Сохранение модели

Для сохранения модели выполните приведенную ниже инструкцию Transact-SQL, чтобы вызвать хранимую процедуру, создать модель и сохранить ее в таблице.

```sql
INSERT INTO GLM_models(model)
EXEC generate_GLM;
```

Обратите внимание, что при повторном выполнении этого кода возникает такая ошибка:

```sql
Violation of PRIMARY KEY constraint...Cannot insert duplicate key in object dbo.stopping_distance_models
```

Чтобы предотвратить данную ошибку, изменяйте имя для каждой новой модели. Например, вы можете изменить имя на более описательное, а также включить тип модели, день ее создания и т. д.

```sql
UPDATE GLM_models
SET model_name = 'GLM_' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
WHERE model_name = 'default model'
```

## <a name="next-steps"></a>Следующие шаги

Теперь, когда у вас есть модель, в окончательном кратком руководстве вы узнаете, как создавать прогнозы и отображать результаты.

> [!div class="nextstepaction"]
> [QuickStart Прогнозирование и построение из модели](quickstart-r-predict-from-model.md)