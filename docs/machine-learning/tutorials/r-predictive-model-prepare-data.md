---
title: Руководство по подготовке данных для обучения прогнозной модели на языке R
titleSuffix: SQL machine learning
description: В второй части этого цикла учебников, состоящего из четырех частей, вы подготовите данные для обучения прогнозной модели в R с помощью машинного обучения SQL.
ms.prod: sql
ms.technology: machine-learning
ms.topic: tutorial
author: cawrites
ms.author: chadam
ms.reviewer: garye, davidph
ms.date: 05/04/2020
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1ae2931ca07cdcd6e3f1216ce7adb2551a6e23ae
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83607037"
---
# <a name="tutorial-prepare-data-to-train-a-predictive-model-in-r-with-sql-machine-learning"></a>Руководство по подготовке данных для обучения прогнозной модели в R с помощью машинного обучения SQL

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Во второй части этого цикла учебников, состоящего из четырех частей, вы подготовите данные из базы данных с помощью R. Далее в этом цикле подготовленные данные будут использоваться для обучения и развертывания прогнозной модели машинного обучения в R с помощью Служб машинного обучения SQL Server или в Кластерах больших данных.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Во второй части этого цикла учебников, состоящего из четырех частей, вы подготовите данные из базы данных с помощью R. Далее в этом цикле подготовленные данные будут использоваться для обучения и развертывания прогнозной модели машинного обучения в R с помощью Служб машинного обучения SQL Server.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Во второй части этого цикла учебников, состоящего из четырех частей, вы подготовите данные из базы данных с помощью R. Далее в этом цикле подготовленные данные будут использоваться для обучения и развертывания прогнозной модели машинного обучения в R с помощью служб SQL Server R Services.
::: moniker-end

В этой статье вы узнаете, как выполнять следующие задачи.

> [!div class="checklist"]
> * Восстановление примера базы данных в базу данных.
> * Загрузка данных из базы данных SQL в кадр данных R.
> * Подготовка данных на языке R путем определения некоторых столбцов как категориальных.

В [первой части](r-predictive-model-introduction.md) вы узнали, как восстановить учебную базу данных.

В [третьей части](r-predictive-model-train.md) вы узнаете, как обучить модель машинного обучения в R.

В [четвертой части](r-predictive-model-deploy.md) вы узнаете, как сохранить модель в базе данных, а затем создать хранимые процедуры на основе сценариев R, разработанных во второй и третьей частях. Хранимые процедуры будут запускаться на сервере, чтобы формировать прогнозы на основе новых данных.

## <a name="prerequisites"></a>Предварительные требования

Во второй части этого учебника предполагается, что вы ознакомились с [**первой частью**](r-predictive-model-introduction.md) и ее компонентами.

## <a name="load-the-data-into-a-data-frame"></a>Загрузка данных в кадр данных

Чтобы использовать данные в R, загрузите их из базы данных SQL в кадр данных (`rentaldata`).

Создайте файл RScript в RStudio и выполните следующий сценарий. Замените **ServerName** собственными данными для подключения.

```r
#Define the connection string to connect to the TutorialDB database
connStr <- "Driver=SQL Server;Server=ServerName;Database=TutorialDB;Trusted_Connection=TRUE"

#Get the data from the table
library(RODBC)

ch <- odbcDriverConnect(connStr)

#Take a look at the structure of the data and the top rows
head(rentaldata)
str(rentaldata)

#Import the data from the table
rentaldata <- sqlFetch(ch, "dbo.rental_data")

#Take a look at the structure of the data and the top rows
head(rentaldata)
str(rentaldata)
```

Результат должен иметь следующий вид.

```results
   Year  Month  Day  RentalCount  WeekDay  Holiday  Snow
1  2014    1     20      445         2        1      0
2  2014    2     13       40         5        0      0
3  2013    3     10      456         1        0      0
4  2014    3     31       38         2        0      0
5  2014    4     24       23         5        0      0
6  2015    2     11       42         4        0      0
'data.frame':       453 obs. of  7 variables:
$ Year       : int  2014 2014 2013 2014 2014 2015 2013 2014 2013 2015 ...
$ Month      : num  1 2 3 3 4 2 4 3 4 3 ...
$ Day        : num  20 13 10 31 24 11 28 8 5 29 ...
$ RentalCount: num  445 40 456 38 23 42 310 240 22 360 ...
$ WeekDay    : num  2 5 1 2 5 4 1 7 6 1 ...
$ Holiday    : int  1 0 0 0 0 0 0 0 0 0 ...
$ Snow       : num  0 0 0 0 0 0 0 0 0 0 ...
```

## <a name="prepare-the-data"></a>Подготовка данных

В этом образце базы данных большая часть подготовки уже выполнена, но можно сделать еще кое-что.
Используйте следующий сценарий R для определения трех столбцов как *категорий*, изменив типы данных на *factor*.



```r
#Changing the three factor columns to factor types
rentaldata$Holiday <- factor(rentaldata$Holiday);
rentaldata$Snow    <- factor(rentaldata$Snow);
rentaldata$WeekDay <- factor(rentaldata$WeekDay);



#Visualize the dataset after the change
str(rentaldata);
```

Результат должен иметь следующий вид.

```results
data.frame':      453 obs. of  7 variables:
$ Year       : int  2014 2014 2013 2014 2014 2015 2013 2014 2013 2015 ...
$ Month      : num  1 2 3 3 4 2 4 3 4 3 ...
$ Day        : num  20 13 10 31 24 11 28 8 5 29 ...
$ RentalCount: num  445 40 456 38 23 42 310 240 22 360 ...
$ WeekDay    : Factor w/ 7 levels "1","2","3","4",..: 2 5 1 2 5 4 1 7 6 1 ...
$ Holiday    : Factor w/ 2 levels "0","1": 2 1 1 1 1 1 1 1 1 1 ...
$ Snow       : Factor w/ 2 levels "0","1": 1 1 1 1 1 1 1 1 1 1 ...
```

Теперь данные готовы для обучения.

## <a name="clean-up-resources"></a>Очистка ресурсов

Если вы не собираетесь продолжать работу с этим учебником, удалите базу данных TutorialDB.

## <a name="next-steps"></a>Дальнейшие действия

Во второй части этого цикла учебников вы узнали, как выполнять следующие задачи:

* Загрузка примера данных из SQL Server в кадр данных R.
* Подготовка данных на языке R путем определения некоторых столбцов как категориальных.

Чтобы создать модель машинного обучения, которая использует данные из базы данных TutorialDB, перейдите к третьей части этого цикла учебников:

> [!div class="nextstepaction"]
> [Создание прогнозной модели в R с помощью машинного обучения SQL](r-predictive-model-train.md)
