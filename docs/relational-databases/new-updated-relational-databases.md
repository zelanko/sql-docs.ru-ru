---
title: "Обновлено — документы по реляционным базам данных | Документация Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по реляционным базам данных."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.author: genemi
ms.openlocfilehash: 70cb071dc7b6f4ff15c5c7dee3f24bb352d6eb61
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Новые и недавно обновленные статьи — документы по реляционным базам данных



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **11.09.2017**&nbsp;–&nbsp;**27.09.2017**
- *Предметная область:* &nbsp; **Реляционные базы данных**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Импорт и экспорт данных в SQL Server и базе данных SQL Azure](import-export/overview-import-export.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Основные сведения о типах пространственных данных](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-spatial-data-types-overviewspatialspatial-data-types-overviewmd"></a>1. &nbsp; [Общие сведения о типах пространственных данных](spatial/spatial-data-types-overview.md)

*Обновлено: 26.09.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 27.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 96dd44cf49e96d1d543a629d49de297dba9c1753 2e9629f852ea42a213c7c24831bcfa53e40358f2  (PR=0  ,  Filename=spatial-data-types-overview.md  ,  Dirpath=docs\relational-databases\spatial\  ,  MergeCommitSha40=b33976cf92f23fbb13cee0c353fd40608d002d94) -->



 -  Существует два типа пространственных данных. Тип данных **geometry** поддерживает планарные или эвклидовы данные (система координат для плоской Земли). Тип данных **geometry** соответствует спецификации "Simple Features for SQL" консорциума OGC версии 1.1.0 и стандарту SQL MM (стандарт ISO).
 -
 - Кроме того, ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] поддерживает тип данных **geography**, который используется для хранения эллиптических (географических) данных, таких как координаты широты и долготы в GPS.
 -
 -> [!IMPORTANT]
 -> Подробное описание и примеры использования функций обработки пространственных данных, реализованных в ..!NCLUDE-NotShown--ssSQL11--../../includes/sssql11-md.md)], в том числе усовершенствования типов пространственных данных см. в скачиваемом техническом документе [New Spatial Features in SQL Server Code-Named "Denali"](http://go.microsoft.com/fwlink/?LinkId=226407) (Новые функции обработки пространственных данных в SQL Server с рабочим названием "Denali").
 -
 -##  <a name="objects"></a> Объекты пространственных данных
 - Типы данных **geometry** и **geography** поддерживают шестнадцать объектов пространственных данных или типов экземпляров. Однако только одиннадцать из этих типов экземпляров являются *материализуемыми*. Такие экземпляры можно создавать в базе данных и работать с ними. Эти экземпляры наследуют от родительских типов данных некоторые свойства, которые разделяют их на **Points**, **LineStrings, CircularStrings**, **CompoundCurves**, **Polygons**, **CurvePolygons** или несколько экземпляров **geometry** или **geography** в коллекции **GeometryCollection**. Тип**Geography** имеет дополнительный тип экземпляра **FullGlobe**.
 -
 - На рисунке ниже изображена иерархия **geometry** , на которой основаны типы данных **geometry** и **geography** . Инстанциируемые типы **geometry** и **geography** выделены синим.
 -
 - ![geom_hierarchy--../../relational-databases/spatial/media/geom-hierarchy.gif)
 -
 - Как показано на рисунке, десятью материализуемыми типами **geometry** и **geography** являются **Point**, **MultiPoint**, **LineString**, **CircularString**, **MultiLineString**, **CompoundCurve**, **Polygon**, **CurvePolygon**, **MultiPolygon**и **GeometryCollection**. Есть один дополнительный тип, допускающий создание экземпляров, для типа данных geography: **FullGlobe**. Типы данных **geometry** и **geography** могут распознавать определенный экземпляр, если он имеет правильный формат, даже в том случае, если он не был определен явно. Например, если определить экземпляр **Point** явно с помощью метода STPointFromText(), то типы данных **geometry** и **geography** будут распознавать экземпляр как **Point**, если входные данные метода имели правильный формат. Если определить такой же экземпляр с помощью метода `STGeomFromText()` , то оба типа данных **geometry** и **geography** будут распознавать экземпляр как **Point**.







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+1): **Углубленная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (0+1): **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (4+1): **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (17+0): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (3+0): **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (1+1): **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (2+0): **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (0+1): **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+1): **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+0): **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


