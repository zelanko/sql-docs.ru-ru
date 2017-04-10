---
title: "Наблюдение за репликацией программным образом | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_replmonitorhelppublisher, хранимая процедура"
  - "sp_replmonitorhelpmergesessiondetail"
  - "мониторинг производительности [репликация SQL Server], состояние публикации"
  - "sp_replmonitorhelpmergesession"
  - "sp_replmonitorhelppublicationthresholds, хранимая процедура"
  - "мониторинг производительности [репликация SQL Server], состояние подписки"
  - "мониторинг производительности [репликация SQL Server], программирование на языке Transact-SQL"
  - "sp_replmonitorsubscriptionpendingcmds"
  - "sp_replmonitorchangepublicationthreshold"
  - "репликация транзакций, мониторинг"
  - "sp_replmonitorhelppublication"
  - "sp_replmonitorhelpsubscription"
  - "мониторинг производительности [репликация SQL Server], пороги и предупреждения"
  - "наблюдение за репликацией слиянием [репликация SQL Server]"
  - "репликация моментального снимка [SQL Server], мониторинг"
ms.assetid: e8bf8850-8da5-4a4f-a399-64232b4e476d
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Наблюдение за репликацией программным образом
  Монитор репликации — это графическое средство, позволяющее осуществлять мониторинг топологии репликации. К данным мониторинга можно обращаться программным путем с помощью хранимых процедур репликации [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO. Эти объекты позволяют программировать следующие задачи:  
  
-   Наблюдение за состоянием издателей, публикаций и подписок.  
  
-   Мониторинг сеансов агентов слияния на одном или нескольких подписчиках.  
  
-   Мониторинг команд транзакций, ожидающих выполнения на одном или нескольких подписчиках.  
  
-   Установка пороговых показателей, определяющих, когда необходимо вмешательство в публикацию.  
  
-   Мониторинг состояния трассировочных токенов.  
  
 **В этом разделе:**  
  
 [Transact-SQL](#Tsql)  
  
 [объекты RMO;](#RMO)  
  
##  <a name="Tsql"></a> Transact-SQL  
  
#### Мониторинг издателей, публикаций и подписок с распространителя  
  
1.  На распространителе в базе данных распространителя, выполните [sp_replmonitorhelppublisher](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublisher-transact-sql.md). Будут возвращены данные мониторинга всех издателей, использующих этот распространитель. Чтобы ограничить результирующий набор одним издателем, задайте параметр **@publisher**.  
  
2.  На распространителе в базе данных распространителя, выполните [sp_replmonitorhelppublication](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublication-transact-sql.md). Будут возвращены данные мониторинга для всех публикаций, использующих этот распространитель. Чтобы ограничить результирующий набор для одного издателя, публикации или опубликованной базы данных, укажите **@publisher**, **@publication**, или **@publisher_db**, соответственно.  
  
3.  На распространителе в базе данных распространителя, выполните [sp_replmonitorhelpsubscription](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpsubscription-transact-sql.md). Будут возвращены данные мониторинга для всех подписок, использующих этот распространитель. Чтобы ограничить результирующий набор для подписок, принадлежащих одному издателю, публикации или опубликованной базы данных, укажите **@publisher**, **@publication**, или **@publisher_db**, соответственно.  
  
#### Мониторинг команд транзакций, ожидающих выполнения на подписчике  
  
1.  На распространителе в базе данных распространителя, выполните [sp_replmonitorsubscriptionpendingcmds](../../../relational-databases/system-stored-procedures/sp-replmonitorsubscriptionpendingcmds-transact-sql.md). Будут возвращены данные мониторинга по всем ждущим командам для всех подписок, использующих этот распространитель. Чтобы ограничить результирующий набор команд, ожидающих для подписок, принадлежащих одному издателю, подписчику, публикации или опубликованной базы данных, укажите **@publisher**, **@subscriber**, **@publication**, или **@publisher_db**, соответственно.  
  
#### Мониторинг изменений слияния, ожидающих загрузки или выгрузки  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_showpendingchanges](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md). Это возвращает результирующий набор с информацией об изменениях, ожидающих репликации на серверы-подписчики. Чтобы ограничить результирующий набор изменениями, которые принадлежат одной публикации или статье, укажите параметр **@publication** или **@article**соответственно.  
  
2.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_showpendingchanges](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md). Это возвращает результирующий набор с информацией об изменениях, ожидающих репликации на сервер-издатель. Чтобы ограничить результирующий набор изменениями, которые принадлежат одной публикации или статье, укажите параметр **@publication** или **@article**соответственно.  
  
#### Мониторинг сеансов агента слияния  
  
1.  На распространителе в базе данных распространителя, выполните [sp_replmonitorhelpmergesession](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md). Будут возвращены данные мониторинга, включая **Session_id**, о всех сеансах агента слияния для всех подписок, использующих этот распространитель. Можно также получить **Session_id** с помощью запроса [MSmerge_sessions](../../../relational-databases/system-tables/msmerge-sessions-transact-sql.md) системной таблицы.  
  
2.  На распространителе в базе данных распространителя, выполните [sp_replmonitorhelpmergesessiondetail](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md). Укажите **Session_id** значение из шага 1 для **@session_id**. Будут выданы подробные сведения о сеансе.  
  
3.  Повторите шаг 2 для всех интересующих сеансов.  
  
#### Мониторинг сеансов агента слияния для подписок по запросу с подписчика  
  
1.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_replmonitorhelpmergesession](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md). Для данной подписки, укажите **@publisher**, **@publication**, и имя базы данных публикации для **@publisher_db**. Будут возвращены сведения о последних пяти сеансах агента слияния для этой подписки. Обратите внимание на значение **Session_id** сеансы интерес в результирующий набор.  
  
2.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_replmonitorhelpmergesessiondetail](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md). Укажите **Session_id** значение из шага 1 для **@session_id**. Будут возвращены подробные данные мониторинга сеанса.  
  
