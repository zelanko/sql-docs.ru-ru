---
title: Преобразование данных с помощью RevoScaleR
description: Сведения о функциях RevoScaleR для преобразования данных на разных этапах анализа и преобразовании данных с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 8c954d708a6dba6a0caad4122149cfcecdb5a182
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470515"
---
# <a name="transform-data-using-r-sql-server-and-revoscaler-tutorial"></a>Преобразование данных с помощью языка R (учебник по SQL Server и RevoScaleR)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Эта часть 9 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В этом учебнике вы получите сведения о функциях **RevoScaleR** для преобразования данных на разных этапах анализа.

> [!div class="checklist"]
> * Использование **rxDataStep** для создания и преобразования подмножества данных
> * Использование **rxImport** для преобразования транзитных данных в XDF-файле или в кадре данных в памяти во время импорта

Функции **rxSummary**, **rxCube**, **rxLinMod** и **rxLogit** поддерживают преобразования данных, хотя и не предназначены специально для перемещения данных.

## <a name="use-rxdatastep-to-transform-variables"></a>Использование функции rxDataStep для преобразования переменных

Функция [rxDataStep](/machine-learning-server/r-reference/revoscaler/rxdatastep) обрабатывает данные по одному блоку за раз, считывая их из одного источника данных и записывая в другой. Вы можете указать столбцы, которые нужно преобразовать, загружаемые преобразования и т. д.

Чтобы сделать этот пример интереснее, используем функцию из другого пакета R для преобразования данных. Пакет **boot** является одним из "рекомендованных" пакетов, то есть **boot** входит в состав каждого дистрибутива R, но не загружается автоматически при запуске. Поэтому этот пакет уже должен быть доступен в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], где настроена интеграция с R.

Пакет **boot** содержит нужную вам функцию **inv.logit**, которая выполняет обратное логит-преобразование. То есть функция **inv.logit** преобразует логит обратно в значение вероятности по шкале [0,1].

> [!TIP] 
> Кроме того, чтобы получать прогнозы по этой шкале, можно задать для параметра *type* значение **response** в исходном вызове функции **rxPredict**.

1. Сначала создайте источник данных, в котором будут храниться данные, предназначенные для таблицы `ccScoreOutput`.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Добавьте еще один источник данных, в котором будут храниться данные для таблицы `ccScoreOutput2`.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    В новой таблице сохраните все переменные из предыдущей таблицы `ccScoreOutput`, а также новые переменные.
  
3. В качестве контекста вычисления задайте экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Используйте функцию **rxSqlServerTableExists**, чтобы проверить наличие таблицы выходных данных `ccScoreOutput2`. Если таблица существует, удалите ее с помощью функции **rxSqlServerDropTable**.
  
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

    При определении преобразований, применяемых к каждому столбцу, можно указать дополнительные пакеты R, необходимые для выполнения преобразований.  Дополнительные сведения о возможных типах преобразования см. в разделе [Преобразование и выделение подмножеств данных с помощью RevoScaleR](/machine-learning-server/r/how-to-revoscaler-data-transform).
  
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

Обратите внимание на то, что факторные переменные были записаны в таблицу `ccScoreOutput2` как символьные данные. Чтобы использовать их как коэффициенты в последующих операциях анализа, задайте уровни с помощью параметра *colInfo* .

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Загрузка данных в память с помощью функции rxImport](../../machine-learning/tutorials/deepdive-load-data-into-memory-using-rximport.md)