---
title: Преобразование данных с помощью RevoScaleR rxDataStep
description: Пошаговое руководство по преобразованию данных с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: c7d88137994cf5d920462cc4942eb5b632ae3d6e
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344678"
---
# <a name="transform-data-using-r-sql-server-and-revoscaler-tutorial"></a>Преобразование данных с помощью R (учебник по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [учебника RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

На этом занятии вы узнаете о функциях **RevoScaleR** для преобразования данных на различных стадиях анализа.

> [!div class="checklist"]
> * Использование **rxDataStep** для создания и преобразования подмножества данных
> * Использование **rxImport** для преобразования транзитных данных в файл Xdf-или в кадр данных в памяти во время импорта

Функции **rxSummary**, **rxCube**, **rxLinMod**и **rxLogit** поддерживают преобразования данных, хотя и не предназначены специально для перемещения данных.

## <a name="use-rxdatastep-to-transform-variables"></a>Использование rxDataStep для преобразования переменных

Функция [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) обрабатывает данные по одному блоку за раз, считывая их из одного источника данных и записывая в другой. Вы можете указать столбцы, которые нужно преобразовать, загружаемые преобразования и т. д.

Чтобы сделать этот пример интересным, мы используем функцию из другого пакета R для преобразования данных. Пакет **boot** является одним из "рекомендованных" пакетов, то есть **boot** входит в состав каждого дистрибутива R, но не загружается автоматически при запуске. Поэтому пакет уже должен быть доступен в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляре, настроенном для интеграции R.

Из пакета **загрузки** используйте функцию **Inv. логит-преобразование**, которая вычислит обратный логит-преобразование. То есть функция **inv.logit** преобразует логит обратно в значение вероятности по шкале [0,1].

> [!TIP] 
> Кроме того, чтобы получать прогнозы по этой шкале, можно задать для параметра *type* значение **response** в исходном вызове функции **rxPredict**.

1. Начните с создания источника данных для хранения данных, предназначенных для таблицы, `ccScoreOutput`.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Добавьте еще один источник данных для хранения данных таблицы `ccScoreOutput2`.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    В новой таблице сохраните все переменные из предыдущей `ccScoreOutput` таблицы и вновь созданную переменную.
  
3. В качестве контекста вычисления задайте экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Используйте функцию **rxSqlServerTableExists** , чтобы проверить, существует ли уже `ccScoreOutput2` выходная таблица, и если да, используйте функцию **rxSqlServerDropTable** для удаления таблицы.
  
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

    При определении преобразований, применяемых к каждому столбцу, можно указать дополнительные пакеты R, необходимые для выполнения преобразований.  Дополнительные сведения о типах преобразований, которые можно выполнить, см. [в разделе Преобразование и подмножество данных с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform).
  
6. Вызовите функцию **rxGetVarInfo** для просмотра сводки переменных в новом наборе данных.
  
```R
rxGetVarInfo(sqlOutScoreDS2)
```

**Результаты**

```R
Var 1: ccFraudLogitScore, Type: numeric
Var 2: state, Type: character
Var 3: gender, Type: character
Var 4: cardholder, Type: character
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: ccFraudProb, Type: numeric
```

Исходные оценки логита сохраняются, однако был добавлен новый столбец *ccFraudProb*, в котором оценки логита представлены значениями от 0 до 1.

Обратите внимание, что переменные фактора записываются `ccScoreOutput2` в таблицу в виде символьных данных. Чтобы использовать их как коэффициенты в последующих операциях анализа, задайте уровни с помощью параметра *colInfo* .

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Загрузка данных в память с помощью функции rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)