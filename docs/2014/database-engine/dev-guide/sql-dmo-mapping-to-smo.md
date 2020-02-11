---
title: Сопоставление SQL-DMO с объектами SMO | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 590f5396-98d5-485e-9b41-728c6ed7cb9d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a6273032f88807291bfc7024f1abcdbd1440073
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62780684"
---
# <a name="sql-dmo-mapping-to-smo"></a>Сопоставление SQL-DMO с SMO
  SQL распределенные управляющие объекты (SQL-DMO) больше не включается в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], приложения SQL-DMO должны быть преобразованы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использования управляющих объектов (SMO). Объектная модель SMO напоминает объектную модель SQL-DMO, поэтому большинство объектов SQL-DMO сопоставляются с одноименными объектами SMO. Однако некоторые объекты SQL-DMO при переходе на SMO изменены или удалены. В следующей таблице приведены рекомендованные действия по преобразованию SQL-DMO объектов, которые не переводятся на объекты SMO непосредственно.  
  
|Объект SQL-DMO|Действие в объекте SMO|  
|---------------------|-------------------|  
|Объект View2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект AlertSystem|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект Application|Удалено.|  
|Объекты Backup и Backup2|Объекты <xref:Microsoft.SqlServer.Management.Smo.Backup> и <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase>.|  
|Объект BackupDevice|<xref:Microsoft.SqlServer.Management.Smo.BackupDevice>объект|  
|Объекты BulkCopy и BulkCopy2|Удалено и заменено объектом <xref:Microsoft.SqlServer.Management.Smo.Transfer>.|  
|Объект Category|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>. Заменено объектами <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCategory>, <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCategory>, <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCategory>.|  
|Объект Check|<xref:Microsoft.SqlServer.Management.Smo.Check>объектами|  
|Объекты Column и Column2|<xref:Microsoft.SqlServer.Management.Smo.Column>объектами.|  
|Объект Configuration|Объекты <xref:Microsoft.SqlServer.Management.Smo.Configuration> и <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase>.|  
|Объект ConfigValue|<xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>объектами.|  
|Объекты Database и Database2|<xref:Microsoft.SqlServer.Management.Smo.Database>объектами.|  
|Объекты DatabaseRole и DatabaseRole2|<xref:Microsoft.SqlServer.Management.Smo.DatabaseRole>объектами.|  
|Объект DBFile|<xref:Microsoft.SqlServer.Management.Smo.DataFile>объектами.|  
|Объекты DBOption и DBOption2|Перемещено в объект <xref:Microsoft.SqlServer.Management.Smo.DatabaseOptions>.|  
|Объекты Default и Default2|<xref:Microsoft.SqlServer.Management.Smo.Default>объектами.|  
|Объекты DistributionArticle и DistributionArticle2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты DistributionDatabase и DistributionDatabase2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты DistributionPublication и DistributionPublication2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты DistributionSubscription и DistributionSubscription2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты Distributor и Distributor2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект DRIDefault|Перемещено в объект <xref:Microsoft.SqlServer.Management.Smo.ScriptingOptions>.|  
|Объекты FileGroup и FileGroup2|<xref:Microsoft.SqlServer.Management.Smo.FileGroup>объектами.|  
|Объекты FullTextCatalog и FullTextCatalog2|Объекты <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> и <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex>.|  
|Объекты Index и Index2|<xref:Microsoft.SqlServer.Management.Smo.Index>объектами|  
|Объект IntegratedSecurity|Функциональность перемещена в объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> в пространстве имен <xref:Microsoft.SqlServer.Management.Common>.|  
|Объект Job|<xref:Microsoft.SqlServer.Management.Smo.Agent.Job>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект JobFilter|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobFilter>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект JobHistoryFilter|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobHistoryFilter>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект JobSchedule|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объекты JobServer и JobServer2|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект JobStep|<xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект Key|Объекты <xref:Microsoft.SqlServer.Management.Smo.ForeignKey> и <xref:Microsoft.SqlServer.Management.Smo.Index>.|  
|Объекты LinkedServer и LinkedServer2|<xref:Microsoft.SqlServer.Management.Smo.LinkedServer>объектами.|  
|Объект LinkedServerLogin|<xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>объектами.|  
|Объект LogFile|<xref:Microsoft.SqlServer.Management.Smo.LogFile>объектами.|  
|Объекты Login и Login2|<xref:Microsoft.SqlServer.Management.Smo.Login>объектами.|  
|Объекты MergeArticle и MergeArticle2|<xref:Microsoft.SqlServer.Replication.MergeArticle>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект MergeDynamicSnapshotJob|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты MergePublication и MergePublication2|<xref:Microsoft.SqlServer.Replication.MergePublication>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты MergePullSubscription и MergePullSubscription2|<xref:Microsoft.SqlServer.Replication.MergePullSubscription>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект MergeSubscription|<xref:Microsoft.SqlServer.Replication.MergeSubscription>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект MergeSubsetFilter|Перемещено в пространство имен `N:Microsoft.SqlServer.Replication`.|  
|Объект NameList|Удалено. Альтернативная функциональность в объекте <xref:Microsoft.SqlServer.Management.Smo.Scripter>.|  
|Объект Operator|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объекты Permission и Permission2|Объекты <xref:Microsoft.SqlServer.Management.Smo.ServerPermission>, <xref:Microsoft.SqlServer.Management.Smo.DatabasePermission>, <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> и <xref:Microsoft.SqlServer.Management.Smo.ObjectPermission>.|  
|Объект Property|`Property`объектами.|  
|Объекты Publisher и Publisher2|<xref:Microsoft.SqlServer.Replication.ReplicationServer>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты QueryResults и QueryResults2|Заменены системными объектами <xref:System.Data.DataTable> или <xref:System.Data.DataSet>.|  
|Объект RegisteredServer|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект RegisteredSubscriber|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты Registry и Registry2|Удалено.|  
|Объект RemoteLogin|<xref:Microsoft.SqlServer.Management.Common.ServerConnection>объектами. Перемещено в общее пространство имен.|  
|Объекты RemoteServer и RemoteServer2|<xref:Microsoft.SqlServer.Management.Common.ServerConnection>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Common>.|  
|Объект Replication|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты ReplicationDatabase и ReplicationDatabase2|<xref:Microsoft.SqlServer.Replication.ReplicationDatabase>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект ReplicationSecurity|<xref:Microsoft.SqlServer.Management.Common.ServerConnection>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Common>.|  
|Объекты ReplicationStoredProcedure и ReplicationStoredProcedure2|<xref:Microsoft.SqlServer.Replication.ReplicationStoredProcedure>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты ReplicationTable и ReplicationTable2|<xref:Microsoft.SqlServer.Replication.ReplicationTable>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты Restore и Restore2|Объекты <xref:Microsoft.SqlServer.Management.Smo.Restore> и <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase>.|  
|Объекты Rule и Rule2|<xref:Microsoft.SqlServer.Management.Smo.Rule>объектами|  
|Объект Schedule|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект ServerGroup|Удалено.|  
|Объект ServerRole|<xref:Microsoft.SqlServer.Management.Smo.ServerRole>объектами.|  
|Объект SQLObjectList|<xref:Microsoft.SqlServer.Management.Smo.SqlSmoObject>inArray.|  
|Объекты SQLServer и SQLServer2|<xref:Microsoft.SqlServer.Management.Smo.Server>объектами.|  
|Объекты StoredProcedure и StoredProcedure2|<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>объекты <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> и|  
|Объекты Subscriber и Subscriber2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты SystemDatatype и SystemDataType2|<xref:Microsoft.SqlServer.Management.Smo.DataType>объектами.|  
|Объекты Table и Table2|<xref:Microsoft.SqlServer.Management.Smo.Table>объектами.|  
|Объект TargetServer|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект TargetServerGroup|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект TransactionLog|Функциональность перемещена в объект <xref:Microsoft.SqlServer.Management.Smo.Database>.|  
|Объекты TransArticle и TransArticle2|<xref:Microsoft.SqlServer.Replication.TransArticle>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Метод Transfer и объект Transfer2|<xref:Microsoft.SqlServer.Management.Smo.Transfer>объектами.|  
|Объекты TransPublication и TransPublication2|<xref:Microsoft.SqlServer.Replication.TransPublication>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты TransPullSubscription и TransPullSubscription2|<xref:Microsoft.SqlServer.Replication.TransPullSubscription>объектами. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты Trigger и Trigger2|<xref:Microsoft.SqlServer.Management.Smo.Trigger>объектами.|  
|Объекты User и User2|<xref:Microsoft.SqlServer.Management.Smo.User>объектами.|  
|Объекты UserDefinedDatatype и UserDefinedDataType2|<xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>объектами.|  
|Объект UserDefinedFunction|Объекты <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> и <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>.|  
|Объекты View и View2|<xref:Microsoft.SqlServer.Management.Smo.View>объектами.|  
  
## <a name="see-also"></a>См. также:  
 [Управляющие объекты SQL Server &#40;инструкции по программированию SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
