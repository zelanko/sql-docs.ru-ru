---
title: "Обновлено. Документация по ядру СУБД | Документы Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по ядру СУБД."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: barbkess
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: database-engine
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/11/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: ce80496cdf82c2bc2df2447ed043216e6c78ad7e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-database-engine-docs"></a>Новые и недавно обновленные статьи: документация по ядру СУБД



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **18.07.2017**&nbsp;–&nbsp;**11.09.2017**
- *Предметная область:* &nbsp; **ядро СУБД**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Установка SQL Server](install-windows/installation-for-sql-server.md)
2. [Поддерживаемые обновления версий и выпусков SQL Server 2017](install-windows/supported-version-and-edition-upgrades-2017.md)
3. [Ядро СУБД SQL Server](sql-server-database-engine-overview.md)
4. [Новые возможности в ядре СУБД SQL Server 2016](whats-new-in-sql-server-2016.md)
5. [Новые возможности в ядре СУБД SQL Server 2017](whats-new-in-sql-server-2017.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Автоматическое заполнение для вторичных реплик](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-automatic-seeding-for-secondary-replicasavailability-groupswindowsautomatic-seeding-secondary-replicasmd"></a>1. &nbsp; [Автоматическое заполнение для вторичных реплик](availability-groups/windows/automatic-seeding-secondary-replicas.md)

*Обновлено: 21.08.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 55.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0b7b6a23f38bfe5959ccd170527a9bbdb308dc4b dc51fdf69649ed6cae03584cff7bc900d5b72149  (PR=2896  ,  Filename=automatic-seeding-secondary-replicas.md  ,  Dirpath=docs\database-engine\availability-groups\windows\  ,  MergeCommitSha40=80642503480add90fc75573338760ab86139694c) -->



В SQL Server 2016 и более ранних версиях папка, в которой будет создана база данных с помощью автоматического заполнения, уже должна существовать, и путь к ней должен совпадать с путем в первичной реплике.

В SQL Server 2017 корпорация Майкрософт рекомендует использовать одни и те же пути к данным и файлам журналов во всех репликах, входящих в группу доступности. Но при необходимости можно использовать разные пути. Например, в кроссплатформенной группе доступности один экземпляр SQL Server находится в Windows, а другой — в Linux. Пути на различных платформах будут разными. SQL Server 2017 поддерживает реплики группы доступности на экземплярах SQL Server с различными путями по умолчанию.

В следующей таблице представлены примеры разметки диска, которые поддерживают автоматическое заполнение.

|Основной экземпляр</br>Путь к данным по умолчанию|Вторичный экземпляр</br>Путь к данным по умолчанию|Основной экземпляр</br>Расположение исходного файла|Вторичный экземпляр</br> Расположение целевого файла
|:------|:------|:------|:------
|c:\\data\\ |/var/opt/mssql/data/ |c:\\data\\ |/var/opt/mssql/data/|
|c:\\data\\ |/var/opt/mssql/data/ |c:\\data\\group1\\ |/var/opt/mssql/data/group1/|
|c:\\data\\ |d:\\data\\ |c:\\data\\ |d:\\data\\
|c:\\data\\ |d:\\data\\ |c:\\data\\group1\\ |d:\\data\\group1\

Это изменение не влияет на сценарии, в которых расположение баз данных для первичной и вторичной реплики не совпадает с путями для экземпляров по умолчанию. При этом пути к файлам для вторичной реплики по-прежнему должны соответствовать путям к файлам для первичной реплики.

|Основной экземпляр</br>Путь к данным по умолчанию|Вторичный экземпляр</br>Путь к данным по умолчанию|Основной экземпляр</br>Размещение файла|Вторичный экземпляр</br> Размещение файла
|:------|:------|:------|:------
|c:\\data\\ |c:\\data\\ |d:\\group1\\ |d:\\group1\\
|c:\\data\\ |c:\\data\\ |d:\\data\\ |d:\\data\\
|c:\\data\\ |c:\\data\\ |d:\\data\\group1\\ |d:\\data\\group1\\

Если в первичной и вторичной репликах используются как пути по умолчанию, так и отличные от них пути, поведение SQL Server 2017 будет отличаться от поведения предыдущих выпусков. Поведение SQL Server 2017 описано в следующей таблице.







## <a name="similar-articles"></a>Похожие статьи

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Предметные области, содержащие новые или недавно обновленные статьи

- [Новые + обновленные (3+12):документация **Расширенная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (5+0): документация **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (5+1): документация **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (19+82): документация **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (1+8): документация **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (12+1): документация **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (0+1): документация **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (7+1): документация **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (1+1): документация **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (0+2): документация **Помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (1+4): документация **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (4+1): документация **Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Новые + обновленные (0+1): документация **Средства для SQL**](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Предметные области, не содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)



