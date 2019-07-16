---
title: Краткое руководство по созданию прогнозную модель с помощью R - машинного обучения SQL Server
description: В этом кратком руководстве вы научитесь создавать модели на языке R, используя данные SQL Server, чтобы построить прогнозов.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: f1eaa39e5f22efbe7bea7a44ac2ce93a5e28205e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962031"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>Краткое руководство. Создание модели прогнозирования с помощью языка R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве будет показан процесс обучения модели с помощью R и затем сохранить модель в таблицу в SQL Server. Модель является простой обобщенную линейную модель (GLM) которая прогнозирует вероятность, что автомобилю был оснащен вручную передачи. Вы будете использовать `mtcars` набора данных, включенных в R.

## <a name="prerequisites"></a>предварительные требования

Предыдущего краткого руководства, [проверьте R в SQL Server существует](quickstart-r-verify.md), сведения и ссылки по настройке среды R, необходимые для этого краткого руководства.

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

Затем вставьте данные из сборки в наборе данных `mtcars`.

```SQL
INSERT INTO dbo.MTCars
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'MTCars <- mtcars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'MTCars';
```

+ Иногда полезно использовать временные таблицы, но имейте в виду, что некоторые клиенты R отключать сеансы между пакетами.

+ В среду выполнения R включено множество наборов данных (больших и маленьких). Чтобы получить список наборов данных, установленных с R, введите `library(help="datasets")` в командной строке R.

## <a name="create-a-model"></a>Создание модели

Данные о скорости автомобиля содержит два столбца, числовые, мощность (`hp`) и вес (`wt`). С помощью этих данных вы создадите обобщенную линейную модель (GLM), которая оценивает вероятность того, что автомобилю был оснащен вручную передачи.

Для построения модели, определить формулу внутри кода R и передать данные в качестве входного параметра.

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

+ Первый аргумент `glm` — *формула* параметр, который определяет `am` как зависимые от `hp + wt`.
+ Входные данные хранятся в переменной `MTCarsData`, которая заполняется SQL-запросом. Если вы не присвоите имя входным данным, по умолчанию будет использоваться имя переменной _InputDataSet_.

## <a name="create-a-table-for-the-model"></a>Создание таблицы для модели

Затем сохраните модель, чтобы можно было переобучить и использовать его для прогнозирования. Выходные данные пакета R, с помощью которого создается модель, обычно являются **двоичным объектом**. Таким образом, таблицы, где хранится модель должна содержать столбец типа **varbinary(max)** типа.

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

Обратите внимание на то, что если вы запустите этот код еще раз, вы получаете эту ошибку:

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

Теперь, когда у вас есть модель, Заключительное краткое руководство, вы узнаете, как для получения прогнозов и отображения результатов.

> [!div class="nextstepaction"]
> [Краткое руководство. Predict and plot из модели и](quickstart-r-predict-from-model.md)