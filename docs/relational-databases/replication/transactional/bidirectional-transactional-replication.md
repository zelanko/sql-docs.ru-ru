---
title: Двунаправленная репликация транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 85ab0f993e919b491376ff3d9ffa44afefd42603
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71710692"
---
# <a name="bidirectional-transactional-replication"></a>двунаправленная репликация транзакций
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Двунаправленная репликация транзакций представляет собой особую топологию репликации транзакций, которая позволяет двум серверам обмениваться изменениями друг с другом: каждый сервер публикует данные, после чего подписывается на публикацию с теми же данными от другого сервера. Для параметра `@loopback_detection` хранимой процедуры [sp_addsubscription &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) устанавливается значение TRUE, чтобы изменения отправлялись только подписчику и не отправлялись обратно издателю.  
  
 В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях такая топология поддерживается также одноранговой репликацией транзакций, но двунаправленная репликация позволяет увеличить производительность.  
  
## <a name="see-also"></a>См. также:  
 [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
