---
title: "Двунаправленная репликация транзакций | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "двунаправленная репликация"
  - "репликация транзакций, двунаправленная репликация"
  - "двунаправленная репликация транзакций"
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# Двунаправленная репликация транзакций
  Двунаправленная репликация транзакций представляет собой особую топологию репликации транзакций, которая позволяет двум серверам обмениваться изменениями друг с другом: каждый сервер публикует данные, после чего подписывается на публикацию с теми же данными от другого сервера.  **@Loopback_detection** параметр [sp_addsubscription & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) Чтобы убедиться, что изменения отправляются только подписчику и не приводят к отправке издателю изменений имеет значение TRUE.  
  
 В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий, данная топология поддерживается также-одноранговой репликации транзакций, но двунаправленная репликация позволяет увеличить производительность.  
  
## См. также:  
 [Одноранговая репликация транзакций](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  