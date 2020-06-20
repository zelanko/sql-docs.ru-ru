---
title: Двунаправленная репликация транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 57b18dde2e7134e0ba9eb6a9b2e8f5357d171a55
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043187"
---
# <a name="bidirectional-transactional-replication"></a>двунаправленная репликация транзакций
  Двунаправленная репликация транзакций представляет собой особую топологию репликации транзакций, которая позволяет двум серверам обмениваться изменениями друг с другом: каждый сервер публикует данные, после чего подписывается на публикацию с теми же данными от другого сервера. **@loopback_detection**Параметру [Sp_addsubscription &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) присваивается значение true, чтобы гарантировать, что изменения отправляются только подписчику и не приводят к тому, что изменения отправляются обратно издателю.  
  
 В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях такая топология поддерживается также одноранговой репликацией транзакций, но двунаправленная репликация позволяет увеличить производительность.  
  
## <a name="see-also"></a>См. также:  
 [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md)  
  
  
