---
title: Краткое руководство, чтобы на основе модели с помощью R - машинного обучения SQL Server
description: В этом кратком руководстве Узнайте оценки с использованием готовых моделей данных R и SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 00fdcb0c8c9c535645268a0212e52eef6f7c88f6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961998"
---
# <a name="quickstart-predict-from-model-using-r-in-sql-server"></a>Краткое руководство. На основе модели, с помощью языка R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве используйте модель, созданную в предыдущем кратком руководстве для оценки прогнозы на основе новых данных. Для выполнения _оценки_ на основе новых данных, получить один из обученной модели из таблицы, а затем вызвать новый набор данных, на которой будет производиться прогнозирование. Оценка — это термин, иногда этот термин используется обработки и анализа данных для обозначения создания прогнозов, вероятности и другие значения, на основе новых данных, поступающих в обученной модели.

## <a name="prerequisites"></a>предварительные требования

В этом кратком руководстве является расширением [Создание модели прогнозирования](quickstart-r-create-predictive-model.md).

## <a name="create-the-table-of-new-data"></a>Создание таблицы с новыми данными

Во-первых создайте таблицу с новыми данными. 

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

## <a name="predict-manual-transmission"></a>Прогнозирование вручную передачи

Теперь ваш `dbo.GLM_models` таблицы может содержать несколько моделей R, созданных с помощью различных параметров и алгоритмов или обученных для различных подмножеств данных.

Чтобы получить прогнозы, основанные на одной конкретной модели, необходимо написать скрипт SQL, который выполняет следующие функции:

1. Получение требуемой модели.
2. Получение новых входных данных.
3. Вызов функции прогнозирования R, совместимой с моделью.

В этом примере мы будем использовать модель, с именем `default model`.

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

Приведенный выше сценарий выполняет следующие действия:

+ Используйте инструкцию SELECT для получения одной модели из таблицы и передайте ее в качестве входного параметра.

+ После получения модели из таблицы вызовите функцию `unserialize` для модели.

+ Примените функцию `predict` с соответствующими аргументами к модели, а также укажите новые входные данные.

+ В примере `str` функция будет добавлена на этапе тестирования, чтобы проверить схему данных, возвращаемого из R. Вы можете удалить эту инструкцию позднее.

+ Имена столбцов, используемые в скрипте R, не передаются в выходные данные хранимой процедуры обязательно. Здесь мы использовали предложение WITH RESULTS для определения некоторых новых имен столбцов.

**Результаты**

![Результирующий набор для прогнозирования properbility вручную передачи](./media/r-predict-am-resultset.png)

Можно также использовать [PREDICT в Transact-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) для создания прогнозируемого значения или оценка на основе хранимой модели.

## <a name="next-steps"></a>Следующие шаги

Интеграция R с SQL Server упрощает развертывание решений R в масштабе, а также позволяет использовать лучшие функции R и реляционные базы данных, повышающие производительность обработки данных и скорость анализа с использованием R. 

Продолжайте изучение решений с помощью языка R с SQL Server через end-to-end сценарии, созданные группами разработки обработки и анализа данных Майкрософт и R Services.

> [!div class="nextstepaction"]
> [Учебники по SQL Server R](sql-server-r-tutorials.md)
