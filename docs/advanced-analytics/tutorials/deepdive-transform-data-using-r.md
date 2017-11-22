---
title: "Преобразование данных с помощью R | Документы Microsoft"
ms.custom: SQL2016_New_Updated
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 0327e788-94cc-4a47-933b-7c5c027b9208
caps.latest.revision: "19"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 24f37dd048f9eb7f8bb872515958006874a9b3a7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="transform-data-using-r"></a>Преобразование данных с помощью R

Пакет **RevoScaleR** содержит несколько функций для преобразования данных на разных этапах анализа.

- **rxDataStep** можно использовать для создания и преобразования подмножеств данных.

- **rxImport** поддерживает преобразование данных по мере того, как данные импортируются в XDF-файл или из него либо в кадр данных или из него.

- Функции **rxSummary**, **rxCube**, **rxLinMod**и **rxLogit** поддерживают преобразования данных, хотя и не предназначены специально для перемещения данных.

В этом разделе вы научитесь пользоваться этими функциями. Давайте начнем с rxDataStep.

## <a name="use-rxdatastep-to-transform-variables"></a>Использование функции rxDataStep для преобразования переменных

Функция rxDataStep обрабатывает один фрагмент данных одновременно, чтения из одного источника данных и записи в другую. Вы можете указать столбцы, которые нужно преобразовать, загружаемые преобразования и т. д.

Чтобы сделать этот пример интереснее, вы используете функцию из другого пакета R для преобразования данных.  Пакет **boot** является одним из "рекомендованных" пакетов, то есть **boot** входит в состав каждого дистрибутива R, но не загружается автоматически при запуске. Поэтому этот пакет уже должен быть доступен в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который вы использовали со службами [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Пакет **boot** содержит нужную вам функцию `inv.logit`, которая выполняет обратное логит-преобразование. То есть функция `inv.logit` преобразует логит обратно в значение вероятности по шкале [0,1].

> [!TIP] 
> Другой способ получить прогнозы в этой шкалы может заключаться в установке *тип* параметр **ответ** в первоначальном вызове rxPredict.

1. Сначала создайте источник данных, в котором будут храниться данные, предназначенные для таблицы *ccScoreOutput*.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Добавьте еще один источник данных, в котором будут храниться данные для таблицы ccScoreOutput2.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    Новая таблица будет содержать все переменные из предыдущей таблицы *ccScoreOutput* и вновь созданную переменную.
  
3. В качестве контекста вычисления задайте экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Чтобы проверить, используйте функцию rxSqlServerTableExists ли выходной таблицы *ccScoreOutput2* уже существует; и если да, используется функция rxSqlServerDropTable при удалении таблицы.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")
    ```
  
5. Вызов функции rxDataStep и указать нужный преобразований в списке.
  
    ```R
    rxDataStep(inData = sqlOutScoreDS,
        outFile = sqlOutScoreDS2,
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),
        transformPackages = "boot",
        overwrite = TRUE)
    ```

    При определении преобразований, применяемых к каждому столбцу, можно указать дополнительные пакеты R, необходимые для выполнения преобразований.  Дополнительные сведения о возможных типах преобразования см. в разделе  [Преобразование и создание подмножеств данных](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform).
  
6. Вызовите rxGetVarInfo, чтобы просмотреть сводку переменных в новом наборе данных.
  
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

Обратите внимание, что факторные переменные были записаны в таблицу *ccScoreOutput2* в качестве символьных данных.  Чтобы использовать их как коэффициенты в последующих операциях анализа, задайте уровни с помощью параметра *colInfo* .

## <a name="next-step"></a>Следующий шаг

[Загрузка данных в памяти с помощью rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)

## <a name="previous-step"></a>Предыдущий шаг

[Создание и выполнение сценариев R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
