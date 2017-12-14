---
title: "Обновленные документы по SQL Server | Документация Майкрософт"
description: "Отрывки из недавно обновленного содержимого в документации по SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: 
ms.component: sql-non-specified
ms.suite: sql
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: sql-server
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.author: genemi
ms.openlocfilehash: 77a97d94d005b43bf4c1a313a15a501cbe74a216
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="new-and-recently-updated-sql-server-docs"></a>Новые и недавно обновленные документы для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **28.09.2017**&nbsp;–&nbsp;**02.12.2017**
- *Предметная область:* &nbsp; **SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Партнеры по разработке SQL Server](partner-dev-sql-server.md)
2. [Партнеры в области высокой доступности и аварийного восстановления SQL Server](partner-hadr-sql-server.md)
3. [Партнеры по управлению SQL Server](partner-management-sql-server.md)
4. [Партнеры по мониторингу SQL Server](partner-monitor-sql-server.md)
5. [Заметки о выпуске SQL Server 2012 с пакетом обновления 4 (SP4)](sql-server-2012-sp4-release-notes.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [SQL Server 2017 Release Notes (Заметки о выпуске SQL Server 2017)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-2017-release-notessql-server-2017-release-notesmd"></a>1. &nbsp; [Заметки о выпуске SQL Server 2017](sql-server-2017-release-notes.md)

*Обновлено: 20.11.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 37.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c9ac7e027e32b17bb9b54a4a878f70a70404f1cb 5b1aa8dc715fbb08d82b241f1e47f6e443b3e2fc  (PR=4032  ,  Filename=sql-server-2017-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=7f8aebc72e7d0c8cff3990865c9f1316996a67d5) -->



- **Решение.** Сначала перезагрузите компьютер и проверьте доступность сетевой папки FILESTREAM. Если она по-прежнему недоступна, выполните следующие действия.

    1. В диспетчере конфигурации SQL Server щелкните экземпляр SQL Server правой кнопкой мыши и выберите пункт **Свойства**.
    2. На вкладке **FILESTREAM** снимите флажок **Разрешить FILESTREAM при потоковом доступе файлового ввода-вывода**, а затем нажмите кнопку **Применить**.
    3. Снова установите флажок **Разрешить FILESTREAM при потоковом доступе файлового ввода-вывода** для имени исходной общей папки и нажмите кнопку **Применить**.

**Службы Master Data Services (MDS)**

- **Проблема и последствия для клиентов:** когда на странице разрешений пользователя предоставляется разрешение для корневого уровня в представлении сущностей в виде дерева, отображается следующая ошибка: `"The model permission cannot be saved. The object guid is not valid"`

- **Решения.**
  - Предоставьте разрешение для подузлов в представлении в виде дерева, а не для корневого уровня.
  - либо
  - Запустите скрипт, описанный в блоге команды разработчиков MDS, посвященном [ошибке при применении разрешения на уровне сущности](http://sqlblog.com/blogs/mds_team/archive/2017/09/05/sql-server-2016-sp1-cu4-regression-error-while-applying-permission-on-entity-level-quick-workaround.aspx).

**службы Analysis Services**

- **Проблема и последствия для клиентов.** Соединители данных для приведенных ниже источников еще недоступны для табличных моделей на уровне совместимости 1400.
  - Amazon Redshift
  - IBM Netezza
  - Impala
- **Решение.** Отсутствует.

- **Проблема и последствия для клиентов:** в моделях прямых запросов на уровне совместимости 1400 с перспективами может возникнуть сбой при запросе или обнаружении метаданных.
- **Решение.** Удалите перспективы и повторите развертывание.







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


