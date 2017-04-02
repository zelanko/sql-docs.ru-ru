---
title: "Издатели, отличные от издателей SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "разнородная репликация базы данных, издатели, отличные от издателей SQL Server"
  - "издатели, отличные от издателей SQL Server"
  - "разнородные источники данных, издатели, отличные от издателей SQL Server"
  - "издатели [репликация SQL Server], Oracle"
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Издатели, отличные от издателей SQL Server
  Публикация данных из отличных[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] источников позволяет консолидировать данные в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может использовать подписку на моментальные снимки или транзакционные данные, публикуемые из базы данных Oracle. Дополнительные сведения о публикации из Oracle см. в разделе [Обзор публикации Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
 Разнородная репликация на подписчики, отличные от подписчика SQL Server, устарела. Публикация Oracle устарела. Для перемещения данных создайте решения с помощью системы отслеживания измененных данных и служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Публикация из баз данных, отличных от баз данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], прекрасно подходит для следующих сценариев:  
  
|Сценарий|Описание|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Разработка при помощи [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при работе с данными, реплицируемыми из базы данных, отличающейся от базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Серверы промежуточного хранения данных|Сохранить [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] синхронизации промежуточных баз данных, отличным от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных.|  
|Переход на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Протестируйте приложения в реальном времени совместно с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при репликации изменений исходной системы. Переключение на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при успешном испытании миграции.|  
  
## См. также:  
 [Разнородная репликация базы данных](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  