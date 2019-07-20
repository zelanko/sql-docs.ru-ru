---
title: Краткое руководство по прогнозированию модели с помощью языка R
description: В этом кратком руководстве вы узнаете об оценке с помощью предварительно созданной модели в R и SQL Server данных.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: e81731683fb71b074ed754ab6ab4eaab40d08c20
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345405"
---
# <a name="quickstart-predict-from-model-using-r-in-sql-server"></a>Краткое руководство. Прогнозирование модели с помощью R в SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом кратком руководстве для оценки прогнозов по актуальным данным используется модель, созданная в предыдущем кратком руководстве. Чтобы выполнить _оценку_ с помощью новых данных, получите одну из обученных моделей из таблицы, а затем вызовите новый набор данных, на основе которого должны основываться прогнозы. Оценка — это термин, который иногда используется в обработке данных, что означает создание прогнозов, вероятностей или других значений на основе новых данных, поступающих в обученную модель.

## <a name="prerequisites"></a>предварительные требования

Это расширение [создает прогнозную модель](quickstart-r-create-predictive-model.md).

## <a name="create-the-table-of-new-data"></a>Создание таблицы новых данных

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

## <a name="predict-manual-transmission"></a>Прогнозирование ручной передачи

Теперь `dbo.GLM_models` таблица может содержать несколько моделей R, построенных с использованием различных параметров или алгоритмов, или обученных по разным подмножествам данных.

Чтобы получить прогнозы на основе одной конкретной модели, необходимо написать скрипт SQL, который выполняет следующие действия:

1. Получение требуемой модели.
2. Получение новых входных данных.
3. Вызов функции прогнозирования R, совместимой с моделью.

В этом примере мы будем использовать модель с именем `default model`.

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

+ Используйте инструкцию SELECT для получения одной модели из таблицы и передайте ее в качестве входного параметра.

+ После получения модели из таблицы вызовите функцию `unserialize` для модели.

+ Примените функцию `predict` с соответствующими аргументами к модели, а также укажите новые входные данные.

+ В этом примере `str` функция добавляется на этапе тестирования, чтобы проверить схему данных, возвращаемых из R. Эту инструкцию можно удалить позже.

+ Имена столбцов, используемые в скрипте R, не обязательно передаются в выходные данные хранимой процедуры. Здесь мы использовали предложение WITH RESULTs для определения новых имен столбцов.

**Результаты**

![Результирующий набор для прогнозирования пропербилити передачи вручную](./media/r-predict-am-resultset.png)

Можно также использовать [Predict в Transact-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) для создания прогнозируемого значения или оценки на основе хранимой модели.

## <a name="next-steps"></a>Следующие шаги

Интеграция R с SQL Server упрощает развертывание решений R в масштабе, а также позволяет использовать лучшие функции R и реляционные базы данных, повышающие производительность обработки данных и скорость анализа с использованием R. 

Ознакомьтесь с решениями, использующими R с SQL Server, с помощью комплексных сценариев, созданных командами разработчиков Майкрософт для обработки и анализа данных и служб R.

> [!div class="nextstepaction"]
> [Учебники по SQL Server R](sql-server-r-tutorials.md)
