---
title: Руководство по обучению и сравниванию прогнозных моделей на языке R
titleSuffix: SQL machine learning
description: В третьей части этого цикла учебников, состоящего из четырех частей, вы создадите две прогнозные модели на языке R с помощью машинного обучения SQL, а затем выберите самую точную модель.
ms.prod: sql
ms.technology: machine-learning
ms.topic: tutorial
author: cawrites
ms.author: chadam
ms.reviewer: garye, davidph
ms.date: 05/21/2020
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 2b57a54c66259fe16c3143e0328476279a1aea01
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748500"
---
# <a name="tutorial-create-a-predictive-model-in-r-with-sql-machine-learning"></a>Руководство по созданию прогнозной модели в R с помощью машинного обучения SQL
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
В третьей части этого цикла учебников, состоящего из четырех частей, вы обучите прогнозную модель на языке R. В следующей части цикла вы развернете эту модель в базе данных SQL Server с помощью Служб машинного обучения или в Кластерах больших данных.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
В третьей части этого цикла учебников, состоящего из четырех частей, вы обучите прогнозную модель на языке R. В следующей части цикла вы развернете эту модель в базе данных SQL Server с помощью Служб машинного обучения.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
В третьей части этого цикла учебников, состоящего из четырех частей, вы обучите прогнозную модель на языке R. В следующей части цикла вы развернете эту модель в базе данных с помощью служб SQL Server R Services.
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
В третьей части этого цикла учебников, состоящего из четырех частей, вы обучите прогнозную модель на языке R. В следующей части цикла вы развернете эту модель в базе данных Управляемого экземпляра SQL Azure с помощью Служб машинного обучения.
::: moniker-end

В этой статье вы узнаете, как выполнять следующие задачи.

> [!div class="checklist"]
> * Обучение двух моделей машинного обучения.
> * Создание прогнозов из обеих моделей.
> * Сравнение результатов для выбора самой точной модели.

В [первой части](r-predictive-model-introduction.md) вы узнали, как восстановить учебную базу данных.

Во [второй части](r-predictive-model-prepare-data.md) вы узнали, как загрузить данные из базы данных в кадр данных Python, а также подготовить данные в R.

В [четвертой части](r-predictive-model-deploy.md) вы узнаете, как сохранить модель в базе данных, а затем создать хранимые процедуры на основе сценариев Python, разработанных во второй и третьей частях. Хранимые процедуры будут запускаться на сервере, чтобы формировать прогнозы на основе новых данных.

## <a name="prerequisites"></a>Предварительные требования

В третьей части этого цикла учебников предполагается, что вы уже выполнили предварительные требования [**первой части**](r-predictive-model-introduction.md), а также действия, указанные во [**второй части**](r-predictive-model-prepare-data.md).

## <a name="train-two-models"></a>Обучение двух моделей

Чтобы найти лучшую модель для данных о прокате лыж, создайте две разные модели (линейная регрессия и дерево принятия решений) и посмотрите, какая из них делает более точные прогнозы. Вы используете кадр данных `rentaldata`, созданный в первой части этой серии.

```r
#First, split the dataset into two different sets:
# one for training the model and the other for validating it
train_data = rentaldata[rentaldata$Year < 2015,];
test_data  = rentaldata[rentaldata$Year == 2015,];


#Use the RentalCount column to check the quality of the prediction against actual values
actual_counts <- test_data$RentalCount;

#Model 1: Use lm to create a linear regression model, trained with the training data set
model_lm <- lm(RentalCount ~  Month + Day + WeekDay + Snow + Holiday, data = train_data);

#Model 2: Use rpart to create a decision tree model, trained with the training data set
library(rpart);
model_rpart  <- rpart(RentalCount ~ Month + Day + WeekDay + Snow + Holiday, data = train_data);
```

## <a name="make-predictions-from-both-models"></a>Создание прогнозов из обеих моделей.

Используйте функцию прогнозирования, чтобы спрогнозировать количество случаев аренды, используя каждую обученную модель.

```r
#Use both models to make predictions using the test data set.
predict_lm <- predict(model_lm, test_data)
predict_lm <- data.frame(RentalCount_Pred = predict_lm, RentalCount = test_data$RentalCount, 
                         Year = test_data$Year, Month = test_data$Month,
                         Day = test_data$Day, Weekday = test_data$WeekDay,
                         Snow = test_data$Snow, Holiday = test_data$Holiday)

predict_rpart  <- predict(model_rpart,  test_data)
predict_rpart <- data.frame(RentalCount_Pred = predict_rpart, RentalCount = test_data$RentalCount, 
                         Year = test_data$Year, Month = test_data$Month,
                         Day = test_data$Day, Weekday = test_data$WeekDay,
                         Snow = test_data$Snow, Holiday = test_data$Holiday)

#To verify it worked, look at the top rows of the two prediction data sets.
head(predict_lm);
head(predict_rpart);
```

```results
    RentalCount_Pred  RentalCount  Month  Day  WeekDay  Snow  Holiday
1         27.45858          42       2     11     4      0       0
2        387.29344         360       3     29     1      0       0
3         16.37349          20       4     22     4      0       0
4         31.07058          42       3      6     6      0       0
5        463.97263         405       2     28     7      1       0
6        102.21695          38       1     12     2      1       0
    RentalCount_Pred  RentalCount  Month  Day  WeekDay  Snow  Holiday
1          40.0000          42       2     11     4      0       0
2         332.5714         360       3     29     1      0       0
3          27.7500          20       4     22     4      0       0
4          34.2500          42       3      6     6      0       0
5         645.7059         405       2     28     7      1       0
6          40.0000          38       1     12     2      1       0
```

## <a name="compare-the-results"></a>Сравнение результатов

Теперь необходимо посмотреть, какая модель делает более точные прогнозы. Быстрый и простой способ сделать это — использовать базовую функцию построения, чтобы увидеть разницу между фактическими значениями в данных для обучения и прогнозируемыми значениями.

```r
#Use the plotting functionality in R to visualize the results from the predictions
par(mfrow = c(1, 1));
plot(predict_lm$RentalCount_Pred - predict_lm$RentalCount, main = "Difference between actual and predicted. lm")
plot(predict_rpart$RentalCount_Pred  - predict_rpart$RentalCount,  main = "Difference between actual and predicted. rpart")
```

![Сравнение двух моделей](./media/compare-models.png)

Похоже, что из двух моделей модель дерева принятия решений точнее.

## <a name="clean-up-resources"></a>Очистка ресурсов

Если вы не собираетесь продолжать работу с этим учебником, удалите базу данных TutorialDB.

## <a name="next-steps"></a>Дальнейшие действия

В третьей части этого цикла учебников вы узнали, как выполнять следующие задачи:

* Обучение двух моделей машинного обучения.
* Создание прогнозов из обеих моделей.
* Сравнение результатов для выбора самой точной модели.

Чтобы развернуть созданную модель машинного обучения, перейдите к четвертой части этого учебника:

> [!div class="nextstepaction"]
> [Развертывание прогнозной модели в R с помощью машинного обучения SQL](r-predictive-model-deploy.md)
