---
title: "Загрузка данных в памяти с помощью rxImport | Документы Microsoft"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 47a42e9a-05a0-4a50-871d-de73253cf070
caps.latest.revision: "14"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3517ad7bb95f79dc2dec2567ecb88d64e78338bc
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="load-data-into-memory-using-rximport"></a>Загрузка данных в память с помощью функции rxImport

Функцию **rxImport** можно использовать для передачи данных из источника данных в кадр данных в памяти сеанса R или в файл XDF на диске. Если не указать файл в качестве назначения, данные помещаются в память как кадр данных.

На этом шаге вы узнаете, как получить данные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а затем использовать функцию rxImport перевод интересующих их данных в локальный файл. Таким образом, их можно будет повторно анализировать в локальном контексте вычисления, не выполняя запрос к базе данных еще раз.

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>Извлечение подмножества данных из SQL Server в локальную память

Вы решили более подробно изучить заказчиков с высокой степенью риска. Исходная таблица в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет большой размер, поэтому вы получите информацию только о заказчиках с высокой степенью риска и загрузите ее в кадр данных в памяти локальной рабочей станции.

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

3. Используйте функцию **rxImport** для фактической загрузки данные в кадр данных в локальном сеансе R.

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    Если операция выполнена успешно, вы увидите сообщение о состоянии: Считано строк: 35, Всего обработано строк: 35, Общее время фрагмента: 0,036 секунды

4. Теперь, когда наблюдения с высокой степенью риска находятся в кадре данных в памяти, можно использовать различные функции R для работы с кадром данных. Например, можно упорядочить клиентов по оценке риска и вывести данные по клиентам, которые представляют наибольший риск.

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

RxImport можно использовать не только для перемещения данных, но для преобразования данных в процессе их считывания. Например, можно указать количество символов для столбцов фиксированной ширины, предоставить описание переменных, задать уровни столбцов коэффициентов и даже создать уровни, которые будут использоваться после импорта.

Функция rxImport назначает имена переменных столбцов во время импорта, но новые имена переменных можно указать с помощью *colInfo* параметра и вы можете изменить типы данных, используя *colClasses* параметра.

Указав дополнительные операции в параметре *transforms* , можно осуществлять простейшую обработку каждого блока считываемых данных.

## <a name="next-step"></a>Следующий шаг

[Создание новой таблицы SQL Server, с помощью rxDataStep](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)

## <a name="previous-step"></a>Предыдущий шаг

[Преобразование данных с помощью R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="see-also"></a>См. также:

[Машинного обучения учебники](../../advanced-analytics/tutorials/machine-learning-services-tutorials.md)

