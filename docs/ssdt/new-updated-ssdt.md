---
title: "Обновленные — документы о SSDT для SQL Server | Документы Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по SQL Server Data Tools (SSDT) для Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 06/30/2017
ms.author: genemi
ms.workload: ssdt-sql-server-data-tools
ms.translationtype: Human Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 5e43cb76dac922b3c43318b2a9f539ab19ec7bfe
ms.contentlocale: ru-ru
ms.lasthandoff: 07/03/2017

---
<a id="new-and-recently-updated-sql-server-data-tools-ssdt" class="xliff"></a>

# Новые и недавно обновленные: SQL Server Data Tools (SSDT)



Почти каждый день Корпорация Майкрософт обновляет некоторые из его существующих статей на его [Docs.Microsoft.com](http://docs.microsoft.com/) документации веб-сайта. В этой статье отображает выдержки из недавно обновлены статьи. Ссылки на новые статьи также может быть указан.

В этой статье создается программой, которая периодически запускается повторно. Иногда фрагмент могут отображаться идеально подходит форматирования или как разметки из статьи источника. Образы никогда не отображается.

Следующий диапазон дат и темы отображаются последние обновления:



- *Диапазон дат для обновлений:* &nbsp; **17.05.2017** &nbsp;–&nbsp; **30.06.2017**
- *Предметная область:* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

<a id="new-articles-created-recently" class="xliff"></a>

## Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые были добавлены недавно.


*Сейчас новые статьи отсутствуют.*



&nbsp;

<a id="updated-articles-with-excerpts" class="xliff"></a>

## Обновлены статьи с отрывки

В этом разделе отображается отрывки обновлений, полученные из статей, в которых были недавно крупных обновлений.

Из семантической контексту отрывки, показанные здесь отображаются раздельно. Кроме того иногда фрагмент отделяется от синтаксис важные разметки окружающего в реальной статьи. Поэтому эти отрывки являются только общие рекомендации. Только отрывки позволяют знаете ли потребностей гарантирует времени, нажмите кнопку и посетите реальной статьи.

Для этих и других причин не копировать из этих отрывки кода и не выполняют как точное истинности любой фрагмент текста. Вместо этого посетите реальной статьи.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

<a id="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd" class="xliff"></a>

### 1. &nbsp; [Журнал изменений для SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)

*Обновлено: 19.05.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 21.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cf17883ce0daf75fdf88881171bf4042558b1cf4 536fe0fe41b023a4186f494a509fa14fcbafccf4  (PR=1777  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=5bd0e1d3955d898824d285d28979089e2de6f322) -->



Подробные сведения о новых и измененных возможностях см. в [блоге группы разработчиков SSDT](https://blogs.msdn.microsoft.com/ssdt/)

**SSDT 17.1**

Номер сборки: 14.0.61705.170

**Новые возможности**

**Проекты Analysis Services:**
- Пользователи могут задавать кодирования ссылок на столбцы в пользовательском Интерфейсе 1400 моделей
- Технология IntelliSense, не относящиеся к модели теперь доступна в автономном режиме
- Обозреватель табличных моделей теперь содержит узел для представления именованных M выражения, доступные в модели (1400 уровня совместимости табличные модели)
- Azure Active Directory Выбор людей аналогично IAM портал Microsoft Azure, теперь доступны при настройке членов роли в табличных моделях

**Проекты базы данных:**
- Обновлено до DacFx 17,1

**Исправления ошибок**

- Устранена проблема, где имя группы конструкторы бизнес-аналитики был неправильно отображается в Visual Studio параметры в VS2017
- Устранена проблема, где сбой может возникать создания карты кода для решения, проекта отчета или проекта как
- Исправлен ряд проблем с интеграцией PowerQuery для табличных моделей уровня совместимости Analysis Services 1400
- Устранена проблема в новом редакторе DAX окна инструментов, где оператор присваивания не удалось на отдельной строке при определении меры
- Устранена проблема, препятствующая отображение табличных мер обновление при переименовании мер в перспективе
- Обновленные встроенной рабочей ядро служб Analysis Services и табличной объектной модели, исправляющий регрессии, вызвавшего 1200 табличных проектов, содержащем переводы Сбой развертывания на сервер SQL Server 2016 Analysis Services
- Исправлена проблема производительности, который создал creation\deletion новый 1400 табличных источников данных очень медленно
- Устранена проблема, где схема представления источника данных в многомерных моделях может остановить подготовку, если изменение представления быстро между различных представлений источников данных

**DacFx 17.1**

- Устранена проблема, при шифровании столбец с оптимизированными для памяти таблиц со столбцами других идентификаторов
- Поддержка SQLDOM CATALOG_COLLATION параметр для СОЗДАНИЯ базы данных





&nbsp;

<a name="compactupdatedlist"/>

<a id="compact-list-of-articles-updated-recently" class="xliff"></a>

## Сокращенный список статей, недавно обновлены

Compact представлены ссылки на обновленные статьи, перечисленные в предыдущем разделе.

1. [Журнал изменений для SQL Server Data Tools (SSDT)](#TitleNum_1)




<a name="sisters2"/>

&nbsp;

<a id="sister-articles" class="xliff"></a>

## Филиалы статей

Этот раздел содержит похожие статьи, аналогичные недавно измененным, для других предметных областей в том же репозитории GitHub.com: [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170630-1150  -->

<a id="subject-areas-which-do-have-new-or-recently-updated-articles" class="xliff"></a>

#### Предметные области, содержащие новые или недавно обновленные статьи

- [Новые + обновленные (12+2): **углубленная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (1+0): **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (0+2): **подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (3+0): **СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (1+2): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (2+8): **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (1+0): **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (5+5): **реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (2+0): **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (0+4): **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1): **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (0+1): **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (1+0): **инструменты для SQL**](../tools/new-updated-tools.md)


<a id="subject-areas-which-have-no-new-or-recently-updated-articles" class="xliff"></a>

#### Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


&nbsp;


