---
title: Создание и оценка прогнозной модели в R
titleSuffix: SQL Server Machine Learning Services
description: Создание простой прогнозной модели на языке R с помощью SQL Server Службы машинного обучения, а затем прогнозирование результатов с помощью новых данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9acfe1e546c332801e9a5c1a7d97758053d9a0f4
ms.sourcegitcommit: 8cb26b7dd40280a7403d46ee59a4e57be55ab462
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542126"
---
# <a name="quickstart-create-and-score-a-predictive-model-in-r-with-sql-server-machine-learning-services"></a>Краткое руководство. Создание и оценка прогнозной модели в R с помощью SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы создадите и обучите прогнозную модель с помощью R, сохраните модель в таблицу в экземпляре SQL Server, а затем используйте модель для прогнозирования значений из новых данных с помощью [SQL Server службы машинного обучения](../what-is-sql-server-machine-learning.md).

Вы создадите и выполните две хранимые процедуры, выполняемые в SQL. В первой из них используется набор данных **мткарс** , включенный в R, и формируется простая обобщенная линейная модель (GLM), которая прогнозирует вероятность того, что транспортный автомобиль был перемещен вручную. Вторая процедура предназначена для оценки — она вызывает модель, созданную в первой процедуре, для вывода набора прогнозов на основе новых данных. Поместив код R в хранимую процедуру SQL, операции, содержащиеся в SQL, можно использовать многократно и могут вызываться другими хранимыми процедурами и клиентскими приложениями.

> [!TIP]
> Если вам требуется Обновитель в линейных моделях, воспользуйтесь этим руководством, в котором описывается процесс подбора модели с помощью rxLinMod: [подгонка линейных моделей](/machine-learning-server/r/how-to-revoscaler-linear-model) .

Выполнив это краткое руководство, вы узнаете:

> [!div class="checklist"]
> - Внедрение кода R в хранимую процедуру
> - Передача входных данных в код с помощью входных данных хранимой процедуры
> - Использование хранимых процедур для эксплуатацию моделей