3.  Повторите шаг 2 для всех интересующих сеансов.  
  
#### Получение и изменение пороговых метрик мониторинга для публикации  
  
1.  На распространителе в базе данных распространителя, выполните [sp_replmonitorhelppublicationthresholds](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublicationthresholds-transact-sql.md). Будут возвращены пороговые значения мониторинга для всех публикаций, использующих этот распространитель. Чтобы ограничить результирующий набор пороговыми значениями для публикаций, принадлежащих одному издателю или опубликованной базе данных или одной публикации, укажите **@publisher**, **@publisher_db**, или **@publication**, соответственно. Обратите внимание на значение **Metric_id** для всех порогов, которые должны быть изменены. Дополнительные сведения см. в статье [Set Thresholds and Warnings in Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
2.  На распространителе в базе данных распространителя, выполните [sp_replmonitorchangepublicationthreshold](../../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md). Если требуется, укажите следующие значения.  
  
    -    **Metric_id** значением, полученным на шаге 1 для **@metric_id**.  
  
    -   Новое отслеживаемое значение пороговой метрики в параметре **@value**.  
  
    -   Значение **1** в параметре **@shouldalert** , чтобы при достижении порога записывалось в журнал предупреждение, или **0** , если предупреждение не требуется.  
  
    -   Значение **1** в параметре **@mode** , чтобы включить мониторинг пороговой метрики, или **2** , чтобы выключить его.  
  
##  <a name="RMO"></a> объекты RMO;  
  
#### Мониторинг подписки на публикацию слиянием на подписчике  
  
1.  Создайте соединение с подписчиком с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor> и задать <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publisher%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publication%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.PublisherDB%2A>, <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.SubscriberDB%2A> Свойства для подписки, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> созданной на шаге 1.  
  
3.  Чтобы получить сведения о сеансах агента слияния для данной подписки, вызовите один из следующих методов.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> — Возвращает массив <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> объектов с информацией на до последних пяти сеансах агента слияния. Примечание <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> значение для всех необходимых сеансов.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> — Возвращает массив <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> объектов с информацией о сеансах агента слияния, возникших во время за количество часов, переданный в качестве *часов* параметра (до пяти последних сеансов). Примечание <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> значение для всех необходимых сеансов.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummary%2A> -возвращает <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> с информацией о последнем сеансе агента слияния. Примечание <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> значение для этого сеанса.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummaryDataSet%2A> -возвращает <xref:System.Data.DataSet> объекта с информацией на до последних пяти сеансах агента слияния, одному в каждой строке. Обратите внимание на значение **Session_id** столбца для всех необходимых сеансов.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummaryDataRow%2A> -возвращает <xref:System.Data.DataRow> с информацией о последнем сеансе агента слияния. Обратите внимание на значение **Session_id** столбец для этого сеанса.  
  
4.  (Необязательно) Вызов <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> обновление данных для <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> объект, передаваемый как *mss,* или вызвать <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> для обновления данных в <xref:System.Data.DataRow> объект, передаваемый как *drRefresh*.  
  
5.  С помощью идентификатора сеанса, полученного в шаге 3, вызовите один из следующих методов для получения сведений об отдельном сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetails%2A> -возвращает массив <xref:Microsoft.SqlServer.Replication.MergeSessionDetail> объектов для предоставленной *SessionId*.  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetailsDataSet%2A> -возвращает <xref:System.Data.DataSet> объект со сведениями для указанного *SessionId*.  
  
#### Мониторинг свойств репликации для всех публикаций на распространителе  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> созданной на шаге 1.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта.  
  
5.  Выполните один или несколько следующих методов для получения сведений о репликации по всем издателям, использующим данный распространитель.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumDistributionAgents%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения обо всех агентах распространителя на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumErrorRecords%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения об ошибках, которые хранятся на распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumLogReaderAgents%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения обо всех агентах чтения журнала на распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMergeAgents%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения обо всех агентах слияния на распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMiscellaneousAgents%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения обо всех агентах репликации на распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения обо всех издателях на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers2%2A> -возвращает <xref:System.Data.DataSet> объекта, который возвращает издателей, использующих этот распространитель.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgents%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения обо всех агентах чтения очереди на распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessionDetails%2A> -возвращает <xref:System.Data.DataSet> объекта со сведениями об указанном агента чтения очереди и сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessions%2A> -возвращает <xref:System.Data.DataSet> объекта со сведениями сеанса об указанном агенте чтения очереди.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumSnapshotAgents%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения обо всех агентах моментальных снимков на распространителе.  
  
#### Мониторинг свойств публикации для указанного издателя на распространителе  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Получить <xref:Microsoft.SqlServer.Replication.PublisherMonitor> объекта в одном из следующих способов.  
  
    -   Создайте экземпляр <xref:Microsoft.SqlServer.Replication.PublisherMonitor> класса. Задайте <xref:Microsoft.SqlServer.Replication.PublisherMonitor.Name%2A> свойство для издателя, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> созданной на шаге 1. Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает значение **false**, это означает, что было неправильно задано имя издателя или такой публикации не существует.  
  
    -   От <xref:Microsoft.SqlServer.Replication.PublisherMonitorCollection> доступ с помощью параметра <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.PublisherMonitors%2A> свойства существующего <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> объекта.  
  
3.  Выполните один или несколько следующих методов, чтобы получить сведения о репликации по всем публикациям, принадлежащим данному издателю.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessionDetails%2A> -возвращает <xref:System.Data.DataSet> объекта со сведениями об указанном агенте распространителя и сеанса.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessions%2A> -возвращает <xref:System.Data.DataSet> объекта со сведениями сеанса об указанном агенте распространителя.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumErrorRecords%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения о записи ошибок об указанной ошибке.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessionDetails%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения для указанного агента чтения журнала и сеанса.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessions%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения о сеансе для указанного агента чтения журнала.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails%2A> -возвращает <xref:System.Data.DataSet> объекта со сведениями об указанном агенте слияния и сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails2%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий дополнительные сведения об указанном агенте слияния и сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения о сеансе для указанного агента слияния.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions2%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий дополнительные сведения о сессии для указанного агента слияния.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения обо всех публикациях на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications2%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий дополнительные сведения обо всех публикациях на данном распространителе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessionDetails%2A> -возвращает <xref:System.Data.DataSet> объекта со сведениями об указанном агента моментальных снимков и сеансе.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessions%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения о сеансе для указанного агента моментальных снимков.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSubscriptions%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения обо всех подписках на публикации на данном распространителе.  
  
#### Мониторинг свойств указанной публикации на распространителе  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Получить <xref:Microsoft.SqlServer.Replication.PublicationMonitor> объекта в одном из следующих способов.  
  
    -   Создайте экземпляр <xref:Microsoft.SqlServer.Replication.PublicationMonitor> класса. Задайте <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, и <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> созданной на шаге 1. Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо свойства публикации были определены неверно, либо публикация не существует.  
  
    -   От <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> доступ с помощью параметра <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> свойства существующего <xref:Microsoft.SqlServer.Replication.PublisherMonitor> объекта.  
  
3.  Выполните один или несколько следующих методов для получения сведений о данной публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumErrorRecords%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий записи ошибок об указанной ошибке.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumLogReaderAgent%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения об агенте чтения журнала для этой публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения о пороговых значениях предупреждений монитора, заданных для этой публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumQueueReaderAgent%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения об агенте чтения очереди, используемый этой публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSnapshotAgent%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения об агенте моментальных снимков для данной публикации.  
  
    -   <xref:Microsoft.SqlServer.Replication.Publication.EnumSubscriptions%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения о подписках на эту публикацию.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSubscriptions2%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий дополнительные сведения о подписках на эту публикацию на основе предоставленного <xref:Microsoft.SqlServer.Replication.SubscriptionResultOption>.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения о задержке для указанных трассировочных маркера.  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> -возвращает <xref:System.Data.DataSet> объект, содержащий сведения обо всех трассировочных токенах, вставленных в данную публикацию.  
  
#### Мониторинг команд транзакций, ожидающих выполнения на подписчике  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Получить <xref:Microsoft.SqlServer.Replication.PublicationMonitor> объекта в одном из следующих способов.  
  
    -   Создайте экземпляр <xref:Microsoft.SqlServer.Replication.PublicationMonitor> класса. Задайте <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, и <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> созданной на шаге 1. Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо свойства публикации были определены неверно, либо публикация не существует.  
  
    -   От <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> доступ с помощью параметра <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> свойства существующего <xref:Microsoft.SqlServer.Replication.PublisherMonitor> объекта.  
  
3.  Выполнение <xref:Microsoft.SqlServer.Replication.PublicationMonitor.TransPendingCommandInfo%2A> метод, возвращающий <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> объекта.  
  
4.  Используйте свойства этого <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> для определения предполагаемое количество ожидающих команд и время, необходимое для завершения доставки этих команд.  
  
#### Мониторинг пороговых значений предупреждений для публикации  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Получить <xref:Microsoft.SqlServer.Replication.PublicationMonitor> объекта в одном из следующих способов.  
  
    -   Создайте экземпляр <xref:Microsoft.SqlServer.Replication.PublicationMonitor> класса. Задайте <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, и <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> созданной на шаге 1. Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо свойства публикации были определены неверно, либо публикация не существует.  
  
    -   От <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> доступ с помощью параметра <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> свойства существующего <xref:Microsoft.SqlServer.Replication.PublisherMonitor> объекта.  
  
3.  Выполнение <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> метод. Обратите внимание, текущие пороговые значения в возвращаемом <xref:System.Collections.ArrayList> из <xref:Microsoft.SqlServer.Replication.MonitorThreshold> объектов.  
  
4.  Выполнение <xref:Microsoft.SqlServer.Replication.PublicationMonitor.ChangeMonitorThreshold%2A> метод. Передайте следующие параметры:  
  
    -   *metricID* - <xref:System.Int32> значение, представляющее пороговую метрику из следующей таблицы:  
  
        |Значение|Описание|  
        |-----------|-----------------|  
        |1|**истечение срока действия** -следит за приближающимся истечением срока подписки на публикации транзакций.|  
        |2|**Задержка** -следит за производительностью подписки на публикации транзакций.|  
        |4|**mergeexpiration** -следит за приближающимся истечением срока подписки на публикации слиянием.|  
        |5|**mergeslowrunduration** -следит за продолжительностью синхронизаций слиянием через соединения с низкой пропускной способностью (коммутируемые).|  
        |6|**mergefastrunduration** -следит за продолжительностью синхронизаций слиянием через соединения с высокой пропускной способностью (локальная сеть).|  
        |7|**mergefastrunspeed** -следит за частотой синхронизации слиянием через соединения с высокой пропускной способностью (локальная сеть).|  
        |8|**mergeslowrunspeed** -следит за частотой синхронизации слиянием через соединения с низкой пропускной способностью (коммутируемые).|  
  
    -   *включить* - <xref:System.Boolean> значение, указывающее, включена ли Метрика для публикации.  
  
    -   *thresholdValue* — целое число, задающее пороговое значение.  
  
    -   *shouldAlert* — целое число, указывающее, следует ли создавать оповещение, это пороговое значение.  
  
  