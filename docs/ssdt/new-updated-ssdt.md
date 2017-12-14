---
title: "Обновленные документы по SSDT для SQL Server | Документация Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по SQL Server Data Tools (SSDT) для Microsoft SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: 
ms.component: ssdt
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.author: genemi
ms.workload: ssdt-sql-server-data-tools
ms.openlocfilehash: 07bfbac52cdd7d118ffd58842fe2085d52265e6f
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="new-and-recently-updated-sql-server-data-tools-ssdt"></a>Новые и недавно обновленные: SQL Server Data Tools (SSDT)



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **28.09.2017**&nbsp;–&nbsp;**02.12.2017**
- *Предметная область:* &nbsp; **SQL Server Data Tools (SSDT)**.




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

1. [Журнал изменений для SQL Server Data Tools (SSDT)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd"></a>1. &nbsp; [Журнал изменений для SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)

*Обновлено: 20.11.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 28.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7700cae7cafe1dac95c240b014f14d9c83e32be4 6416949beaee91da2f77dfebb9eb5ed363db4cb7  (PR=4032  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=7f8aebc72e7d0c8cff3990865c9f1316996a67d5) -->




**SSDT для Visual Studio 2017 (предварительная версия 15.4.0)**

Номер сборки: 14.0.16134.0

**Новые возможности**


В этом выпуске представлен автономный веб-установщик для проектов баз данных SQL Server, Analysis Services, Reporting Services и Integration Services в Visual Studio 2017 15.4 и более поздних версиях.

**Установщик**


- Пользователь может задавать псевдоним при установке нового экземпляра SSDT для VS2017.
- Скрытие флажков выбора компонентов установщика, если не выбрано ни одного экземпляра VS.
- Уточнены некоторые сообщения установщика на основе отзывов пользователей.
- Устранена проблема, связанная с тем, что установщик не поддерживает обновление.


**Службы SSIS**


- Устранена проблема, связанная с тем, что мастер импорта и экспорта данных не может указывать источник данных, если установлен пакет дополнительных компонентов Azure.
- Устранена проблема, связанная с тем, что при редактировании задачи процесса служб Analysis Services SSIS возникает исключение при переключении соединения.
- Устранена проблема, связанная с нарушением работы компонентов CDC после применения исправления SQL, которое добавляет столбец __$command_id.
- Устранена проблема, связанная с невозможностью изменения и выполнения стороннего пакета при использовании прежней версии SQL Server в качестве целевой платформы.
- Устранена проблема, связанная с неправильным отображением диалогового окна настройки источника неструктурированного файла при двойном щелчке DTSWizard.exe и выбора источника неструктурированного файла.
- Устранена проблема, связанная с невозможностью выполнения пакета, содержащего компонент или задачу пакета дополнительных компонентов Azure при выборе SQL Server 2017 в качестве целевой платформы.


**Известные проблемы**

- Установщик не локализован.
- Задача запуска пакетов в службах SSIS не поддерживает отладку, если параметр *ExecuteOutOfProcess* имеет значение True. Эта проблема относится только к отладке. Она не влияет на сохранение, развертывание и запуск с использованием DTExec.exe или каталога SSIS.


**SSDT 17.3 для Visual Studio 2015**

Номер сборки: 14.0.61709.290

**Новые возможности**


**Analysis Services**

- Поддержка Cosmos DB и HDI Spark в моделях уровня 1400.
- Свойства табличных источников данных
- Теперь вы можете выбрать "Пустой запрос" при создании запроса в редакторе для моделей с уровнем совместимости 1400.
- Редактор запросов для моделей режима 1400 теперь позволяет сохранять запросы без автоматической обработки новых таблиц.







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


