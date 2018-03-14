---
title: "Двунаправленная репликация транзакций | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ccca24e2509bdb0f3de8c8c98e1ab5b652856423
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="bidirectional-transactional-replication"></a>двунаправленная репликация транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Двунаправленная репликация транзакций представляет собой особую топологию репликации транзакций, которая позволяет двум серверам обмениваться изменениями друг с другом: каждый сервер публикует данные, после чего подписывается на публикацию с теми же данными от другого сервера. Для параметра **@loopback_detection** хранимой процедуры [sp_addsubscription &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) устанавливается значение TRUE, чтобы гарантировать, что изменения отправляются только подписчику и не приведут к отправке изменений обратно издателю.  
  
 В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях такая топология поддерживается также одноранговой репликацией транзакций, но двунаправленная репликация позволяет увеличить производительность.  
  
## <a name="see-also"></a>См. также:  
 [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
