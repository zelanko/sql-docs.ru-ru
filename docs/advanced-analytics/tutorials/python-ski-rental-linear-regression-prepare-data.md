---
title: 'Учебник по Python: Подготовка данных (линейная регрессия)'
description: В этом учебнике вы будете использовать Python и линейную регрессию в SQL Server Службы машинного обучения для прогнозирования количества Ski напрокат. Вы будете подготавливать данные из базы данных SQL Server с помощью Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c6c4d5fb4ffc5049f7e1325267b7623dc195e9d8
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70242502"
---
# <a name="python-tutorial-prepare-data-to-train-a-linear-regression-model-in-sql-server-machine-learning-services"></a>Учебник по Python: Подготовка данных для обучения модели линейной регрессии в SQL Server Службы машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В второй части серии руководств из четырех частей вы будете подготавливать данные из SQL Server базы данных с помощью Python. Далее в этой серии вы будете использовать эти данные для обучения и развертывания модели линейной регрессии в Python с SQL Server Службы машинного обучения.

Из этой статьи вы узнаете о следующем:

> [!div class="checklist"]
> * Загрузка данных из базы данных SQL Server в кадр данных **Pandas**
> * Подготовка данных в Python путем удаления некоторых столбцов

В [первой части](python-ski-rental-linear-regression.md)вы узнали, как восстановить образец базы данных.

В [третьей части](python-ski-rental-linear-regression-train-model.md)вы узнаете, как обучить модель машинного обучения линейной регрессии в Python.

В [части 4](python-ski-rental-linear-regression-deploy-model.md)вы узнаете, как сохранить модель для SQL Server, а затем создать хранимые процедуры из скриптов Python, разработанных в двух и трех частях. Хранимые процедуры будут выполняться в SQL Server, чтобы сделать прогнозы на основе новых данных.

## <a name="prerequisites"></a>Предварительные требования

* В части 2 этого учебника предполагается, что вы завершили [часть первой](python-ski-rental-linear-regression.md) и ее предварительных требований.

## <a name="explore-and-prepare-the-data"></a>Просмотр и подготовка данных

Чтобы использовать данные в Python, необходимо загрузить данные из SQL Server базы данных в кадр данных Pandas.

Создайте новую записную книжку Python в Azure Data Studio и выполните следующий скрипт. Замените `<SQL Server>` на собственное имя SQL Server.

Приведенный ниже сценарий Python импортирует набор данных из таблицы **dbo. rental_data** в базе данных в значение **DF**кадра данных Pandas.

```python
import pandas as pd
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_import

# Connection string to your SQL Server instance
conn_str = 'Driver=SQL Server;Server=<SQL Server>;Database=TutorialDB;Trusted_Connection=True;'

# Define the columns you will import
 column_info = {
         "Year" : { "type" : "integer" },
         "Month" : { "type" : "integer" },
         "Day" : { "type" : "integer" },
         "RentalCount" : { "type" : "integer" },
         "WeekDay" : {
             "type" : "factor",
             "levels" : ["1", "2", "3", "4", "5", "6", "7"]
         },
         "Holiday" : {
             "type" : "factor",
             "levels" : ["1", "0"]
         },
         "Snow" : {
             "type" : "factor",
             "levels" : ["1", "0"]
         }
     }

# Get the data from the SQL Server table
data_source = RxSqlServerData(table="dbo.rental_data",
                               connection_string=conn_str, column_info=column_info)
computeContext = RxInSqlServer(
     connection_string = conn_str,
     num_tasks = 1,
     auto_cleanup = False
)

RxInSqlServer(connection_string=conn_str, num_tasks=1, auto_cleanup=False)

# import data source and convert to pandas dataframe
df = pd.DataFrame(rx_import(input_data = data_source))
print("Data frame:", df)

# Get all the columns from the dataframe.
columns = df.columns.tolist()

# Filter the columns to remove ones we don't want to use in the training
columns = [c for c in columns if c not in ["Year"]]
```

Должны отобразиться результаты, аналогичные приведенным ниже.

```results
Rows Processed: 453
Data frame:      Day  Holiday  Month  RentalCount  Snow  WeekDay  Year
0     20        1      1          445     2        2  2014
1     13        2      2           40     2        5  2014
2     10        2      3          456     2        1  2013
3     31        2      3           38     2        2  2014
4     24        2      4           23     2        5  2014
5     11        2      2           42     2        4  2015
6     28        2      4          310     2        1  2013
...
[453 rows x 7 columns]
```

## <a name="next-steps"></a>Следующие шаги

В второй части этой серии руководств вы выполнили следующие действия:

* Загрузка данных из базы данных SQL Server в кадр данных **Pandas**
* Подготовка данных в Python путем удаления некоторых столбцов

Чтобы обучить модель машинного обучения, которая использует данные из базы данных TutorialDB, следуйте третьей части этой серии руководств:

> [!div class="nextstepaction"]
> [Учебник по Python: Обучение модели линейной регрессии](python-ski-rental-linear-regression-train-model.md)