---
title: Загрузка данных с помощью функции rxImport
description: Узнайте, как получить данные из SQL Server, а затем использовать функцию rxImport, чтобы поместить интересующие вас данные в локальный файл.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 1eb487a19e911808d11de0c4f56c06af2b30c0cb
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470535"
---
# <a name="load-data-into-memory-using-rximport-sql-server-and-revoscaler-tutorial"></a>Загрузка данных в память с помощью rxImport (учебник по SQL Server и RevoScaleR)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Эта часть 10 входит в состав [серии учебников по RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md), посвященной использованию [функций RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) в SQL Server.

В этом учебнике вы узнаете, как получить данные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а затем использовать функцию **rxImport**, чтобы поместить интересующие вас данные в локальный файл. Таким образом, их можно будет повторно анализировать в локальном контексте вычисления, не выполняя запрос к базе данных еще раз.

Функцию [rxImport](/machine-learning-server/r-reference/revoscaler/rximport) можно использовать для передачи данных из источника данных в кадр данных в памяти сеанса или в файл XDF на диске. Если не указать файл в качестве назначения, данные помещаются в память как кадр данных.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Извлечение подмножества данных из SQL Server в локальную память

Вы решили более подробно изучить заказчиков с высокой степенью риска. Исходная таблица в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет большой размер, поэтому вы хотите получить информацию только о заказчиках с высокой степенью риска. Затем вы загрузите ее в кадр данных в памяти локальной рабочей станции.

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

3. Вызовите функцию [rxImport](/machine-learning-server/r-reference/revoscaler/rximport) для считывания данных в кадр данных в локальном сеансе R.

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    Если операция выполнена успешно, вы увидите сообщение о состоянии наподобие следующего: "Считано строк: 35. Всего обработано строк: 35. Общее время фрагмента: 0,036 секунды"

4. Теперь, когда наблюдения с высокой степенью риска находятся в кадре данных в памяти, можно использовать различные функции R для работы с кадром данных. Например, можно упорядочить клиентов по оценке риска и вывести список клиентов, которые представляют наибольший риск.

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

Функция **rxImport** присваивает имена переменных столбцам в процессе импорта, но вы можете указать новые имена переменных с помощью параметра *colInfo* или изменить типы данных с помощью параметра *colClasses*.

Указав дополнительные операции в параметре *transforms* , можно осуществлять простейшую обработку каждого блока считываемых данных.

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Создание таблицы SQL Server с помощью rxDataStep](../../machine-learning/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)