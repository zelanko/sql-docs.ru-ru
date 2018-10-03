---
title: Двунаправленная репликация транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
ms.assetid: 98772e95-67ed-4010-8108-5113dbe709ff
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 86cdfaa9e7bf61b76acb953e3f2c6a1feb7d1dad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126831"
---
# <a name="bidirectional-transactional-replication"></a>двунаправленная репликация транзакций
  Двунаправленная репликация транзакций представляет собой особую топологию репликации транзакций, которая позволяет двум серверам обмениваться изменениями друг с другом: каждый сервер публикует данные, после чего подписывается на публикацию с теми же данными от другого сервера. Для параметра **@loopback_detection** хранимой процедуры [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) устанавливается значение TRUE, чтобы гарантировать, что изменения отправляются только подписчику и не приведут к отправке изменений обратно издателю.  
  
 В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версиях такая топология поддерживается также одноранговой репликацией транзакций, но двунаправленная репликация позволяет увеличить производительность.  
  
## <a name="see-also"></a>См. также  
 [Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md)  
  
  
