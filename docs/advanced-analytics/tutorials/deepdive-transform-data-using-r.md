---
title: Преобразование данных с помощью R (SQL и R глубокое погружение) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 80472b3328c392d886733aad97adf1aa6eeae4ba
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31204627"
---
# <a name="transform-data-using-r-sql-and-r-deep-dive"></a>Преобразование данных с помощью R (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Пакет **RevoScaleR** содержит несколько функций для преобразования данных на разных этапах анализа.

- **rxDataStep** можно использовать для создания и преобразования подмножеств данных.

- **rxImport** поддерживает преобразование данных по мере того, как данные импортируются в XDF-файл или из него либо в кадр данных или из него.

- Функции **rxSummary**, **rxCube**, **rxLinMod**и **rxLogit** поддерживают преобразования данных, хотя и не предназначены специально для перемещения данных.

В этом разделе вы узнаете, как использовать эти функции. Давайте начнем с [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep).

## <a name="use-rxdatastep-to-transform-variables"></a>Использование rxDataStep для преобразования переменных

Функция **rxDataStep** обрабатывает данные по одному блоку за раз, считывая их из одного источника данных и записывая в другой. Вы можете указать столбцы, которые нужно преобразовать, загружаемые преобразования и т. д.

Чтобы сделать этот пример более информативным, позволяет использовать функцию из другого пакета R для преобразования данных.  Пакет **boot** является одним из "рекомендованных" пакетов, то есть **boot** входит в состав каждого дистрибутива R, но не загружается автоматически при запуске. Поэтому этот пакет уже должен быть доступен в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который вы использовали со службами [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Из **загрузки** пакет, используйте функцию `inv.logit`, которая вычисляет обратное logit. То есть функция `inv.logit` преобразует логит обратно в значение вероятности по шкале [0,1].

> [!TIP] 
> Другой способ получить прогнозы в этой шкалы может заключаться в установке *тип* параметр **ответ** в первоначальном вызове rxPredict.

1. Начните с создания источника данных для хранения данных, предназначенные для таблицы, `ccScoreOutput`.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Добавление другого источника данных для хранения данных для таблицы `ccScoreOutput2`.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    В новой таблице хранить все переменные из предыдущего `ccScoreOutput` таблицы, а также вновь созданная переменная.
  
3. В качестве контекста вычисления задайте экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Используйте функцию **rxSqlServerTableExists** для проверки ли выходной таблицы `ccScoreOutput2` уже существует; и если да, используйте функцию **rxSqlServerDropTable** при удалении таблицы.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")
    ```
  
5. Вызовите функцию **rxDataStep** и укажите требуемые преобразования в списке.
  
    ```R
    rxDataStep(inData = sqlOutScoreDS,
        outFile = sqlOutScoreDS2,
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),
        transformPackages = "boot",
        overwrite = TRUE)
    ```

    При определении преобразований, применяемых к каждому столбцу, можно указать дополнительные пакеты R, необходимые для выполнения преобразований.  Дополнительные сведения о типах преобразования, которые можно выполнять в разделе [преобразования и подмножество данных, с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform).
  
6. Вызовите функцию **rxGetVarInfo** для просмотра сводки переменных в новом наборе данных.
  
    ```R
    rxGetVarInfo(sqlOutScoreDS2)
    ```

    **Результаты**
    
    *Var 1: ccFraudLogitScore, Тип: numeric*
    
    *Var 2: state, Тип: character*
    
    *Var 3: gender, Тип: character*
    
    *Var 4: cardholder, Тип: character*
    
    *Var 5: balance, Тип: integer*
    
    *Var 6: numTrans, Тип: integer*
    
    *Var 7: numIntlTrans, Тип: integer*
    
    *Var 8: creditLine, Тип: integer*
    
    *Var 9: ccFraudProb, Тип: numeric*

Исходные оценки логита сохраняются, однако был добавлен новый столбец *ccFraudProb*, в котором оценки логита представлены значениями от 0 до 1.

Обратите внимание, что переменные коэффициент были записаны в таблицу `ccScoreOutput2` как символьные данные. Чтобы использовать их как коэффициенты в последующих операциях анализа, задайте уровни с помощью параметра *colInfo* .

## <a name="next-step"></a>Следующий шаг

[Загрузка данных в память с помощью функции rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание и выполнение скриптов R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
