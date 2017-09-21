---
title: "Обновленные документы по SSMS для SQL Server | Документация Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по SQL Server Management Studio (SSMS) для Microsoft SQL Server."
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
ms.date: 09/11/2017
ms.author: genemi
ms.workload: ssms-sql-server-management-studio
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 917198902baf85f2bae57c9ade9f8d3e29dea357
ms.contentlocale: ru-ru
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Новые и недавно обновленные: SQL Server Management Studio (SSMS) для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат выхода обновлений:* &nbsp; **18.07.2017** &nbsp;—&nbsp; **11.09.2017**
- *Предметная область:* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Окно вывода в SQL Server Management Studio](output-window.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Скачивание SQL Server Management Studio (SSMS)](#TitleNum_1)
2. [Подключение к SQL Server или базе данных SQL Azure](#TitleNum_2)
3. [Среда SQL Server Management Studio (SSMS) — журнал изменений](#TitleNum_3)
4. [Создание и изменение таблиц баз данных](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-sql-server-management-studio-ssmsdownload-sql-server-management-studio-ssmsmd"></a>1. &nbsp; [Скачивание SQL Server Management Studio (SSMS)](download-sql-server-management-studio-ssms.md)

*Обновление: 07.08.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 63.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 23260f301f86651061b47065bee43d42c92a7be4 0c2178d96b621b96bfcd2fbb782f24792debb407  (PR=2775  ,  Filename=download-sql-server-management-studio-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=3f12671ace99d5fefc199c7b1c2db31e5b3cfade) -->



SSMS 17.2 — это последняя версия SQL Server Management Studio. Поколение 17.x среды SSMS поддерживает почти все функциональные возможности выпусков SQL Server 2008 — SQL Server 2017. Версия 17.x также поддерживает SQL Analysis Services в режиме PaaS.

Версия 17.2 включает в себя перечисленные ниже возможности.

- Многофакторная идентификация (MFA)
  - Проверка подлинности нескольких пользователей Azure AD с помощью универсальной проверки подлинности с Многофакторной идентификацией (MFA)
  - Было добавлено новое поле ввода учетных данных пользователей для поддержки проверки подлинности нескольких пользователей с помощью универсальной проверки подлинности с Многофакторной идентификацией.
- Диалоговое окно подключения теперь поддерживает следующие 5 способов проверки подлинности:
  - Проверка подлинности Windows.
  - Проверка подлинности SQL Server
  - Active Directory — универсальная с поддержкой MFA
  - Active Directory — пароль
  - Active Directory — встроенная

- При импорте и экспорте базы данных для мастера DacFx теперь можно использовать универсальную проверку подлинности с MFA.
- Сведения о поддержке API см. в описании [интерфейса IUniversalAuthProvider](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx).
- Управляемая библиотека ADAL, используемая для универсальной проверки подлинности Azure AD с MFA, обновлена до версии 3.13.9.
- Реализован новый интерфейс командной строки (CLI) с поддержкой параметров администрирования Azure AD для Базы данных SQL и хранилища данных SQL.

 Дополнительные сведения о способах проверки подлинности Active Directory см. в статьях [Универсальная проверка подлинности для Базы данных SQL и хранилища данных SQL (поддержка SSMS для MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) и [Настройка Многофакторной идентификации Базы данных SQL Azure для SQL Server Management Studio](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- В окне вывода приводятся записи, связанные с запросами, которые выполнялись во время развертывания узлов обозревателя объектов.
- Включен конструктор представлений для Баз данных SQL Azure.
- Изменились параметры скриптов для объектов в обозревателе объектов SQL Server Management Studio.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-connect-to-a-sql-server-or-azure-sql-databaseobjectconnect-to-an-instance-from-object-explorermd"></a>2. &nbsp; [Подключение к SQL Server или базе данных SQL Azure](object/connect-to-an-instance-from-object-explorer.md)

*Обновлено: 25.08.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_1) | [Далее](#TitleNum_3))

<!-- Source markdown line 40.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cfd72893c35c87df96dc8605807e542be28936e2 840981d3a115a15774a8e47ee2f6a0e5c4177b01  (PR=2961  ,  Filename=connect-to-an-instance-from-object-explorer.md  ,  Dirpath=docs\ssms\object\  ,  MergeCommitSha40=21f0cfd102a6fcc44dfc9151750f1b3c936aa053) -->



   ![брандмауэр--../media/connect-to-server/new-firewall-rule.png)

1. Чтобы создать правило брандмауэра и подключиться к серверу, нажмите кнопку **ОК**.

1. После подключения сервер появится в **Обозревателе объектов**.

   ![подключенный сервер--../media/connect-to-server/connected.png)

**Следующие шаги**


[Проектирование, создание и обновление таблиц--../visual-db-tools/design-tables-visual-database-tools.md)

**См. также:**


[SQL Server Management Studio (SSMS) (SSMS)--../sql-server-management-studio-ssms.md) [Скачивание SQL Server Management Studio (SSMS)--../download-sql-server-management-studio-ssms.md)

[Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/connect-to-analysis-services)
[Integration Services](https://docs.microsoft.com/sql/integration-services/sql-server-integration-services)
[Reporting Services](https://docs.microsoft.com/sql/reporting-services/tools/connect-to-a-report-server-in-management-studio)



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>3. &nbsp; [Среда SQL Server Management Studio (SSMS) — журнал изменений](sql-server-management-studio-changelog-ssms.md)

*Обновлено: 07.08.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_2) | [Далее](#TitleNum_4))

<!-- Source markdown line 20.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1733ce3c556db1e51cb27bf830429f2c42e8f97e 2abb24fd6547e438181039d095cbad027473a57e  (PR=2775  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=3f12671ace99d5fefc199c7b1c2db31e5b3cfade) -->



В этой статье приводятся подробные сведения об обновлениях, улучшениях и исправлениях ошибок в текущей и предыдущих версиях SQL Server Management Studio. [Предыдущие версии SQL Server Management Studio можно скачать ниже--#previous-ssms-releases).

**[SSMS 17.2--download-sql-server-management-studio-ssms.md)**


Общедоступная версия | Номер сборки: 14.0.17177.0

**Усовершенствования**


- Многофакторная идентификация (MFA)
  - Проверка подлинности нескольких пользователей Azure AD с помощью универсальной проверки подлинности с Многофакторной идентификацией (MFA)
  - Было добавлено новое поле ввода учетных данных пользователей для поддержки проверки подлинности нескольких пользователей с помощью универсальной проверки подлинности с Многофакторной идентификацией.
- Диалоговое окно подключения теперь поддерживает следующие 5 способов проверки подлинности:
  - Проверка подлинности Windows.
  - Проверка подлинности SQL Server
  - Active Directory — универсальная с поддержкой MFA
  - Active Directory — пароль
  - Active Directory — встроенная

- Импорт и экспорт базы данных для мастера DacFx с использованием универсальной проверки подлинности с MFA.
- Сведения о поддержке API см. в описании [интерфейса IUniversalAuthProvider](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx).
- Управляемая библиотека ADAL, используемая для универсальной проверки подлинности Azure AD с MFA, обновлена до версии 3.13.9.
- Кроме того, реализован новый интерфейс командной строки (CLI) с поддержкой параметров администрирования Azure AD для Базы данных SQL и хранилища данных SQL.

 Дополнительные сведения о способах проверки подлинности Active Directory см. в статьях [Универсальная проверка подлинности для Базы данных SQL и хранилища данных SQL (поддержка SSMS для MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) и [Настройка Многофакторной идентификации Базы данных SQL Azure для SQL Server Management Studio](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- В окне вывода приводятся записи, связанные с запросами, которые выполнялись во время развертывания узлов обозревателя объектов.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-create-and-update-database-tablesvisual-db-toolsdesign-tables-visual-database-toolsmd"></a>4. &nbsp; [Создание и изменение таблиц баз данных](visual-db-tools/design-tables-visual-database-tools.md)

*Обновлено: 25.08.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_3))

<!-- Source markdown line 30.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f63884ac2d04889e70c505cb5262c8dd81d73ee7 4b4c7aa5e8a0548405f02d11a66b722219fa78f0  (PR=2961  ,  Filename=design-tables-visual-database-tools.md  ,  Dirpath=docs\ssms\visual-db-tools\  ,  MergeCommitSha40=21f0cfd102a6fcc44dfc9151750f1b3c936aa053) -->



**Создание таблицы**


1. Щелкните правой кнопкой мыши узел **Таблицы** в базе данных и выберите **Создать** > **Таблица**.

    ![Новая таблица--../media/design-tables/new-table.png)

1. Добавление [столбцы--column-properties-visual-database-tools.md) в таблицу:

    ![проектирование таблицы--../media/design-tables/new-table2.png)

1. Закройте конструктор и сохраните изменения.

**Обновление таблицы**


1. Щелкните правой кнопкой мыши узел **Таблицы** в базе данных и выберите **Конструктор**.

   ![Обновление таблицы--../media/design-tables/update-table.png)

1. Измените необходимые параметры таблицы.

   ![--../media/design-tables/update-table2.png)

1. Закройте конструктор и сохраните изменения.

**См. также:**


[Таблицы](http://msdn.microsoft.com/82d7819c-b801-4309-a849-baa63083e83f) [Свойства таблиц &#40;Visual Database Tools&#41;--../../ssms/visual-db-tools/table-properties-visual-database-tools.md) [Свойства столбцов--column-properties-visual-database-tools.md) [Добавление столбцов в таблицу--../../relational-databases/tables/add-columns-to-a-table-database-engine.md) [Основной и внешний ключ--../../relational-databases/tables/primary-and-foreign-key-constraints.md) [Indexes--../../relational-databases/indexes/indexes.md) [Типы данных (Transact-SQL)--../../t-sql/data-types/data-types-transact-sql.md) [Скачивание SQL Server Management Studio (SSMS)--../download-sql-server-management-studio-ssms.md)







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



