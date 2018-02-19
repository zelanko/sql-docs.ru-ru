---
title: "Обновлено. Документация по ядру СУБД | Документы Майкрософт"
description: "Отображение фрагментов обновленного содержимого для последних изменений в документации по ядру СУБД."
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: database-engine
ms.date: 02/03/2018
ms.openlocfilehash: d01d9fa13342709a74d98033d093d9856ab5d680
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-database-engine-docs"></a>Новые и недавно обновленные статьи: документация по ядру СУБД



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Диапазон дат обновлений:* &nbsp; **03.12.2017**&nbsp;–&nbsp;**03.02.2018**
- *Предметная область:* &nbsp; **ядро СУБД**.




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

1. [Обновление экземпляров реплики группы доступности AlwaysOn](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-upgrading-always-on-availability-group-replica-instancesavailability-groupswindowsupgrading-always-on-availability-group-replica-instancesmd"></a>1. &nbsp; [Обновление экземпляров реплики группы доступности AlwaysOn](availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md)

*Обновлено: 29.01.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 174.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 20ca282e8965889a7a530fb67e125cc876410e41 9f27d0f9a74333b291c1cdc1529edc13960fae29  (PR=4741  ,  Filename=upgrading-always-on-availability-group-replica-instances.md  ,  Dirpath=docs\database-engine\availability-groups\windows\  ,  MergeCommitSha40=0a44ce9993ebf61f86e409255a1d58d47993951a) -->



**Особые действия для записи измененных данных или репликации**


В зависимости от применяемого обновления для баз данных реплики группы доступности, включенных для записи измененных данных или репликации, могут потребоваться дополнительные действия. См. заметки о выпуске для обновления, чтобы определить необходимость выполнения приведенных далее шагов.

1. Обновление каждой вторичной реплики.

1. Перенос группы доступности на обновленный экземпляр после обновления всех вторичных реплик.

1. Выполнение следующего запроса Transact-SQL на экземпляре, где размещена первичная реплика.

   ```
   EXECUTE [master].[sys].[sp_vupgrade_replication];
   ```

   >[!NOTE]
   >Выполнение этой команды может занять несколько минут.

1. Обновление экземпляра, который изначально был первичной репликой.

Дополнительные сведения см. в статье [CDC functionality may break after upgrading to the latest](http://blogs.msdn.microsoft.com/sql_server_team/cdc-functionality-may-break-after-upgrading-to-the-latest-cu-for-sql-server-2012-2014-and-2016/) (Возможное нарушение функциональности записи измененных данных после обновления до последнего накопительного обновления).









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


