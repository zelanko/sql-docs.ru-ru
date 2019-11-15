---
title: Краткое руководство. Обучение модели в R
titleSuffix: SQL Server Machine Learning Services
description: Создание простой прогнозной модели в R с помощью служб машинного обучения SQL Server с последующим прогнозированием результатов на основе новых данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bd91191a84aac8c245bdcbbe0afd2bf3241aa6b3
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73726517"
---
# <a name="quickstart-create-and-score-a-predictive-model-in-r-with-sql-server-machine-learning-services"></a>Краткое руководство. Создание и оценка модели прогнозов в R с помощью служб машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В этом кратком руководстве вы создадите и обучите прогнозную модель с помощью R, сохраните модель в таблицу в экземпляре SQL Server, а затем используете эту модель для прогнозирования значений на основе новых данных с помощью [служб машинного обучения SQL Server](../what-is-sql-server-machine-learning.md).

Вы создадите и запустите две хранимые процедуры, выполняемые в SQL. В первой из них используется набор данных **mtcars**, входящий в состав R, на основе которого создается простая обобщенная линейная модель (ОЛМ), которая прогнозирует вероятность оснащения автомобиля механической КПП. Вторая процедура предназначена для оценки — она вызывает модель, созданную в первой процедуре, для вывода набора прогнозов на основе новых данных. Поместив код R в хранимую процедуру SQL, вы переносите операции в SQL, благодаря чему они могут многократно использоваться и вызываться другими хранимыми процедурами и клиентскими приложениями.

> [!TIP]
> Если вам требуется средство обновления линейных моделей, ознакомьтесь со следующим руководством, в котором описывается процесс компоновки моделей с помощью функции rxLinMod:  [Fitting Linear Models](/machine-learning-server/r/how-to-revoscaler-linear-model) (Компоновка линейных моделей)

Выполнив это краткое руководство, вы узнаете, как делать следующее.

> [!div class="checklist"]
> - Внедрение кода R в хранимую процедуру
> - Передача входных данных в код с помощью входных данных хранимой процедуры
> - Использование хранимых процедур для эксплуатации моделей

## <a name="prerequisites"></a>предварительные требования

- Для этого краткого руководства требуется доступ к экземпляру SQL Server со [службами машинного обучения SQL Server](../install/sql-machine-learning-services-windows-install.md) и с установленным языком R.

  Экземпляр SQL Server может находиться в виртуальной машине Azure или на локальном компьютере. Обратите внимание, что функция внешних сценариев по умолчанию отключена, поэтому перед началом работы вам может потребоваться [включить ее](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) и убедиться, что **служба панели запуска SQL Server** выполняется.