## <a name="prerequisites"></a>предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server с [SQL Server службы машинного обучения](../install/sql-machine-learning-services-windows-install.md) с установленным языком R.

  Ваш экземпляр SQL Server может находиться на виртуальной машине Azure или в локальной среде. Просто имейте в виду, что функция внешних скриптов по умолчанию отключена, поэтому может потребоваться [включить внешние сценарии](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедиться, что **Служба панель запуска SQL Server** запущена перед началом работы.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих скрипты R. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, если они могут подключаться к SQL Server экземпляру и выполнять запрос T-SQL или хранимую процедуру. В этом кратком руководстве используется [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="create-the-model"></a>Создание модели

Для создания модели необходимо создать исходные данные для обучения, создать модель и обучить ее с помощью данных, а затем сохранить модель в базе данных SQL, где ее можно использовать для создания прогнозов с новыми данными.

### <a name="create-the-source-data"></a>Создание исходных данных

1. Откройте среду SSMS, подключитесь к экземпляру SQL Server и откройте новое окно запроса.

1. Создайте таблицу для сохранения обучающих данных.

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

1. Вставьте данные из встроенного набора данных `mtcars`.

   ```SQL
   INSERT INTO dbo.MTCars
   EXEC sp_execute_external_script @language = N'R'
       , @script = N'MTCars <- mtcars;'
       , @input_data_1 = N''
       , @output_data_1_name = N'MTCars';
   ```

   > [!TIP]
   > В среду выполнения R включено множество наборов данных (больших и маленьких). Чтобы получить список наборов данных, установленных с R, введите `library(help="datasets")` из командной строки R.

### <a name="create-and-train-the-model"></a>Создание и обучение модели

Данные о скорости автомобиля содержат два столбца: "мощность" (`hp`) и "вес" (`wt`). На основе этих данных вы создадите обобщенную линейную модель (GLM), которая оценивает вероятность того, что транспортный автомобиль перемещается вручную.

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

- Первым аргументом для `glm` является параметр *формулы* , который определяет `am` в зависимости от `hp + wt`.
- Входные данные хранятся в переменной `MTCarsData`, которая заполняется SQL-запросом. Если вы не присвоите имя входным данным, по умолчанию будет использоваться имя переменной _InputDataSet_.

### <a name="store-the-model-in-the-sql-database"></a>Сохранение модели в базе данных SQL

Затем сохраните модель в базе данных SQL, чтобы ее можно было использовать для прогнозирования или переобучения. 

1. Создайте таблицу для хранения модели.

   Выходные данные пакета R, создающего модель, обычно являются двоичными объектами. Таким образом, таблица, в которой хранится модель, должна содержать столбец типа **varbinary (max)** .

   ```sql
   CREATE TABLE GLM_models (
       model_name varchar(30) not null default('default model') primary key,
       model varbinary(max) not null
   );
   ```

1. Выполните следующую инструкцию Transact-SQL, чтобы вызвать хранимую процедуру, создать модель и сохранить ее в созданной таблице.

   ```sql
   INSERT INTO GLM_models(model)
   EXEC generate_GLM;
   ```

   > [!TIP]
   > Если запустить этот код еще раз, возникнет эта ошибка: "нарушение ограничения ПЕРВИЧного ключа... Не удается вставить дублирующийся ключ в объект dbo. stopping_distance_models. Чтобы предотвратить данную ошибку, изменяйте имя для каждой новой модели. Например, вы можете изменить имя на более описательное, а также включить тип модели, день ее создания и т. д.

     ```sql
     UPDATE GLM_models
     SET model_name = 'GLM_' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
     WHERE model_name = 'default model'
     ```

## <a name="score-new-data-using-the-trained-model"></a>Оценка новых данных с помощью обученной модели

*Оценка* — это термин, используемый для обработки и анализа данных, что означает создание прогнозов, вероятностей или других значений на основе новых данных, поступающих в обученную модель. Модель, созданную в предыдущем разделе, будет использоваться для оценки прогнозов по новым данным.

### <a name="create-a-table-of-new-data"></a>Создать таблицу с новыми данными

Сначала создайте таблицу с новыми данными.

```sql
CREATE TABLE dbo.NewMTCars(
    hp INT NOT NULL
    , wt DECIMAL(10,3) NOT NULL
    , am INT NULL
)
GO

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (110, 2.634)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (72, 3.435)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (220, 5.220)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (120, 2.800)
GO
```

### <a name="predict-manual-transmission"></a>Прогнозирование ручной передачи

Чтобы получить прогнозы на основе модели, напишите сценарий SQL, который выполняет следующие действия:

1. Получение требуемой модели.
1. Получение новых входных данных.
1. Вызов функции прогнозирования R, совместимой с моделью.

Со временем таблица может содержать несколько моделей R, все из которых построены с использованием различных параметров или алгоритмов или обучены по разным подмножествам данных. В этом примере мы будем использовать модель с именем `default model`.

```sql
DECLARE @glmmodel varbinary(max) = 
    (SELECT model FROM dbo.GLM_models WHERE model_name = 'default model');

EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(glmmodel));
            new <- data.frame(NewMTCars);
            predicted.am <- predict(current_model, new, type = "response");
            str(predicted.am);
            OutputDataSet <- cbind(new, predicted.am);
            '
    , @input_data_1 = N'SELECT hp, wt FROM dbo.NewMTCars'
    , @input_data_1_name = N'NewMTCars'
    , @params = N'@glmmodel varbinary(max)'
    , @glmmodel = @glmmodel
WITH RESULT SETS ((new_hp INT, new_wt DECIMAL(10,3), predicted_am DECIMAL(10,3)));
```

Приведенный выше сценарий выполняет следующие действия.

- Используйте инструкцию SELECT для получения одной модели из таблицы и передайте ее в качестве входного параметра.

- После получения модели из таблицы вызовите функцию `unserialize` для модели.

- Примените функцию `predict` с соответствующими аргументами к модели, а также укажите новые входные данные.

> [!NOTE]
> В этом примере функция `str` добавляется на этапе тестирования для проверки схемы данных, возвращаемых из R. Эту инструкцию можно удалить позже.
>
> Имена столбцов, используемые в скрипте R, не обязательно передаются в выходные данные хранимой процедуры. Здесь предложение WITH RESULTs используется для определения новых имен столбцов.

**Результаты**

![Результирующий набор для прогнозирования пропербилити передачи вручную](./media/r-predict-am-resultset.png)

Можно также использовать инструкцию [Predict (Transact-SQL)](../../t-sql/queries/predict-transact-sql.md) для создания прогнозируемого значения или оценки на основе хранимой модели.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о SQL Server Службы машинного обучения см. в следующих статьях:

- [Что такое Службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
