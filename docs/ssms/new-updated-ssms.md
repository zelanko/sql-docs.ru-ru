---
title: "Обновленные документы по SSMS для SQL Server | Документация Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по SQL Server Management Studio (SSMS) для Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: 
ms.component: ssms
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: 
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.author: genemi
ms.workload: ssms-sql-server-management-studio
ms.openlocfilehash: a1a9156ef4bc2846f377f9c0695ec015d58606dd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Новые и недавно обновленные: SQL Server Management Studio (SSMS) для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **28.09.2017**&nbsp;–&nbsp;**02.12.2017**
- *Предметная область:* &nbsp; **SQL Server Management Studio (SSMS)**.




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

1. [Среда SQL Server Management Studio (SSMS) — журнал изменений](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>1. &nbsp; [Среда SQL Server Management Studio (SSMS) — журнал изменений](sql-server-management-studio-changelog-ssms.md)

*Обновлено: 09.10.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 23.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f483a7e0ba53cff80d3f2d33c9196906d27a7a61 c125f43f0a45e70ce180e62edecc68bdcffd5086  (PR=3441  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=29122bdf543e82c1f429cf401b5fe1d8383515fc) -->



**[SSMS 17.3--download-sql-server-management-studio-ssms.md)**

Общедоступная версия | Номер сборки: 14.0.17199.0

**Усовершенствования**


- Добавлен новый мастер импорта неструктурированных файлов, работающий на базе интеллектуальной платформы, которая упрощает процесс импорта CSV-файлов и не требует от пользователей многочисленных действий или специализированных знаний. Подробные сведения см. в разделе [Import Flat File to SQL Wizard--../relational-databases/import-export/import-flat-file-wizard.md).
- В обозреватель объектов добавлен узел XEvent Profiler. Подробные сведения см. в разделе [Use the SSMS XEvent Profiler--../relational-databases/extended-events/use-the-ssms-xe-profiler.md).
- Обновлена фильтрация и классификация ожиданий в отчете об истории ожиданий из панели мониторинга производительности.
- Добавлена проверка синтаксиса функции Predict.
- Добавлена проверка синтаксиса запросов в функции управления внешними библиотеками.
- Добавлена поддержка SMO для управления внешними библиотеками.
- Добавлена поддержка запуска PowerShell в окне "Зарегистрированные серверы" (требуется новый модуль PowerShell для SQL).
- AlwaysOn: добавлена [read-only routing support--../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md) для групп доступности.
- Добавлена возможность отправлять в окно вывода данные трассировки по входам с использованием проверки подлинности "Active Directory — универсальная с поддержкой MFA". По умолчанию эта функция отключена, и ее нужно включить в параметрах пользователя, последовательно выбрав "Сервис" > "Параметры" > "Службы Azure" > "Облако Azure" > "Уровень трассировки для окна вывода ADAL".
- Хранилище запросов
  - Пользовательский интерфейс хранилища запросов доступен, даже когда служба QDS отключена, при условии, что она записала какие-либо данные.
  - Пользовательский интерфейс хранилища запросов теперь предоставляет классификацию ожиданий во всех существующих отчетах. За счет этого пользователям будут доступны сценарии "Топ ожидающих запросов" и многие другие.
- Включать заголовки параметров сценариев стало необязательно. По умолчанию эта возможность отключена, и ее можно включить в параметрах пользователя, последовательно выбрав "Сервис" > "Параметры" > "Обозреватель объектов SQL Server" > "Сценарии" > "Включить заголовок с параметрами сценариев". Это связано с [элементом Connect 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199).







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новые + обновленные (3+14): **Углубленная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (1+0): **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (87+0): **Analytics Platform System для SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (5+4): **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (0+1): **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (2+2): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (10+9): **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (2+4): **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (4+2): **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (0+1): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (21+0): **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(5+1): **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1): **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (1+0): **Помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+1): **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2): **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