- Вам также понадобится средство для выполнения SQL-запросов, содержащих сценарии R. Эти сценарии можно выполнять с помощью любого средства управления базами данных или запросов, которые могут подключаться к экземпляру SQL Server и выполнять запросы T-SQL или хранимые процедуры. В этом кратком руководстве используется среда [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="create-the-model"></a>Создание модели

Чтобы создать модель, вам необходимо создать исходные данные для обучения, создать модель и обучить ее с использованием этих данных, а затем сохранить модель в базе данных SQL, где она будет использоваться для создания прогнозов на основе новых данных.

### <a name="create-the-source-data"></a>Создание исходных данных

1. Откройте SSMS, подключитесь к экземпляру SQL Server и откройте окно создания запроса.

1. Создайте таблицу, чтобы сохранить данные для обучения.

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
   > В среду выполнения R включено множество наборов данных (больших и маленьких). Чтобы получить список наборов данных, установленных с R, введите `library(help="datasets")` в командной строке R.

### <a name="create-and-train-the-model"></a>Создание и обучение модели

Данные о скорости автомобиля содержат два численных столбца — мощность в лошадиных силах (`hp`) и масса (`wt`). На основе этих данных вы создадите обобщенную линейную модель (ОЛМ), которая оценивает вероятность того, что автомобиль оснащен механической КПП.

Чтобы создать модель, необходимо определить формулу внутри кода R, а затем передать данные в качестве входных параметров.

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

- Первый аргумент для функции `glm` — это параметр *formula*, где дистанция (`am`) является значением, зависимым от скорости (`hp + wt`).
- Входные данные хранятся в переменной `MTCarsData`, которая заполняется SQL-запросом. Если вы не присвоите имя входным данным, по умолчанию будет использоваться имя переменной _InputDataSet_.

### <a name="store-the-model-in-the-sql-database"></a>Сохранение модели в базе данных SQL

Далее необходимо сохранить модель в базе данных SQL, где ее можно использовать для прогнозирования или повторного обучения. 

1. Создайте таблицу для хранения модели.

   Выходные данные пакета R, с помощью которого создается модель, обычно являются двоичным объектом. Это означает, что таблица, в которой хранится модель, должна содержать столбец типа **varbinary(max)** .

   ```sql
   CREATE TABLE GLM_models (
       model_name varchar(30) not null default('default model') primary key,
       model varbinary(max) not null
   );
   ```

1. Выполните приведенную ниже инструкцию Transact-SQL, чтобы вызвать хранимую процедуру, создать модель и сохранить ее в созданной таблице.

   ```sql
   INSERT INTO GLM_models(model)
   EXEC generate_GLM;
   ```

   > [!TIP]
   > Если вы выполните этот код во второй раз, появится следующая ошибка: "Нарушение ограничения первичного ключа... Невозможно вставить повторяющийся ключ в объект dbo.stopping_distance_models". Чтобы предотвратить данную ошибку, изменяйте имя для каждой новой модели. Например, вы можете изменить имя на более описательное, а также включить тип модели, день ее создания и т. д.

     ```sql
     UPDATE GLM_models
     SET model_name = 'GLM_' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
     WHERE model_name = 'default model'
     ```

## <a name="score-new-data-using-the-trained-model"></a>Оценка новых данных с использованием обученной модели

По *оценкой* в области обработки и анализа данных понимается вычисление прогнозов, вероятностей и других значений на основе данных, подаваемых в обученную модель. Для оценки прогнозов на основе новых данных вы будете использовать модель, созданную в предыдущем разделе.

### <a name="create-a-table-of-new-data"></a>Создание таблицы с новыми данными

Для начала создайте таблицу с новыми данными.

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

### <a name="predict-manual-transmission"></a>Прогнозирование вероятности оснащения автомобиля механической КПП

Чтобы получить прогнозы на основе вашей модели, необходимо написать скрипт SQL, который выполняет следующие функции:

1. Получение требуемой модели.
1. Получение новых входных данных.
1. Вызов функции прогнозирования R, совместимой с моделью.

Со временем ваша таблица может содержать несколько моделей R, созданных с помощью различных параметров и алгоритмов или обученных на основе разных подмножеств данных. В этом примере мы будем использовать модель `default model`.

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

Приведенный выше скрипт выполняет следующие действия:

- Используйте инструкцию SELECT для получения одной модели из таблицы и передайте ее в качестве входного параметра.

- После получения модели из таблицы вызовите функцию `unserialize` для модели.

- Примените функцию `predict` с соответствующими аргументами к модели, а также укажите новые входные данные.

> [!NOTE]
> В этом примере на этапе тестирования мы добавили функцию `str` для проверки схемы данных, возвращаемой из кода R. В дальнейшем вы можете удалить эту инструкцию.
>
> Имена столбцов, используемые в скрипте R, не обязательно передаются в выходные данные хранимой процедуры. В этом случае предложение WITH RESULTS используется для определения новых имен столбцов.

**Результаты**

![Результирующий набор для прогнозирования вероятности оснащения автомобиля механической КПП](./media/r-predict-am-resultset.png)

Кроме того, вы можете использовать инструкцию [PREDICT (Transact-SQL)](../../t-sql/queries/predict-transact-sql.md) для получения прогнозируемого значения или оценки на основе сохраненной модели.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о службах машинного обучения SQL Server см. в следующей статье:

- [Что такое службы машинного обучения SQL Server (Python и R)?](../what-is-sql-server-machine-learning.md)
