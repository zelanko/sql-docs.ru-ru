---
title: "Разнородная репликация базы данных | Microsoft Docs"
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
  - "разнородная репликация базы данных, о разнородной репликации базы данных"
  - "репликация [SQL Server], разнородная репликация базы данных"
  - "разнородная репликация базы данных"
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Разнородная репликация базы данных
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает следующие разнородные сценарии для репликации транзакций и репликации моментальных снимков.  
  
-   Публикация данных из Oracle в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Публикация данных с подписчиков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на подписчики, отличные от [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Разнородная репликация на подписчики, отличные от подписчика SQL Server, устарела. Публикация Oracle устарела. Для перемещения данных создайте решения с помощью системы отслеживания измененных данных и служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## Публикация данных из Oracle  
 Для публикации данных из Oracle можно использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], причем большинство функций и простота их использования такие же, как и в случае репликации моментальных снимков и репликации транзакций [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Публикация данных из Oracle идеально подходит для следующих сценариев:  
  
|Сценарий|Описание|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Разработка при помощи [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при работе с данными, реплицируемыми из базы данных, отличающейся от базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Серверы промежуточного хранения данных|Сохранить [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] синхронизации промежуточных баз данных, отличным от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных.|  
|Переход на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Протестируйте приложения в реальном времени совместно с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при репликации изменений исходной системы. Переключение на [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при успешном испытании миграции.|  
  
 Дополнительные сведения см. в разделе [Обзор публикации Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## Публикация данных на подписчиках, отличных от подписчиков SQL Server   
 Следующие базы данных, отличные от баз данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], поддерживаются в качестве подписчиков для публикации моментальных снимков и публикации транзакций.  
  
-   Oracle для всех платформ с поддержкой Oracle.  
  
-   IBM DB2 для AS400, MVS, Unix, Linux и Windows.  
  
 Дополнительные сведения см. в разделе [Non-SQL Server Subscribers](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
  