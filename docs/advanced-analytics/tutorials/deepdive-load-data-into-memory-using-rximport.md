---
title: Загрузка данных в памяти с помощью rxImport (SQL и R глубокое погружение) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ea5a977f1504a245e270a93a876ac617d8aa6852
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201706"
---
# <a name="load-data-into-memory-using-rximport-sql-and-r-deep-dive"></a>Данные загружаются в память с использованием rxImport (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

[RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) функцию можно использовать для перемещения данных из источника данных, в кадр данных в памяти для сеанса, или в XDF-файл на диске. Если не указать файл в качестве назначения, данные помещаются в память как кадр данных.

На этом шаге вы узнаете, как получить данные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а затем используйте **rxImport** функция перевод интересующих их данных в локальный файл. Таким образом, их можно будет повторно анализировать в локальном контексте вычисления, не выполняя запрос к базе данных еще раз.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Извлечение подмножества данных из SQL Server в локальной памяти

Вы решили, что вы хотите проанализировать только пользователи высокого риска, более подробно. Исходная таблица при [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет большой размер, поэтому необходимо получить сведения о только что клиентов с высоким риском. Затем загрузите эти данные в кадр данных в памяти локальной рабочей станции.

1. Задайте в качестве контекста вычисления локальную рабочую станцию.

    ```R
    rxSetComputeContext("local")
    ```

2. Создайте объект источника данных SQL Server, указав допустимую инструкцию SQL в параметре *sqlQuery* . В этом примере возвращается подмножество наблюдений с наивысшими показателями рисков. Таким образом, в локальную память будут помещены только действительно нужные данные.

    ```R
    sqlServerProbDS \<- RxSqlServerData(
        sqlQuery = paste("SELECT * FROM ccScoreOutput2",
        "WHERE (ccFraudProb > .99)"),
        connectionString = sqlConnString)
    ```

3. Вызовите функцию [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) для чтения данных в кадр данных в локальном сеансе R.

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    Если операция выполнена успешно, появится сообщение о состоянии похожее на следующее: «прочитано строк: 35, Всего обработано строк: 35, общее время блока: 0.036 секунд»

4. Теперь, когда с высоким риском наблюдения в кадре данных в памяти, можно использовать различные функции R для обработки кадров данных. Например можно упорядочить пользователей по их оценки риска и распечатать список клиентов, которые представляют высокий риск.

    ```R
    orderedHighRisk <- highRisk[order(-highRisk$ccFraudProb),]
    row.names(orderedHighRisk) <- NULL
    head(orderedHighRisk)
    ```

**Результаты**

*ccFraudLogitScore   state gender cardholder balance numTrans numIntlTrans creditLine ccFraudProb1*

*9,786345    SD   Male  Principal   23456       25            5 75   0,99994382*

*9,433040    FL Female  Principal   20629       24           28 75   0,99992003*

*8,556785    NY Female  Principal   19064       82           53 43   0,99980784*

*8,188668    AZ Female  Principal   19948       29            0 75   0,99972235*

*7,551699    NY Female  Principal   11051       95            0 75   0,99947516*

*7,335080    NV   Male  Principal   21566        4            6  75   0,9993482*

## <a name="more-about-rximport"></a>Дополнительные сведения о функции rxImport

Функцию **rxImport** можно использовать не только для передачи данных, но и для их преобразования в процессе считывания. Например, можно указать количество символов для столбцов фиксированной ширины, предоставить описание переменных, задать уровни столбцов коэффициентов и даже создать уровни, которые будут использоваться после импорта.

**RxImport** функция назначает имена переменных столбцов во время импорта, но новые имена переменных можно указать с помощью *colInfo* параметра или изменение типов данных, с помощью *colClasses* параметра.

Указав дополнительные операции в параметре *transforms* , можно осуществлять простейшую обработку каждого блока считываемых данных.

## <a name="next-step"></a>Следующий шаг

[Создание таблицы SQL Server с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)

## <a name="previous-step"></a>Предыдущий шаг

[Преобразование данных с помощью языка R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

