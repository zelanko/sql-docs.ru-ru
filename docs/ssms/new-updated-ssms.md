---
title: Обновленные документы по SSMS для SQL Server | Документация Майкрософт
description: Отображение фрагментов обновленного содержимого для последних изменений в документации по SQL Server Management Studio (SSMS) для Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: ssms
ms.date: 04/28/2018
ms.openlocfilehash: 1ce446219f71baca0f4cdedc835fca929b572a0f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Новые и недавно обновленные: SQL Server Management Studio (SSMS) для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Даты обновлений:* &nbsp; **02.03.2018**&nbsp;–&nbsp;**28.04.2018**
- *Предметная область:* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Учебник. Подключение к экземпляру SQL Server и выполнение запросов с помощью SQL Server Management Studio](tutorials/connect-query-sql-server.md)
2. [Учебник. Создание скриптов для объектов в среде SQL Server Management Studio](tutorials/scripting-ssms.md)
3. [Учебник. Компоненты и конфигурация SQL Server Management Studio](tutorials/ssms-configuration.md)
4. [Учебник: дополнительные советы и рекомендации по использованию SSMS](tutorials/ssms-tricks.md)
5. [Учебник. Использование шаблонов в среде SQL Server Management Studio](tutorials/templates-ssms.md)



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
2. [Учебники по SQL Server Management Studio (SSMS)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>1. &nbsp; [Среда SQL Server Management Studio (SSMS) — журнал изменений](sql-server-management-studio-changelog-ssms.md)

*Обновлено: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 27.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 eb641ac39386a26a76dc303f5bd55eb3f9f4c78d f560f09b51ea30b255c10f7eb86857c3090881d9  (PR=5676  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**[SSMS 17.6]**


Номер выпуска: 17.6<br>
Номер сборки: 14.0.17230.0<br>
Дата выпуска: 20 марта 2018 г.

**Новые возможности**


**Общие ошибки SSMS**

Управляемый экземпляр базы данных SQL:

- Добавлена поддержка [Управляемого экземпляра базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance). Управляемый экземпляр базы данных SQL Azure (предварительная версия) — это новая разновидность базы данных SQL Azure, предоставляющая почти полную совместимость с локальным развертыванием SQL Server, собственную реализацию [виртуальной сети](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview), которая решает распространенные проблемы безопасности, и [бизнес-модель](https://azure.microsoft.com/pricing/details/sql-database/), подходящую клиентам локальных версий SQL Server.
- Поддержка распространенных сценариев управления, таких как:
   - создание и изменение баз данных;
   - резервное копирование и восстановление баз данных;
   - импорт, экспорт, извлечение и публикация приложений уровня данных;
   - просмотр и изменение свойств сервера;
   - полная поддержка обозревателя объектов;
   - создание скриптов для объектов базы данных;
   - поддержка заданий агента SQL;
   - поддержка связанных серверов.
- Дополнительные сведения об управляемых экземплярах можно найти [здесь](https://azure.microsoft.com/blog/migrate-your-databases-to-a-fully-managed-service-with-azure-sql-database-managed-instance/).

Обозреватель объектов:
- Добавлены параметры, отключающие принудительное заключение имен в скобки при перетаскивании из обозревателя объектов в окно запроса. (Предложения пользователей [32911933](https://feedback.azure.com/forums/908035-sql-server/suggestions/32911933) и [32671051](https://feedback.azure.com/forums/908035-sql-server/suggestions/32671051).)

Классификация данных:
- Общие усовершенствования и исправления ошибок.

**Integration Services (IS)**

- Добавлена поддержка развертывания пакетов в [Управляемом экземпляре базы данных SQL Azure](docs/ssms/https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-tutorials-for-sql-server-management-studio-ssmstutorialstutorial-sql-server-management-studiomd"></a>2. &nbsp; [Учебники по SQL Server Management Studio (SSMS)](tutorials/tutorial-sql-server-management-studio.md)

*Обновлено: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_1))

<!-- Source markdown line 49.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b272c75bab04912ebb706098cf6b6a6c80d9e2b8 d453ebc8251fb83ffcb1af58c9a08bb65b3e9fa2  (PR=5676  ,  Filename=tutorial-sql-server-management-studio.md  ,  Dirpath=docs\ssms\tutorials\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- Учебник. Подключение к SQL Server и выполнение запросов с помощью SSMS

    Из этого учебника вы узнаете, как подключиться к экземпляру SQL Server. Вы также ознакомитесь с некоторыми основными командами Transact-SQL (T-SQL) для создания базы данных и выполнения запросов к ней.

- Учебник. Создание скриптов для объектов в SSMS

    Из этого учебника вы узнаете, как создавать скрипты для различных объектов в среде SSMS, включая базы данных и запросы.

- Учебник. Использование шаблонов в SSMS

    Из этого учебника вы узнаете, как работать с готовыми шаблонами в среде SSMS. Шаблоны — это малоизвестный компонент, в котором хранится ряд фрагментов кода Transact-SQL для разных задач администрирования баз данных.

- Учебник. Настройка SSMS

    Из этого учебника вы узнаете основы настройки среды SSMS, например изменение структуры среды. В нем также описываются разные компоненты SSMS.


- Учебник: дополнительные советы и рекомендации по использованию SSMS

    Из этого учебника вы получите дополнительные советы и рекомендации по использованию среды SSMS. Учебник включает следующее:
    - закомментирование и раскомментирование текста;
    - добавление отступов в тексте;
    - фильтрация объектов в обозревателе объектов;
    - доступ к журналу ошибок SQL Server;
    - определение имени экземпляра.








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

