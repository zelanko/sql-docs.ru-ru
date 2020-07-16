---
title: Двунаправленная репликация транзакций | Документация Майкрософт
description: Двунаправленная репликация транзакций позволяет двум серверам обмениваться изменениями. Каждый сервер публикует данные и затем подписывается на публикацию другого сервера.
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: afd98116cd58e1e4c5fd3c284ea228d6c5ca6007
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159422"
---
# <a name="bidirectional-transactional-replication"></a>двунаправленная репликация транзакций
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/applies-to-version/sql-asdbmi.md)]
  Двунаправленная репликация транзакций представляет собой особую топологию репликации транзакций, которая позволяет двум серверам обмениваться изменениями друг с другом: каждый сервер публикует данные, после чего подписывается на публикацию с теми же данными от другого сервера. Для параметра `@loopback_detection` хранимой процедуры [sp_addsubscription &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) устанавливается значение TRUE, чтобы изменения отправлялись только подписчику и не отправлялись обратно издателю.  
  
 В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях такая топология поддерживается также одноранговой репликацией транзакций, но двунаправленная репликация позволяет увеличить производительность.  
  
## <a name="see-also"></a>См. также:  
 [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
