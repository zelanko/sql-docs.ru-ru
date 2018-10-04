---
title: Основные понятия исполняемых файлов агента репликации | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- replication
ms.topic: reference
helpviewer_keywords:
- programming interfaces [SQL Server replication]
- programming [SQL Server replication], agents
- replication [SQL Server], agents and profiles
- agents [SQL Server replication], executables
- command prompt [SQL Server replication]
ms.assetid: cba476df-d4ea-44c9-bb86-81488971e328
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7a3f8fd68a103b66670051f18ceeb12e0e9f85f2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48107234"
---
# <a name="replication-agent-executables-concepts"></a>Основные понятия исполняемых файлов агента репликации
  Управление агентами репликации может осуществляться программным путем следующими способами:  
  
-   использованием управляемых программных интерфейсов агента в пространстве имен <xref:Microsoft.SqlServer.Replication>;  
  
-   вызовом исполняемых файлов агента из командной строки с предоставленным набором параметров.  
  
 Непосредственный вызов агентов репликации из командной строки позволяет использовать агенты для доступа к ним программным путем из пакетных файлов сценариев командной строки. Если агент вызван из командной строки, то выполняется в учетной записи системы безопасности [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows того пользователя, который вызвал агента или запустил пакетный файл.  
  
 С применением исполняемых файлов можно запускать экземпляры следующих агентов репликации.  
  
-   [Агент распространения репликации](../agents/replication-distribution-agent.md)  
  
-   [Агент чтения журнала репликации](../agents/replication-log-reader-agent.md)  
  
-   [Replication Merge Agent](../agents/replication-merge-agent.md)  
  
-   [Replication Queue Reader Agent](../agents/replication-queue-reader-agent.md)  
  
-   [Replication Snapshot Agent](../agents/replication-snapshot-agent.md)  
  
 При вызове агентов репликации можно использовать профили производительности для автоматической передачи определенного набора параметров для исполняемого файла агента. Дополнительные сведения см. в разделе [Replication Agent Profiles](../agents/replication-agent-profiles.md).  
  
## <a name="examples"></a>Примеры  
 В следующих примерах показано, как вызывать агенты репликации из командной строки. Агенты репликации могут быть также вызваны с использованием объектов RMO. Дополнительные сведения см. в статье [Синхронизация подписок (репликация)](../synchronize-subscriptions-replication.md).  
  
> [!NOTE]  
>  Символы обозначения конца строки в этих примерах были добавлены для повышения удобства чтения. В пакетном файле команды необходимо вводить в одной строке.  
  
### <a name="running-the-snapshot-agent"></a>Управление агентом моментальных снимков  
 Этот пример пакетного файла вызывает агент моментальных снимков из командной строки для создания моментального снимка публикации **AdvWorksSalesOrdersMerge**.  
  
```  
REM -- Declare variables  
SET Publisher=%InstanceName%;  
SET PublicationDB=AdventureWorks2012;   
SET Publication=AdvWorksSalesOrdersMerge;   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1 ;  
  
```  
  
### <a name="running-the-distribution-agent"></a>Управление агентом распространителя  
 Этот пример пакетного файла вызывает агент распространителя из командной строки для непрерывной репликации изменений из публикации **AdvWorksProductTran** подписчику с принудительной подпиской.  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksProductsTran;  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4 ;  
  
```  
  
### <a name="running-the-merge-agent"></a>Управление агентом слияния  
 Этот пример пакетного файла вызывает агент слияния из командной строки для синхронизации подписки по запросу для публикации **AdvWorksSalesOrdersMerge**.  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksSalesOrdersMerge;  
  
REM --Start the Merge Agent with concurrent upload and download processes.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publication %Publication%    
-Publisher %Publisher%  -Subscriber  %Subscriber%  -Distributor %Publisher%    
-PublisherDB %PublicationDB%  -SubscriberDB %SubscriptionDB% -PublisherSecurityMode 1    
-OutputVerboseLevel 2  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1    
-Validate 3  -ParallelUploadDownload 1 ;  
  
```  
  
  
