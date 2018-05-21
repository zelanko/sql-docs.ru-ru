---
title: Обновленные документы по SSDT для SQL Server | Документация Майкрософт
description: Отображение фрагментов обновленного содержимого для последних изменений в документации по SQL Server Data Tools (SSDT) для Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: ssdt
ms.date: 04/28/2018
ms.openlocfilehash: 99b0844803e1ce95bd6f73b0d45a2baf867428ba
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-sql-server-data-tools-ssdt"></a>Новые и недавно обновленные: SQL Server Data Tools (SSDT)



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Даты обновлений:* &nbsp; **02.03.2018**&nbsp;–&nbsp;**28.04.2018**
- *Предметная область:* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Поддержка Azure Active Directory в SQL Server Data Tools (SSDT)](azure-active-directory.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Журнал изменений для SQL Server Data Tools (SSDT)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd"></a>1. &nbsp; [Журнал изменений для SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)

*Обновлено: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 29.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 de18314845cffa197b3fd2ed868f2c330760bedb 5487de1ed57c16a6517a3a8849f412c208f1889f  (PR=5676  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->





**SSDT для Visual Studio 2017 (15.6.0)**

Номер сборки: 14.0.16162.0. Дата выпуска: 10 апреля 2018 г.

**Новые возможности**


**SSIS**

1.  Устранена проблема, из-за которой задача обработки AS не записывает шаги обработки при выборе SQL Server 2016 и SQL Server 2017 в качестве целевых платформ.
2.  Устранена проблема, из-за которой предоставлялся несанкционированный доступ при открытии DTSX-файла с очень длинными локализованными именами задач в SSDT.
3.  Устранена проблема, из-за которой список переменных ScriptTask иногда пропадал из пользовательского интерфейса задач.
4.  Устранена проблема, из-за которой происходил сбой при добавлении копии существующего пакета, если он находился в SQL Server.
5.  Устранена проблема, из-за которой в некоторых диалоговых окнах редактора не удавалось выбрать пункт в поле со списком.
6.  Устранена проблема, из-за которой фон не менялся при переключении темы Visual Studio.
7.  Устранена проблема, из-за которой аннотация и метка загрузки не были видны при темной теме.
8.  Устранена проблема, из-за которой свойство состояния неправильно определялось для отключенных элементов панели элементов SSIS.
9.  Устранена проблема, из-за которой никогда не удавалось выполнить WebServiceTask.
10. Устранена проблема, из-за которой происходил сбой развертывания пакета, если строке подключения присваивалась переменная, в которой выражение зависело от параметров проекта.

**Установщик:**

1.  В заявление о конфиденциальности добавлена ссылка "Программа улучшения качества программного обеспечения для SQL Server Data Tools".
2.  Устранена проблема, из-за которой открывалось окно установщика Visual Studio при выборе параметра "Установить новую версию SQL Server Data Tools для экземпляра Visual Studio 2017".

**Известные проблемы**

1.  Задача запуска пакетов в службах SSIS не поддерживает отладку, если параметр ExecuteOutOfProcess имеет значение True. Эта проблема относится только к отладке. Она не влияет на сохранение, развертывание и запуск с использованием DTExec.exe или каталога SSIS.



**SSDT для Visual Studio 2017 (15.5.2)**

Номер сборки: 14.0.16156.0

**Новые возможности**


**Службы SSIS**
1.  Устранена проблема, из-за которой не удавалось перенести проекты служб SSIS 2008 при установке служб SSAS и SSIS в одном экземпляре Visual Studio 2017.
2.  Устранена проблема, из-за которой при установке конструктора отчетов Rdlc и служб SQL Server Integration Services в одном экземпляре Visual Studio 2017 не удавалось выполнить сборку проектов Rdlc.







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи

- [Новые + обновленные (11+6): &nbsp; &nbsp;**Углубленная аналитика для SQL** (документация)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (18+0): &nbsp;&nbsp;**Analysis Services для SQL** (документация)](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (218+14):  **Подключение к SQL** (документация)](../connect/new-updated-connect.md)
- [Новые + обновленные (14+0): &nbsp; &nbsp;**Ядро СУБД для SQL** (документация)](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (3+2): &nbsp; &nbsp;**Integration Services для SQL** (документация)](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (3+3): &nbsp; &nbsp;**Linux для SQL** (документация)](../linux/new-updated-linux.md)
- [Новые + обновленные (7+10): &nbsp; &nbsp;**Реляционные базы данных для SQL** (документация)](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (0+2): &nbsp; **&nbsp;Reporting Services для SQL** (документация)](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (1+3): &nbsp; &nbsp;**SQL Operations Studio** (документация)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(2+3): &nbsp; &nbsp;**Microsoft SQL Server** (документация)](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (1+1): &nbsp; &nbsp;**SQL Server Data Tools (SSDT)** (документация)](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (5+2): &nbsp; &nbsp;**SQL Server Management Studio (SSMS)** (документация)](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2): &nbsp; &nbsp;**Transact-SQL** (документация)](../t-sql/new-updated-t-sql.md)
- [Новые + обновленные (1+1): &nbsp;**&nbsp;Инструменты для SQL** (документация)](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0):  **Analytics Platform System для SQL** (документация)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../samples/new-updated-samples.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)

