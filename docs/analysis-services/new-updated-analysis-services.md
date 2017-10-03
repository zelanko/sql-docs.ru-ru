---
title: "Обновлено - служб Analysis Services для SQL Server docs | Документы Microsoft"
description: "Отображение фрагментов обновленное содержимое для последних измененных в документации служб Analysis Services для Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: analysis-services
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.author: genemi
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: a21f82dd5a0bd4ef59abc639d9441be25191a21b
ms.contentlocale: ru-ru
ms.lasthandoff: 10/02/2017

---
# <a name="new-and-recently-updated-analysis-services-for-sql-server"></a>Новые и недавно обновленные: службы Analysis Services для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон обновлений дат:* &nbsp; **2017 г-09-11** &nbsp; - в - &nbsp; **2017 г-09-27**
- *Предметной области:* &nbsp; **служб Analysis Services для SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


***На данный момент новых статей нет.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Какой &#39; новые возможности служб Analysis Services SQL Server 2017 г.](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-what39s-new-in-sql-server-2017-analysis-serviceswhat-s-new-in-sql-server-analysis-services-2017md"></a>1. &nbsp;[Что &#39; новые возможности служб Analysis Services SQL Server 2017 г.](what-s-new-in-sql-server-analysis-services-2017.md)

*Обновлено: 2017 г-09-22* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 143.  ms.author= "owend".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c8d75883f07e6e32859728d09139920eb9bf65c5 d206e83413d15a6e6116120e4a98dda9c8ce81d8  (PR=3278  ,  Filename=what-s-new-in-sql-server-analysis-services-2017.md  ,  Dirpath=docs\analysis-services\  ,  MergeCommitSha40=656e62f36446db4ef5b232129130a0253d2aebdf) -->



**Безопасность на уровне объекта**

В этом выпуске вводится [безопасность на уровне объекта--... / analysis-services/tabular-models/object-level-security.md) для таблиц и столбцов. Помимо ограничения доступа к данным таблицы и столбца, можно защитить конфиденциальные имена таблиц и столбцов. Благодаря этому злоумышленник не сможет узнать о существовании этих таблиц.

Безопасность на уровне объекта необходимо задать, используя метаданные на основе JSON, табличных языка скриптов модели (TMSL) или табличной модели объектов (TOM).

Например, приведенный ниже код позволяет защитить таблицу Product в образце табличной модели Adventure Works путем присвоения свойству **MetadataPermission** класса **TablePermission** значения **None**.

```
//Find the Users role in Adventure Works and secure the Product table
ModelRole role = db.Model.Roles.Find("Users");
Table productTable = db.Model.Tables.Find("Product");
if (role != null && productTable != null)
{
    TablePermission tablePermission;
    if (role.TablePermissions.Contains(productTable.Name))
    {
        tablePermission = role.TablePermissions[productTable.Name];
    }
    else
    {
        tablePermission = new TablePermission();
        role.TablePermissions.Add(tablePermission);
        tablePermission.Table = productTable;
    }
    tablePermission.MetadataPermission = MetadataPermission.None;
}
db.Update(UpdateOptions.ExpandFull);
```

**Динамические административные представления (DMV)**

[Динамических административных представлений--... / analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md) запросы в SQL Server Profiler, которые возвращают сведения о локальных операциях сервера и исправности сервера.
Этот выпуск включает усовершенствования для [динамические административные представления](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services) (DMV) для табличных моделей на уровне совместимости 1200 и 1400.







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новый + обновленные (0 + 1): **Advanced Analytics для SQL** документы](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новый + обновленные (0 + 1): **служб Analysis Services для SQL** документы](../analysis-services/new-updated-analysis-services.md)
- [Новый + обновленные (4 + 1): **СУБД для SQL** документы](../database-engine/new-updated-database-engine.md)
- [Новый + обновленные (17 + 0): **службы Integration Services для SQL** документы](../integration-services/new-updated-integration-services.md)
- [Новый + обновленные (3 + 0): **Linux для SQL** документы](../linux/new-updated-linux.md)
- [Новый + обновленные (1 + 1): **реляционных баз данных для SQL** документы](../relational-databases/new-updated-relational-databases.md)
- [Новый + обновленные (2 + 0): **служб Reporting Services для SQL** документы](../reporting-services/new-updated-reporting-services.md)
- [Новый + обновленные (0 + 1): **SQL Server Management Studio (SSMS)** документы](../ssms/new-updated-ssms.md)
- [Новый + обновленные (0 + 1): **Transact-SQL** документы](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новый + обновленные (0 + 0): **подключение к SQL** документы](../connect/new-updated-connect.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новый + обновленные (0 + 0): **Microsoft SQL Server** документы](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+0): **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новый + обновленные (0 + 0): **средства для SQL** документы](../tools/new-updated-tools.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)



