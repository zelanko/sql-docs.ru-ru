---
title: Учебник по Python. Обучение модели
description: В этом учебнике вы будете использовать Python и линейную регрессию в службах машинного обучения SQL Server для прогнозирования количества прокатов лыж. Вы проведете обучение модели линейной регрессии на языке Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e5f83fe37890c997865c44198cbe30bc13cdea4e
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727044"
---
# <a name="python-tutorial-train-a-linear-regression-model-in-sql-server-machine-learning-services"></a>Учебник по Python. Обучение модели линейной регрессии в службах машинного обучения SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

В третьей части серии руководств из четырех частей вы проведете обучение модели линейной регрессии в Python. В следующей части этого учебника вы развернете эту модель в базе данных SQL Server с использованием служб машинного обучения.

В этой статье вы узнаете, как выполнять следующие задачи.

> [!div class="checklist"]
> * Обучение модели линейной регрессии
> * Прогнозирование по модели линейной регрессии

В [первой части](python-ski-rental-linear-regression.md) вы узнали, как восстановить учебную базу данных.

Во [второй части](python-ski-rental-linear-regression-prepare-data.md) вы узнали, как загружать данные из SQL Server в кадр данных Python, а также подготавливать данные в Python.

В [четвертой части](python-ski-rental-linear-regression-deploy-model.md) вы узнаете, как сохранить модель в SQL Server, а затем создать хранимые процедуры на основе сценариев Python, разработанных во второй и третьей частях. Хранимые процедуры будут запускаться в SQL Server, чтобы сформировать прогнозы на основе новых данных.

## <a name="prerequisites"></a>предварительные требования

* В третьей части этого учебника предполагается, что вы уже выполнили [первую часть](python-ski-rental-linear-regression.md) и описанные в ней предварительные требования.

## <a name="train-the-model"></a>Обучение модели

Для прогнозирования необходимо найти функцию (модель), которая лучше всего описывает зависимость между переменными в нашем наборе данных. Это называется обучением модели. Набор данных для обучения будет подмножеством всего набора данных из кадра данных Pandas **df**, созданного в второй части этой серии.

Вы обучите модель **lin_model** с использованием алгоритма линейной регрессии.

```python
# Store the variable we'll be predicting on.
target = "RentalCount"

# Generate the training set.  Set random_state to be able to replicate results.
train = df.sample(frac=0.8, random_state=1)

# Select anything not in the training set and put it in the testing set.
test = df.loc[~df.index.isin(train.index)]

# Print the shapes of both sets.
print("Training set shape:", train.shape)
print("Testing set shape:", test.shape)

# Initialize the model class.
lin_model = LinearRegression()

# Fit the model to the training data.
lin_model.fit(train[columns], train[target])
```

Результат должен иметь следующий вид.

```results
Training set shape: (362, 7)
Testing set shape: (91, 7)
```

## <a name="make-predictions"></a>Составление прогнозов

Используйте функцию прогнозирования для предсказания количества аренд с помощью модели **lin_model**.

```python
# Generate our predictions for the test set.
lin_predictions = lin_model.predict(test[columns])
print("Predictions:", lin_predictions)
# Compute error between our test predictions and the actual values.
lin_mse = mean_squared_error(lin_predictions, test[target])
print("Computed error:", lin_mse)
```

```results
Predictions: [  40.   38.  240.   39.  514.   48.  297.   25.  507.   24.   30.   54.
   40.   26.   30.   34.   42.  390.  336.   37.   22.   35.   55.  350.
  252.  370.  499.   48.   37.  494.   46.   25.  312.  390.   35.   35.
  421.   39.  176.   21.   33.  452.   34.   28.   37.  260.   49.  577.
  312.   24.   24.  390.   34.   64.   26.   32.   33.  358.  348.   25.
   35.   48.   39.   44.   58.   24.  350.  651.   38.  468.   26.   42.
  310.  709.  155.   26.  648.  617.   26.  846.  729.   44.  432.   25.
   39.   28.  325.   46.   36.   50.   63.]
Computed error: 3.59831533436e-26
```

## <a name="next-steps"></a>Следующие шаги

В третьей части этого учебника вы выполнили следующие действия:

* Обучение модели линейной регрессии
* Прогнозирование по модели линейной регрессии

Чтобы развернуть созданную модель машинного обучения, перейдите к четвертой части этого учебника:

> [!div class="nextstepaction"]
> [Учебник по Python. Развертывание модели машинного обучения](python-ski-rental-linear-regression-deploy-model.md)