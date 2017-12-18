---
title: "Наблюдение за репликацией программным образом | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- sp_replmonitorhelppublisher
- sp_replmonitorhelpmergesessiondetail
- monitoring performance [SQL Server replication], publication status
- sp_replmonitorhelpmergesession
- sp_replmonitorhelppublicationthresholds
- monitoring performance [SQL Server replication], subscription status
- monitoring performance [SQL Server replication], Transact-SQL programming
- sp_replmonitorsubscriptionpendingcmds
- sp_replmonitorchangepublicationthreshold
- transactional replication, monitoring
- sp_replmonitorhelppublication
- sp_replmonitorhelpsubscription
- monitoring performance [SQL Server replication], thresholds and warnings
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
ms.assetid: e8bf8850-8da5-4a4f-a399-64232b4e476d
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: caa7d7966fee784794884d7e840f0802c4a7774d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="programmatically-monitor-replication"></a>Наблюдение за репликацией программным образом
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Монитор репликации — это графическое средство, позволяющее осуществлять мониторинг топологии репликации. К данным мониторинга можно обращаться программным путем с помощью хранимых процедур репликации [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO. Эти объекты позволяют программировать следующие задачи:  
  
-   Наблюдение за состоянием издателей, публикаций и подписок.  
  
-   Мониторинг сеансов агентов слияния на одном или нескольких подписчиках.  
  
-   Мониторинг команд транзакций, ожидающих выполнения на одном или нескольких подписчиках.  
  
-   Установка пороговых показателей, определяющих, когда необходимо вмешательство в публикацию.  
  
-   Мониторинг состояния трассировочных токенов.  
  
 **В этом разделе:**  
  
 [Transact-SQL](#Tsql)  
  
 [объекты RMO;](#RMO)  
  
##  <a name="Tsql"></a> Transact-SQL  
  
#### <a name="to-monitor-publishers-publications-and-subscriptions-from-the-distributor"></a>Мониторинг издателей, публикаций и подписок с распространителя  
  
1.  В базе данных распространителя на распространителе выполните процедуру [sp_replmonitorhelppublisher](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublisher-transact-sql.md). Будут возвращены данные мониторинга всех издателей, использующих этот распространитель. Чтобы ограничить результирующий набор одним издателем, задайте параметр **@publisher**.  
  
2.  В базе данных распространителя на распространителе выполните процедуру [sp_replmonitorhelppublication](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublication-transact-sql.md). Будут возвращены данные мониторинга для всех публикаций, использующих этот распространитель. Чтобы ограничить результирующий набор одним издателем, одной публикацией или одной опубликованной базой данных, задайте, соответственно, параметр **@publisher**, **@publication**или **@publisher_db**.  
  
3.  В базе данных распространителя на распространителе выполните процедуру [sp_replmonitorhelpsubscription](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpsubscription-transact-sql.md). Будут возвращены данные мониторинга для всех подписок, использующих этот распространитель. Чтобы ограничить результирующий набор подписками, принадлежащими одному издателю, публикации или опубликованной базе данных, задайте, соответственно, параметр **@publisher**, **@publication**или **@publisher_db**.  
  
#### <a name="to-monitor-transactional-commands-waiting-to-be-applied-at-the-subscriber"></a>Мониторинг команд транзакций, ожидающих выполнения на подписчике  
  
1.  В базе данных распространителя на распространителе выполните процедуру [sp_replmonitorsubscriptionpendingcmds](../../../relational-databases/system-stored-procedures/sp-replmonitorsubscriptionpendingcmds-transact-sql.md). Будут возвращены данные мониторинга по всем ждущим командам для всех подписок, использующих этот распространитель. Чтобы ограничить результирующий набор ждущими командами для подписок, принадлежащих одному издателю, подписчику, публикации или опубликованной базе данных, укажите, соответственно, параметр **@publisher**, **@subscriber**, **@publication**или **@publisher_db**.  
  
#### <a name="to-monitor-merge-changes-waiting-to-be-uploaded-or-downloaded"></a>Мониторинг изменений слияния, ожидающих загрузки или выгрузки  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_showpendingchanges](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md). Это возвращает результирующий набор с информацией об изменениях, ожидающих репликации на серверы-подписчики. Чтобы ограничить результирующий набор изменениями, которые принадлежат одной публикации или статье, укажите параметр **@publication** или **@article**.  
  
2.  В базе данных подписки на подписчике выполните процедуру [sp_showpendingchanges](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md). Это возвращает результирующий набор с информацией об изменениях, ожидающих репликации на сервер-издатель. Чтобы ограничить результирующий набор изменениями, которые принадлежат одной публикации или статье, укажите параметр **@publication** или **@article**.  
  
#### <a name="to-monitor-merge-agent-sessions"></a>Мониторинг сеансов агента слияния  
  
1.  В базе данных распространителя на распространителе выполните процедуру [sp_replmonitorhelpmergesession](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md). Это возвращает данные мониторинга, включая **Session_id**, по всем сеансам агента слияния для всех подписок, использующих этот распространитель. Еще один способ получить **Session_id** — это запросить системную таблицу [MSmerge_sessions](../../../relational-databases/system-tables/msmerge-sessions-transact-sql.md) .  
  
2.  В базе данных распространителя на распространителе выполните процедуру [sp_replmonitorhelpmergesessiondetail](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md). В параметре **Session_id** укажите полученное на шаге 1 значение **@session_id**. Будут выданы подробные сведения о сеансе.  
  
3.  Повторите шаг 2 для всех интересующих сеансов.  
  
#### <a name="to-monitor-merge-agent-sessions-for-pull-subscriptions-from-the-subscriber"></a>Мониторинг сеансов агента слияния для подписок по запросу с подписчика  
  
1.  В базе данных подписки на подписчике выполните процедуру [sp_replmonitorhelpmergesession](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md). Для данной подписки укажите **@publisher**, **@publication**и имя базы данных публикации для **@publisher_db**. Будут возвращены сведения о последних пяти сеансах агента слияния для этой подписки. Запомните значение **Session_id** для сеансов, представляющих интерес в результирующем наборе.  
  
2.  В базе данных подписки на подписчике выполните процедуру [sp_replmonitorhelpmergesessiondetail](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md). В параметре **Session_id** укажите полученное на шаге 1 значение **@session_id**. Будут возвращены подробные данные мониторинга сеанса.  
  
3.  Повторите шаг 2 для всех интересующих сеансов.  
  
#### <a name="to-view-and-modify-the-monitor-threshold-metrics-for-a-publication"></a>Получение и изменение пороговых метрик мониторинга для публикации  
  
1.  В базе данных распространителя на распространителе выполните процедуру [sp_replmonitorhelppublicationthresholds](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublicationthresholds-transact-sql.md). Будут возвращены пороговые значения мониторинга для всех публикаций, использующих этот распространитель. Чтобы ограничить результирующий набор пороговыми значениями для публикаций, принадлежащих одному издателю, одной опубликованной базе данных или одной публикации, задайте, соответственно, параметр **@publisher**, **@publisher_db**или **@publication**. Запомните значение **Metric_id** для всех порогов, которые требуется изменить. Дополнительные сведения см. в статье [Set Thresholds and Warnings in Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
2.  В базе данных распространителя на распространителе выполните процедуру [sp_replmonitorchangepublicationthreshold](../../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md). Если требуется, укажите следующие значения.  
  
    -   Значение **Metric_id** , полученное в шаге 1, в параметре **@metric_id**.  
  
    -   Новое отслеживаемое значение пороговой метрики в параметре **@value**.  
  
    -   Значение **1** в параметре **@shouldalert** , чтобы при достижении порога записывалось в журнал предупреждение, или **0** , если предупреждение не требуется.  
  
    -   Значение **1** в параметре **@mode** , чтобы включить мониторинг пороговой метрики, или **2** , чтобы выключить его.  
  
##  <a name="RMO"></a> объекты RMO;  
  
#### <a name="to-monitor-a-subscription-to-a-merge-publication-at-the-subscriber"></a>Мониторинг подписки на публикацию слиянием на подписчике  
  
1.  Создайте соединение с подписчиком с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor> и задайте свойства <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publisher%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publication%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.PublisherDB%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.SubscriberDB%2A> для подписки, а затем задайте свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> для <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданного в шаге 1.  
  
3.  Чтобы получить сведения о сеансах агента слияния для данной подписки, вызовите один из следующих методов.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> — возвращает массив объектов <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> со сведениями о последних пяти сеансах агента слияния. Запомните значения <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> для всех необходимых сеансов.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> — возвращает массив объектов <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> со сведениями о сеансах агента слияния за количество часов, указанное в параметре *hours* (до пяти последних сеансов). Запомните значения <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> для всех необходимых сеансов.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummary%2A> — возвращает объект <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> с информацией о последнем сеансе агента слияния. Запомните значение <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> для этого сеанса.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummaryDataSet%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями о последних сеансах агента слияния (до пяти сеансов по одному в каждой строке). Запишите значение столбца **Session_id** для каждого сеанса, представляющего интерес.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummaryDataRow%2A> — возвращает объект <xref:System.Data.DataRow> с информацией о последнем сеансе агента слияния. Запишите значение столбца **Session_id** для каждого сеанса, представляющего интерес.  
  
4.  Вызовите <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> , чтобы обновить данные для объекта <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> , передаваемого в качестве параметра *mss,* или вызовите <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> , чтобы обновить данные для объекта <xref:System.Data.DataRow> , передаваемого в качестве параметра *drRefresh*.  
  
5.  С помощью идентификатора сеанса, полученного в шаге 3, вызовите один из следующих методов для получения сведений об отдельном сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetails%2A> — возвращает массив объектов <xref:Microsoft.SqlServer.Replication.MergeSessionDetail> для указанного *SessionId*.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetailsDataSet%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями для указанного *SessionId*.  
  
#### <a name="to-monitor-replication-properties-for-all-publications-at-a-distributor"></a>Мониторинг свойств репликации для всех публикаций на распространителе  
  
1.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> .  
  
3.  Укажите для свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения соединение <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданное в шаге 1.  
  
4.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> .  
  
5.  Выполните один или несколько следующих методов для получения сведений о репликации по всем издателям, использующим данный распространитель.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumDistributionAgents%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех агентах распространителя на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumErrorRecords%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об ошибках, которые хранятся на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumLogReaderAgents%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех агентах чтения журнала на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMergeAgents%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех агентах слияния на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMiscellaneousAgents%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех остальных агентах репликации на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех издателях на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers2%2A> — возвращает объект <xref:System.Data.DataSet> со списком издателей, использующих данный распространитель.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgents%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех агентах чтения очереди на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessionDetails%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об указанном агенте чтения очереди и сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessions%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями сеанса об указанном агенте чтения очереди.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumSnapshotAgents%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех агентах моментальных снимков на данном распространителе.  
  
#### <a name="to-monitor-publication-properties-for-a-specific-publisher-at-the-distributor"></a>Мониторинг свойств публикации для указанного издателя на распространителе  
  
1.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Получите объект <xref:Microsoft.SqlServer.Replication.PublisherMonitor> одним из следующих способов.  
  
    -   Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.PublisherMonitor> . Задайте для издателя свойство <xref:Microsoft.SqlServer.Replication.PublisherMonitor.Name%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> . Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает значение **false**, это означает, что было неправильно задано имя издателя или такой публикации не существует.  
  
    -   Из коллекции <xref:Microsoft.SqlServer.Replication.PublisherMonitorCollection> , доступ к которой был получен с помощью свойства <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.PublisherMonitors%2A> существующего объекта <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> .  
  
3.  Выполните один или несколько следующих методов, чтобы получить сведения о репликации по всем публикациям, принадлежащим данному издателю.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessionDetails%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об указанном агенте распространителя и сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessions%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об указанном агенте распространителя.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumErrorRecords%2A> — возвращает объект <xref:System.Data.DataSet> с информацией журнала ошибок об указанной ошибке.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessionDetails%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об указанном агенте чтения журнала и сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessions%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями сеанса по указанному агенту чтения журнала.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об указанном агенте слияния и сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails2%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об указанном агенте слияния и сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями сеанса об указанном агенте слияния.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions2%2A> — возвращает объект <xref:System.Data.DataSet> с дополнительными сведениями сеанса об указанном агенте слияния.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех публикациях на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications2%2A> — возвращает объект <xref:System.Data.DataSet> с дополнительными сведениями обо всех публикациях на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessionDetails%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об указанном агенте моментальных снимков и сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessions%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями сеанса об указанном агенте моментальных снимков.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSubscriptions%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех подписках на публикации на данном распространителе.  
  
#### <a name="to-monitor-properties-for-a-specific-publication-at-the-distributor"></a>Мониторинг свойств указанной публикации на распространителе  
  
1.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Получите объект <xref:Microsoft.SqlServer.Replication.PublicationMonitor> одним из следующих способов.  
  
    -   Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.PublicationMonitor> . Задайте для публикации свойства <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>и <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> . Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо свойства публикации были определены неверно, либо публикация не существует.  
  
    -   Из коллекции <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> , доступ к которой был получен с помощью свойства <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> существующего объекта <xref:Microsoft.SqlServer.Replication.PublisherMonitor> .  
  
3.  Выполните один или несколько следующих методов для получения сведений о данной публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumErrorRecords%2A> — возвращает объект <xref:System.Data.DataSet> с информацией журнала ошибок об указанной ошибке.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumLogReaderAgent%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об агенте чтения журнала для данной публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> — возвращает объект <xref:System.Data.DataSet> с информацией по мониторингу пороговых значений, заданных для этой публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumQueueReaderAgent%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об агенте чтения очереди, используемом данной публикацией.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSnapshotAgent%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями об агенте моментальных снимков для данной публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.Publication.EnumSubscriptions%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех подписках на эту публикацию.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSubscriptions2%2A> — возвращает объект <xref:System.Data.DataSet> с дополнительными сведениями обо всех подписках на данную публикацию в зависимости от параметра <xref:Microsoft.SqlServer.Replication.SubscriptionResultOption>.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> — возвращает объект <xref:System.Data.DataSet> с данными задержки для указанного трассировочного токена.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> — возвращает объект <xref:System.Data.DataSet> со сведениями обо всех трассировочных токенах, вставленных в данную публикацию.  
  
#### <a name="to-monitor-transactional-commands-that-are-waiting-to-be-applied-at-the-subscriber"></a>Мониторинг команд транзакций, ожидающих выполнения на подписчике  
  
1.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Получите объект <xref:Microsoft.SqlServer.Replication.PublicationMonitor> одним из следующих способов.  
  
    -   Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.PublicationMonitor> . Задайте для публикации свойства <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>и <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> . Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо свойства публикации были определены неверно, либо публикация не существует.  
  
    -   Из коллекции <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> , доступ к которой был получен с помощью свойства <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> существующего объекта <xref:Microsoft.SqlServer.Replication.PublisherMonitor> .  
  
3.  Выполните метод <xref:Microsoft.SqlServer.Replication.PublicationMonitor.TransPendingCommandInfo%2A> , который возвращает объект <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> .  
  
4.  Используйте свойства этого объекта <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> для определения примерного количества команд, ожидающих выполнения, и необходимого времени для завершения их доставки.  
  
#### <a name="to-set-the-monitor-warning-thresholds-for-a-publication"></a>Мониторинг пороговых значений предупреждений для публикации  
  
1.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Получите объект <xref:Microsoft.SqlServer.Replication.PublicationMonitor> одним из следующих способов.  
  
    -   Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.PublicationMonitor> . Задайте для публикации свойства <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>и <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> , а также установите созданное на шаге 1 соединение <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> в качестве значения для свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> . Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо свойства публикации были определены неверно, либо публикация не существует.  
  
    -   Из коллекции <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> , доступ к которой был получен с помощью свойства <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> существующего объекта <xref:Microsoft.SqlServer.Replication.PublisherMonitor> .  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> . Запомните текущие пороговые значения в возвращаемом списке <xref:System.Collections.ArrayList> объектов <xref:Microsoft.SqlServer.Replication.MonitorThreshold> .  
  
4.  Вызовите метод <xref:Microsoft.SqlServer.Replication.PublicationMonitor.ChangeMonitorThreshold%2A> . Передайте следующие параметры:  
  
    -   *metricID* — это значение <xref:System.Int32> , представляющее пороговую метрику из следующей таблицы.  
  
        |Значение|Описание|  
        |-----------|-----------------|  
        |1|**expiration** следит за приближающимся истечением срока подписки на публикации транзакций.|  
        |2|**latency** следит за производительностью подписки на публикации транзакций.|  
        |4|**mergeexpiration** следит за приближающимся истечением срока подписки на публикации слиянием.|  
        |5|**mergeslowrunduration** — следит за продолжительностью синхронизаций слиянием через соединения с низкой пропускной способностью (коммутируемые).|  
        |6|**mergefastrunduration** следит за длительностью синхронизации слиянием через соединения с высокой пропускной способностью (локальная сеть).|  
        |7|**mergefastrunspeed** — следит за частотой синхронизаций слиянием через соединения с высокой пропускной способностью (локальная сеть).|  
        |8|**mergeslowrunspeed** — следит за частотой синхронизаций слиянием через соединения с низкой пропускной способностью (коммутируемые).|  
  
    -   *enable* - <xref:System.Boolean> , которое указывает, включен ли этот показатель для данной публикации.  
  
    -   *thresholdValue* — целое значение, определяющее порог.  
  
    -   *shouldAlert* — целочисленное значение, которое указывает, должен ли порог вызывать предупреждение.  
  
  
