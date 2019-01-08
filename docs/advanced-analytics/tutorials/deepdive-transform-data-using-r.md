---
title: Преобразование данных с помощью rxDataStep RevoScaleR - машинного обучения SQL Server
description: Руководство по преобразованию данных с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e124825e29392111a453cae0c41b49e8984c9906
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645393"
---
# <a name="transform-data-using-r-sql-server-and-revoscaler-tutorial"></a>Преобразование данных с помощью R (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

В этом занятии описывается **RevoScaleR** функции для преобразования данных на разных этапах анализа.

> [!div class="checklist"]
> * Используйте **rxDataStep** для создания и преобразования подмножеств данных
> * Используйте **rxImport** для преобразования данных, передаваемых в из xdf-файл или кадр данных в памяти во время импорта

Функции **rxSummary**, **rxCube**, **rxLinMod**и **rxLogit** поддерживают преобразования данных, хотя и не предназначены специально для перемещения данных.

## <a name="use-rxdatastep-to-transform-variables"></a>Использование функции rxDataStep для преобразования переменных

Функция [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) обрабатывает данные по одному блоку за раз, считывая их из одного источника данных и записывая в другой. Вы можете указать столбцы, которые нужно преобразовать, загружаемые преобразования и т. д.

Чтобы сделать этот пример интереснее, давайте использовать функцию из другого пакета R для преобразования данных. Пакет **boot** является одним из "рекомендованных" пакетов, то есть **boot** входит в состав каждого дистрибутива R, но не загружается автоматически при запуске. Таким образом, пакет уже должен быть доступен на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра, настроенного для интеграция R.

Из **загрузки** пакет, используйте функцию **inv.logit**, которая выполняет обратное логит-преобразование. То есть функция **inv.logit** преобразует логит обратно в значение вероятности по шкале [0,1].

> [!TIP] 
> Кроме того, чтобы получать прогнозы по этой шкале, можно задать для параметра *type* значение **response** в исходном вызове функции **rxPredict**.

1. Начните с создания источника данных для хранения данных, предназначенные для таблицы, `ccScoreOutput`.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Добавить другой источник данных для хранения данных для таблицы `ccScoreOutput2`.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    В новой таблице, хранить все переменные из предыдущей `ccScoreOutput` таблицы, а также вновь созданная переменная.
  
3. В качестве контекста вычисления задайте экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Используйте функцию **rxSqlServerTableExists** проверяемый ли выходной таблицы `ccScoreOutput2` уже существует; и если да, используйте функцию **rxSqlServerDropTable** при удалении таблицы.
  
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

    При определении преобразований, применяемых к каждому столбцу, можно указать дополнительные пакеты R, необходимые для выполнения преобразований.  Дополнительные сведения о типах преобразования, которые можно выполнить, см. в разделе [преобразования и подмножество данных, с помощью RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform).
  
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

Обратите внимание, что факторные переменные были записаны в таблицу `ccScoreOutput2` как символьные данные. Чтобы использовать их как коэффициенты в последующих операциях анализа, задайте уровни с помощью параметра *colInfo* .

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Загрузка данных в память с помощью функции rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)