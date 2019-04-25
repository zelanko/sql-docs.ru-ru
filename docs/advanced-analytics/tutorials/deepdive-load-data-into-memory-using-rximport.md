---
title: Загрузка данных в памяти, с помощью функции rxImport RevoScaleR - машинного обучения SQL Server
description: Руководство по загрузке данных с помощью языка R на SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 5fc29872795623bd0d9e72414a15add92591ec7d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641390"
---
# <a name="load-data-into-memory-using-rximport-sql-server-and-revoscaler-tutorial"></a>Загрузка данных в памяти, с помощью функции rxImport (руководство по SQL Server и RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Это занятие является частью [руководстве RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) по использованию [функций RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

[RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) функция может использоваться для перемещения данных из источника данных во фрейм данных в памяти сеанса или в файл XDF на диске. Если не указать файл в качестве назначения, данные помещаются в память как кадр данных.

На этом шаге вы узнаете, как получить данные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а затем с помощью **rxImport** функции, чтобы поместить интересующие вас данные в локальный файл. Таким образом, их можно будет повторно анализировать в локальном контексте вычисления, не выполняя запрос к базе данных еще раз.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Извлечение подмножества данных из SQL Server в локальную память

Вы решили, что вы хотите проанализировать только с высокой степенью риска более подробно. Исходная таблица в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет большой размер, поэтому вы хотите получить сведения о только что заказчиках. Вы затем загрузили эти данные во фрейм данных в памяти локальной рабочей станции.

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

    Если операция выполнена успешно, вы увидите сообщение о состоянии следующего вида: «Прочитано строк: 35, всего строк обработано: Время 35, общее фрагмента: 0,036 секунды»

4. Теперь, когда наблюдения с высоким риском в кадре данных в памяти, можно использовать различные функции R для работы с кадром данных. Например можно упорядочить клиентов по оценке риска и распечатать список клиентов, которые представляют наибольший риск.

    ```R
    orderedHighRisk <- highRisk[order(-highRisk$ccFraudProb),]
    row.names(orderedHighRisk) <- NULL
    head(orderedHighRisk)
    ```

**Результаты**

```R
ccFraudLogitScore   state gender cardholder balance numTrans numIntlTrans creditLine ccFraudProb1
9.786345    SD   Male  Principal   23456       25            5 75   0.99994382
9.433040    FL Female  Principal   20629       24           28 75   0.99992003
8.556785    NY Female  Principal   19064       82           53 43   0.99980784
8.188668    AZ Female  Principal   19948       29            0 75   0.99972235
7.551699    NY Female  Principal   11051       95            0 75   0.99947516
7.335080    NV   Male  Principal   21566        4            6  75   0.9993482
```

## <a name="more-about-rximport"></a>Дополнительные сведения о функции rxImport

Функцию **rxImport** можно использовать не только для передачи данных, но и для их преобразования в процессе считывания. Например, можно указать количество символов для столбцов фиксированной ширины, предоставить описание переменных, задать уровни столбцов коэффициентов и даже создать уровни, которые будут использоваться после импорта.

**RxImport** функция присваивает имена переменных столбцам в процессе импорта, но можно указать новые имена переменных с помощью *colInfo* параметр или изменить типы данных, с помощью *colClasses* параметра.

Указав дополнительные операции в параметре *transforms* , можно осуществлять простейшую обработку каждого блока считываемых данных.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Создание таблицы SQL Server с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)