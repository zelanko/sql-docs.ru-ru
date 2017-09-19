---
title: "Обновленные документы по SQL Server | Документация Майкрософт"
description: "Отрывки из недавно обновленного содержимого в документации по SQL Server."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: sql-server
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: bd22355518bde09b5af006062b2ec03cf11a7597
ms.contentlocale: ru-ru
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-docs"></a>Новые и недавно обновленные документы для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат выхода обновлений:* &nbsp; **18.07.2017** &nbsp;—&nbsp; **11.09.2017**
- *Предметная область:* &nbsp; **SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [SQL Server 2008 R2 SP2 Release Notes](sql-server-2008-r2-sp2-release-notes.md)
2. [Заметки о выпуске SQL Server 2012](sql-server-2012-release-notes.md)
3. [SQL Server 2012 SP1 Release Notes](sql-server-2012-sp1-release-notes.md)
4. [SQL Server 2012 SP2 Release Notes](sql-server-2012-sp2-release-notes.md)
5. [Заметки о выпуске SQL Server 2012 с пакетом обновления 3 (SP3)](sql-server-2012-sp3-release-notes.md)
6. [SQL Server 2014 Release Notes](sql-server-2014-release-notes.md)
7. [Окно справки и автономное содержимое для SQL Server](sql-server-help-installation.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Что нового в SQL Server 2016](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-whats-new-in-sql-server-2016what-s-new-in-sql-server-2016md"></a>1. &nbsp;[Что нового в SQL Server 2016](what-s-new-in-sql-server-2016.md)

*Обновлено: 08.09.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 34.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e5bc0c05f120289f09a535400a4d521e4113ae55 0607d0a9af1c9a8dd9d3d7b0606895ff23bbffdc  (PR=0  ,  Filename=what-s-new-in-sql-server-2016.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=b97cc9723d563b19c85661f5ad7049a96fc904ff) -->



- Скачайте **бесплатный** [**выпуск SQL Server 2016 Developer Edition**](https://www.microsoft.com/en-us/cloud-platform/sql-server-editions-developers).
- Скачайте последнюю версию [SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).
- Есть учетная запись Azure? Запустите [виртуальную машину с уже установленным решением SQL Server 2016](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/).

**Ядро СУБД SQL Server 2016**

- Теперь вы можете настроить **несколько файлов базы данных tempDB** во время установки и настройки SQL Server.
- В базе данных нового **хранилища запросов** хранятся тексты запросов, планы выполнения и метрики производительности. Это позволяет легко выполнять мониторинг и устранять проблемы с производительностью. На панели мониторинга указано, какие запросы потребляют больше всего времени, памяти или ресурсов ЦП.
- **Темпоральные таблицы** — это хронологические таблицы, в которые записываются все изменения данных, а также дата и время таких изменений.
- Новые встроенные средства **поддержки JSON** в SQL Server обеспечивают импорт, экспорт, синтаксический анализ и хранение файлов JSON.
- Новый обработчик запросов **PolyBase** интегрирует SQL Server с внешними данными в Hadoop или хранилище BLOB-объектов Azure. Теперь вы можете импортировать и экспортировать данные, а также выполнять запросы.
- Новая функция **Stretch Database** позволяет выполнять безопасную динамическую архивацию данных из локальной базы данных SQL Server в базу данных Azure SQL в облаке. SQL Server автоматически обращается к данным в локальных и удаленных связанных базах данных.
- **Выполняющаяся в памяти OLTP.**
    - Реализована поддержка FOREIGN KEY, ограничений UNIQUE и CHECK, а также скомпилированных в собственном коде хранимых процедур OR, NOT SELECT DISTINCT, OUTER JOIN и вложенных запросов в SELECT.
    - Поддерживаются таблицы до 2 ТБ (от 256 ГБ).
    - Усовершенствованы индексы хранилища столбцов для сортировки и поддержки групп доступности AlwaysOn.
- Новые функции безопасности:
    - **Постоянное шифрование.** Если оно включено, доступ к зашифрованным конфиденциальным данным в базе данных SQL Server 2016 получают только приложения с ключом шифрования. Ключ никогда не передается в SQL Server.







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Этот раздел содержит похожие статьи, аналогичные недавно измененным, для других предметных областей в том же общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новые + обновленные (3+12): документация по **расширенной аналитике для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (5+0): документация по **подключению к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (5+1): документация по **ядру СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (19+82): документация по **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (1+8): документация по **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (12+1): документация по **реляционным базам данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (0+1): документация по **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (7+1): документация по **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (1+1): документация по **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (0+2): документация по **помощнику по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (1+4): документация по **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (4+1): документация по **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Новые + обновленные (0+1): документация по **средствам для SQL**](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация по **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация по **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)



