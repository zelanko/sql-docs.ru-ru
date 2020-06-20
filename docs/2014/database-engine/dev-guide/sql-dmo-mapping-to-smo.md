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
ms.openlocfilehash: 147c75384fa65a103c3d17c731add99ecec79b63
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933375"
---
# <a name="sql-dmo-mapping-to-smo"></a>Сопоставление SQL-DMO с SMO
  SQL распределенные управляющие объекты (SQL-DMO) больше не включается в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , приложения SQL-DMO должны быть преобразованы для использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] управляющих объектов (SMO). Объектная модель SMO напоминает объектную модель SQL-DMO, поэтому большинство объектов SQL-DMO сопоставляются с одноименными объектами SMO. Однако некоторые объекты SQL-DMO при переходе на SMO изменены или удалены. В следующей таблице приведены рекомендованные действия по преобразованию SQL-DMO объектов, которые не переводятся на объекты SMO непосредственно.  
  
|Объект SQL-DMO|Действие в объекте SMO|  
|---------------------|-------------------|  
|Объект View2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект AlertSystem|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект Application|Удаляются.|  
|Объекты Backup и Backup2|Объекты <xref:Microsoft.SqlServer.Management.Smo.Backup> и <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase>.|  
|Объект BackupDevice|Объекты <xref:Microsoft.SqlServer.Management.Smo.BackupDevice>|  
|Объекты BulkCopy и BulkCopy2|Удалено и заменено объектом <xref:Microsoft.SqlServer.Management.Smo.Transfer>.|  
|Объект Category|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>. Заменено объектами <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCategory>, <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCategory>, <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCategory>.|  
|Объект Check|Объект <xref:Microsoft.SqlServer.Management.Smo.Check>.|  
|Объекты Column и Column2|Объект <xref:Microsoft.SqlServer.Management.Smo.Column>.|  
|Объект Configuration|Объекты <xref:Microsoft.SqlServer.Management.Smo.Configuration> и <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase>.|  
|Объект ConfigValue|Объект <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>.|  
|Объекты Database и Database2|Объект <xref:Microsoft.SqlServer.Management.Smo.Database>.|  
|Объекты DatabaseRole и DatabaseRole2|Объект <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole>.|  
|Объект DBFile|Объект <xref:Microsoft.SqlServer.Management.Smo.DataFile>.|  
|Объекты DBOption и DBOption2|Перемещено в объект <xref:Microsoft.SqlServer.Management.Smo.DatabaseOptions>.|  
|Объекты Default и Default2|Объект <xref:Microsoft.SqlServer.Management.Smo.Default>.|  
|Объекты DistributionArticle и DistributionArticle2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты DistributionDatabase и DistributionDatabase2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты DistributionPublication и DistributionPublication2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты DistributionSubscription и DistributionSubscription2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты Distributor и Distributor2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект DRIDefault|Перемещено в объект <xref:Microsoft.SqlServer.Management.Smo.ScriptingOptions>.|  
|Объекты FileGroup и FileGroup2|Объект <xref:Microsoft.SqlServer.Management.Smo.FileGroup>.|  
|Объекты FullTextCatalog и FullTextCatalog2|Объекты <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> и <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex>.|  
|Объекты Index и Index2|Объект <xref:Microsoft.SqlServer.Management.Smo.Index>.|  
|Объект IntegratedSecurity|Функциональность перемещена в объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> в пространстве имен <xref:Microsoft.SqlServer.Management.Common>.|  
|Объект Job|Объект <xref:Microsoft.SqlServer.Management.Smo.Agent.Job>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект JobFilter|Объект <xref:Microsoft.SqlServer.Management.Smo.Agent.JobFilter>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект JobHistoryFilter|Объект <xref:Microsoft.SqlServer.Management.Smo.Agent.JobHistoryFilter>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект JobSchedule|Объект <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объекты JobServer и JobServer2|Объект <xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект JobStep|Объект <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект Key|Объекты <xref:Microsoft.SqlServer.Management.Smo.ForeignKey> и <xref:Microsoft.SqlServer.Management.Smo.Index>.|  
|Объекты LinkedServer и LinkedServer2|Объект <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>.|  
|Объект LinkedServerLogin|Объект <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>.|  
|Объект LogFile|Объект <xref:Microsoft.SqlServer.Management.Smo.LogFile>.|  
|Объекты Login и Login2|Объект <xref:Microsoft.SqlServer.Management.Smo.Login>.|  
|Объекты MergeArticle и MergeArticle2|Объект <xref:Microsoft.SqlServer.Replication.MergeArticle>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект MergeDynamicSnapshotJob|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты MergePublication и MergePublication2|Объект <xref:Microsoft.SqlServer.Replication.MergePublication>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты MergePullSubscription и MergePullSubscription2|Объект <xref:Microsoft.SqlServer.Replication.MergePullSubscription>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект MergeSubscription|Объект <xref:Microsoft.SqlServer.Replication.MergeSubscription>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект MergeSubsetFilter|Перемещено в пространство имен `N:Microsoft.SqlServer.Replication`.|  
|Объект NameList|Удаляются. Альтернативная функциональность в объекте <xref:Microsoft.SqlServer.Management.Smo.Scripter>.|  
|Объект Operator|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объекты Permission и Permission2|Объекты <xref:Microsoft.SqlServer.Management.Smo.ServerPermission>, <xref:Microsoft.SqlServer.Management.Smo.DatabasePermission>, <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> и <xref:Microsoft.SqlServer.Management.Smo.ObjectPermission>.|  
|Объект Property|Объект `Property`.|  
|Объекты Publisher и Publisher2|Объект <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты QueryResults и QueryResults2|Заменены системными объектами <xref:System.Data.DataTable> или <xref:System.Data.DataSet>.|  
|Объект RegisteredServer|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект RegisteredSubscriber|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты Registry и Registry2|Удаляются.|  
|Объект RemoteLogin|Объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Перемещено в общее пространство имен.|  
|Объекты RemoteServer и RemoteServer2|Объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Common>.|  
|Объект Replication|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты ReplicationDatabase и ReplicationDatabase2|Объект <xref:Microsoft.SqlServer.Replication.ReplicationDatabase>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект ReplicationSecurity|Объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Common>.|  
|Объекты ReplicationStoredProcedure и ReplicationStoredProcedure2|Объект <xref:Microsoft.SqlServer.Replication.ReplicationStoredProcedure>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты ReplicationTable и ReplicationTable2|Объект <xref:Microsoft.SqlServer.Replication.ReplicationTable>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты Restore и Restore2|Объекты <xref:Microsoft.SqlServer.Management.Smo.Restore> и <xref:Microsoft.SqlServer.Management.Smo.BackupRestoreBase>.|  
|Объекты Rule и Rule2|Объект <xref:Microsoft.SqlServer.Management.Smo.Rule>.|  
|Объект Schedule|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объект ServerGroup|Удаляются.|  
|Объект ServerRole|Объект <xref:Microsoft.SqlServer.Management.Smo.ServerRole>.|  
|Объект SQLObjectList|Массив <xref:Microsoft.SqlServer.Management.Smo.SqlSmoObject>.|  
|Объекты SQLServer и SQLServer2|Объект <xref:Microsoft.SqlServer.Management.Smo.Server>.|  
|Объекты StoredProcedure и StoredProcedure2|Объекты <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> и <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>.|  
|Объекты Subscriber и Subscriber2|Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты SystemDatatype и SystemDataType2|Объект <xref:Microsoft.SqlServer.Management.Smo.DataType>.|  
|Объекты Table и Table2|Объект <xref:Microsoft.SqlServer.Management.Smo.Table>.|  
|Объект TargetServer|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект TargetServerGroup|Перемещено в пространство имен <xref:Microsoft.SqlServer.Management.Smo.Agent>.|  
|Объект TransactionLog|Функциональность перемещена в объект <xref:Microsoft.SqlServer.Management.Smo.Database>.|  
|Объекты TransArticle и TransArticle2|Объект <xref:Microsoft.SqlServer.Replication.TransArticle>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Метод Transfer и объект Transfer2|Объект <xref:Microsoft.SqlServer.Management.Smo.Transfer>.|  
|Объекты TransPublication и TransPublication2|Объект <xref:Microsoft.SqlServer.Replication.TransPublication>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты TransPullSubscription и TransPullSubscription2|Объект <xref:Microsoft.SqlServer.Replication.TransPullSubscription>. Перемещено в пространство имен <xref:Microsoft.SqlServer.Replication>.|  
|Объекты Trigger и Trigger2|Объект <xref:Microsoft.SqlServer.Management.Smo.Trigger>.|  
|Объекты User и User2|Объект <xref:Microsoft.SqlServer.Management.Smo.User>.|  
|Объекты UserDefinedDatatype и UserDefinedDataType2|Объект <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>.|  
|Объект UserDefinedFunction|Объекты <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> и <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>.|  
|Объекты View и View2|Объект <xref:Microsoft.SqlServer.Management.Smo.View>.|  
  
## <a name="see-also"></a>См. также:  
 [Учебник по программированию управляющих объектов SQL Server (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
