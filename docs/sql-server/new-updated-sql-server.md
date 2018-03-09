---
title: "Обновленные документы по SQL Server | Документация Майкрософт"
description: "Отрывки из недавно обновленного содержимого в документации по SQL Server."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: sql-server
ms.date: 02/03/2018
ms.openlocfilehash: d819ecfc22e3a8e27fdfe7263b1d545298ca5055
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-sql-server-docs"></a>Новые и недавно обновленные документы для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **03.12.2017**&nbsp;–&nbsp;**03.02.2018**
- *Предметная область:* &nbsp; **SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Обновление экземпляров SQL Server, работающих в кластерах Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012](failover-clusters/windows/upgrade-sql-server-failover-cluster-instance-2008-2012.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Автономная справка SQL Server и окно справки](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-offline-help-and-help-viewersql-server-help-installationmd"></a>1. &nbsp; [Автономная справка SQL Server и окно справки](sql-server-help-installation.md)

*Обновлено: 19.12.2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 67.  ms.author= "craigg".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ea491fdc173a54fb4cdb3dfa2e26bd206d1cc45d 22444427a48064b76088d19d1ffae0a885bfe2a7  (PR=4338  ,  Filename=sql-server-help-installation.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=f2fde1c324466530f92006561a9a29decb711e1b) -->



   В окне справки откроется вкладка "Управление содержимым".

2. Чтобы установить последний пакет с содержимым справки, установите переключатель "Источник установки" в положение **Интернет**.

   ![HelpViewer2_ManageContent_OnlineSource](../sql-server/media/sql-server-help-installation/helpviewer2-managecontent-onlinesource.png)

   >[!NOTE]
   > Чтобы произвести установку с диска (справка SQL Server 2014), установите переключатель "Источник установки" в положение **Диск** и укажите расположение на диске.

   На вкладке "Управление содержимым" в поле "Путь к локальному хранилищу" отображается место установки содержимого на локальном компьютере. Чтобы изменить расположение, нажмите кнопку **Переместить**, в поле **Куда** введите путь к другой папке и нажмите кнопку **ОК**.
   Если после изменения пути к локальному хранилищу установить справку не удается, закройте и повторно откройте окно справки, проверьте, отображается ли новое расположение в поле "Путь к локальному хранилищу", а затем повторите попытку установки.

3. Щелкните ссылку **Добавить** рядом с каждым пакетом (книгой) содержимого, который нужно установить.
   Чтобы установить все содержимое справки SQL Server, добавьте все 13 книг в разделе SQL Server.

4. В правом нижнем углу нажмите кнопку **Обновить**.
   Новые пакеты автоматически появятся в содержании справки слева.

   ![HelpViewer2_ManageContent_AddContent](../sql-server/media/sql-server-help-installation/helpviewer2-managecontent-addcontent.png)

> [!NOTE]
> Не все заголовки верхнего уровня в содержании справки SQL Server в точности совпадают с названиями соответствующих скачиваемых пакетов справки. Заголовки в содержании сопоставляются с названиями пакетов следующим образом:

| Область содержания | Пакет справки SQL Server |
|-----|-----|
|Справочник по языку служб Analysis Services | Справочник по языку служб Analysis Services (MDX)|
|Справочник по выражениям анализа данных (DAX) | Справочник по выражениям анализа данных (DAX)|
|Справочник по расширениям интеллектуального анализа данных | Справочник по расширениям интеллектуального анализа данных|
|Руководства разработчиков по SQL Server | Справочник разработчика для SQL Server|
|Скачивание SQL Server Management Studio | Среда SQL Server Management Studio|







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи


- [Новые + обновленные (1+3):&nbsp; **Углубленная аналитика для SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (0+1):&nbsp; **Analytics Platform System для SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (0+1):&nbsp; **Подключение к SQL**](../connect/new-updated-connect.md)
- [Новые + обновленные (0+1):&nbsp; **Ядро СУБД для SQL**](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (12+1): **Integration Services для SQL**](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (6+2):&nbsp; **Linux для SQL**](../linux/new-updated-linux.md)
- [Новые + обновленные (15+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (2+9):&nbsp; **Реляционные базы данных для SQL**](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (1+0):&nbsp; **Reporting Services для SQL**](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (1+1):&nbsp; **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(1+1):&nbsp; **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (0+1):&nbsp; **SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (1+2):&nbsp; **SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2):&nbsp; **Transact-SQL**](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи


- [Новые + обновленные (0+0): **Data Migration Assistant (DMA) для SQL**](../dma/new-updated-dma.md)
- [Новые + обновленные (0+0): **объекты данных ActiveX (ADO) для SQL**](../ado/new-updated-ado.md)
- [Новые + обновленные (0+0): документация **Analysis Services для SQL**](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../sample/new-updated-sample.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **Инструменты для SQL**](../tools/new-updated-tools.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)


