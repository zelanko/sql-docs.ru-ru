---
title: "Обновлено - T-SQL docs | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации, Transact-SQL."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.workload: t-sql
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: fa2ad3f4bc6071c54b9996a893ee584ba215100f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-transact-sql-docs"></a>Обновление новых и недавно: docs Transact-SQL



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон обновлений дат:* &nbsp; **2017 г-07-18** &nbsp; - в - &nbsp; **2017 г-09-11**
- *Предметной области:* &nbsp; **T-SQL**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Следующие ссылки на новые статьи, которые недавно были добавлены.


1. [ПРОГНОЗ (Transact-SQL)](queries/predict-transact-sql.md)
2. [ALTER ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)](statements/alter-external-library-transact-sql.md)
3. [Создание ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)](statements/create-external-library-transact-sql.md)
4. [DROP ВНЕШНЕЙ БИБЛИОТЕКИ (Transact-SQL)](statements/drop-external-library-transact-sql.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе отображается отрывки обновлений, полученные из статей, в которых были недавно крупных обновлений.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

Compact представлены ссылки на обновленные статьи, которые перечислены в разделе отрывки.

1. [CAST и CONVERT (Transact-SQL)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-cast-and-convert-transact-sqlfunctionscast-and-convert-transact-sqlmd"></a>1. &nbsp;[CAST и CONVERT (Transact-SQL)](functions/cast-and-convert-transact-sql.md)

*Обновлено: 2017 г-09-08* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 647.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b805ecddecda72ffc026c3866b5284a79b69fb3f f2906eaf87c7cdf1409922d4efba8cd1c5635674  (PR=0  ,  Filename=cast-and-convert-transact-sql.md  ,  Dirpath=docs\t-sql\functions\  ,  MergeCommitSha40=b97cc9723d563b19c85661f5ad7049a96fc904ff) -->



**Л. Использование функции CAST с арифметическими операторами**

В следующем примере вычисляется столбец значений, разделив цена единицы товара (`UnitPrice`), процент скидки (`UnitPriceDiscountPct`). Результат преобразуется к типу данных `int` после округления до ближайшего целого числа. Использует AdventureWorksDW.

```
SELECT ProductKey, UnitPrice,UnitPriceDiscountPct,
       CAST(ROUND (UnitPrice*UnitPriceDiscountPct,0) AS int) AS DiscountPrice
FROM dbo.FactResellerSales
WHERE SalesOrderNumber = 'SO47355'
      AND UnitPriceDiscountPct > .02;
```

..! ДОБАВИТЬ NotShown--ssResult--... /.. /includes/ssresult-MD.MD)]

```
ProductKey  UnitPrice  UnitPriceDiscountPct  DiscountPrice
----------  ---------  --------------------  -------------
323         430.6445   0.05                  22
213         18.5043    0.05                  1
456         37.4950    0.10                  4
456         37.4950    0.10                  4
216         18.5043    0.05                  1
```

**М. Использование функции CAST для объединения**

Следующий пример Сцепляет несимвольных выражения приведения. Использует AdventureWorksDW.

```
SELECT 'The list price is ' + CAST(ListPrice AS varchar(12)) AS ListPrice
FROM dbo.DimProduct
WHERE ListPrice BETWEEN 350.00 AND 400.00;
```

..! ДОБАВИТЬ NotShown--ssResult--... /.. /includes/ssresult-MD.MD)]

```
ListPrice
------------------------
The list price is 357.06
The list price is 364.09
The list price is 364.09
The list price is 364.09
The list price is 364.09
```

**М. Использование функции CAST для получения удобочитаемого текста**

В следующем примере используется ПРИВЕДЕНИЕ в списке ВЫБОРА для преобразования `Name` столбец **char(10)** столбца. Использует AdventureWorksDW.

```
SELECT DISTINCT CAST(EnglishProductName AS char(10)) AS Name, ListPrice
FROM dbo.DimProduct
WHERE EnglishProductName LIKE 'Long-Sleeve Logo Jersey, M';
```

..! ДОБАВИТЬ NotShown--ssResult--... /.. /includes/ssresult-MD.MD)]







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

В этом разделе перечислены схожий статей для недавно обновлены статьи в других предметных областей, в общедоступный репозиторий GitHub.com: [MicrosoftDocs, sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новый + обновленные (3 + 12): **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (5 + 0): **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новый + обновленные (5 + 1): **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (19 + 82): **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (1 + 8): **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (12 + 1): **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (0 + 1): **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (7 + 1): **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новый + обновленные (1 + 1): **SQL Server Data Tools (SSDT)** документы](../ssdt/new-updated-ssdt.md)
- [Новый + обновленные (0 + 2): **SQL Server Migration Assistant (SSMA)** документы](../ssma/new-updated-ssma.md)
- [Новый + обновленные (1 + 4): **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (4 + 1): **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)
- [Новый + обновленные (0 + 1): **средства для SQL** документы](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новый + обновленные (0 + 0): **служб Analysis Services для SQL** документы](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новый + обновленные (0 + 0): **Master Data Services (MDS) для SQL** документы](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)



