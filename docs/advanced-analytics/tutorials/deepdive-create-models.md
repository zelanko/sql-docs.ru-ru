---
title: Руководство по созданию моделей R RevoScaleR
description: Пошаговое руководство по созданию модели с использованием языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 65d5d999df39909a5419883736686c5bc22e0062
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469807"
---
# <a name="create-r-models-sql-server-and-revoscaler-tutorial"></a>Создание моделей R (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Теперь, когда обучающие данные были расширены, пришло время анализировать данные с помощью регрессионного моделирования. Линейные модели являются важным инструментом в сфере прогнозной аналитики, а пакет **RevoScaleR** включает алгоритмы регрессии, которые могут разделить рабочую нагрузку и параллельно запускать ее.

> [!div class="checklist"]
> * создание модели линейной регрессии;
> * создание модели логистической регрессии;

## <a name="create-a-linear-regression-model"></a>создание модели линейной регрессии;

На этом шаге создается простая линейная модель, которая оценивает баланс кредитной карты для клиентов, использующих в качестве независимых переменных значения в столбцах *Gender* и *creditLine* .
  
Для этого используйте функцию [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) , которая поддерживает удаленные контексты вычислений.
  
1. Создайте переменную R для хранения завершенной модели и вызовите **rxLinMod**, передав соответствующую формулу.
  
    ```R
    linModObj <- rxLinMod(balance ~ gender + creditLine,  data = sqlFraudDS)
    ```
  
2. Чтобы просмотреть сводку результатов, вызовите стандартную функцию " **Сводка** R" для объекта модели.
  
     ```R
     summary(linModObj)
     ```

Вам может показаться странным, что обыкновенная функция R, такая как **summary** , будет здесь работать, поскольку на предыдущем шаге контекст вычислений был переключен на серверный. Однако даже если функция **rxLinMod** использует контекст удаленных вычислений для создания модели, она также возвращает объект, который содержит модель для локальной рабочей станции, и сохраняет его в общем каталоге.

Таким образом, для модели можно выполнять стандартные команды R, как если бы она была создана с помощью контекста local.

**Результаты**

```R
Linear Regression Results for: balance ~ gender + creditLineData: sqlFraudDS (RxSqlServerData Data Source)
Dependent variable(s): balance
Total independent variables: 4 (Including number dropped: 1)
Number of valid observations: 10000
Number of missing observations: 0
Coefficients: (1 not defined because of singularities)

Estimate Std. Error t value Pr(>|t|) (Intercept)
3253.575 71.194 45.700 2.22e-16
gender=Male -88.813 78.360 -1.133 0.257
gender=Female Dropped Dropped Dropped Dropped
creditLine 95.379 3.862 24.694 2.22e-16
Signif. codes: 0  0.001  0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 3812 on 9997 degrees of freedom
Multiple R-squared: 0.05765
Adjusted R-squared: 0.05746
F-statistic: 305.8 on 2 and 9997 DF, p-value: < 2.2e-16
Condition number: 1.0184
```

## <a name="create-a-logistic-regression-model"></a>создание модели логистической регрессии;

Затем создайте модель логистической регрессии, которая показывает, является ли конкретный клиент риском мошенничества. Вы будете использовать функцию **RevoScaleR** [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) , которая поддерживает размещение моделей логистической регрессии в удаленных контекстах вычислений.

Не меняйте контекст вычисления. Кроме того, вы также будете использовать тот же источник данных.

1. Вызовите функцию **rxLogit** и передайте формулу, необходимую для определения модели.

    ```R
    logitObj <- rxLogit(fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS, dropFirst = TRUE)
    ```
  
    Так как это большая модель, содержащая 60 независимых переменных, в том числе три фиктивные переменные, которые удаляются, возможно, придется подождать некоторое время, пока контекст вычислений вернет объект.
    
    Причина такого большого размера модели в том, что в языке R (и в пакете **RevoScaleR** ) каждый уровень категориальной факторной переменной автоматически обрабатывается как отдельная фиктивная переменная.
  
2. Чтобы просмотреть сводку по полученной модели, вызовите функцию R **summary** .
  
    ```R
    summary(logitObj)
    ```
  
**Частичные результаты**

```R
Logistic Regression Results for: fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine
Data: sqlFraudDS (RxSqlServerData Data Source)
Dependent variable(s): fraudRisk
Total independent variables: 60 (Including number dropped: 3)
Number of valid observations: 10000 -2

LogLikelihood: 2032.8699 (Residual deviance on 9943 degrees of freedom)

Coefficients:
Estimate Std. Error z value Pr(>|z|)     (Intercept)
-8.627e+00  1.319e+00  -6.538 6.22e-11
state=AK                Dropped    Dropped Dropped  Dropped
state=AL             -1.043e+00  1.383e+00  -0.754   0.4511

(other states omitted)

gender=Male             Dropped    Dropped Dropped  Dropped
gender=Female         7.226e-01  1.217e-01   5.936 2.92e-09
cardholder=Principal    Dropped    Dropped Dropped  Dropped
cardholder=Secondary  5.635e-01  3.403e-01   1.656   0.0977
balance               3.962e-04  1.564e-05  25.335 2.22e-16
numTrans              4.950e-02  2.202e-03  22.477 2.22e-16
numIntlTrans          3.414e-02  5.318e-03   6.420 1.36e-10
creditLine            1.042e-01  4.705e-03  22.153 2.22e-16

Signif. codes:  0 '\*\*\*' 0.001 '\*\*' 0.01 '\*' 0.05 '.' 0.1 ' ' 1
Condition number of final variance-covariance matrix: 3997.308
Number of iterations: 15
```

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Оценка новых данных](../../advanced-analytics/tutorials/deepdive-score-new-data.md)