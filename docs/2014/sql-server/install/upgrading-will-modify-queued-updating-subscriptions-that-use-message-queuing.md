---
title: Обновление изменит очереди обновляемых подписок, использующих очереди сообщений | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- subscriptions [SQL Server replication]
- MSMQ [SQL Server replication]
- queues [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
ms.assetid: 97944de3-fbad-4db1-939a-dcd550bf5893
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: efb1b244385061bee985ec04b5f90d3fb349aef3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096059"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a>Обновление изменит обновляемую посредством очередей подписку, использующую службу очередей сообщений
  Советник по переходу обнаружил, что может иметь одно или несколько обновляемых посредством очередей подписками, использующими [!INCLUDE[msCoName](../../includes/msconame-md.md)] очереди сообщений (MSMQ). Эта служба больше не поддерживается при репликации, поэтому для использования очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписки будут изменены.  
  
 Только значение **sql** разрешено. Если в существующих публикациях используется служба очередей сообщений, при обновлении следует настроить их для использования очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Приложения, для которых установлено обновление посредством очередей с помощью службы очередей сообщений, следует переписать для их соответствия очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения об обновляемых посредством очередей подписках см. в разделе «Обновляемые подписки для репликации транзакций» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если при обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет запущена служба очередей сообщений, то существующие очереди подписки MSMQ будут удалены.  
  
 Если служба очередей сообщений не запущена, то необходимо вручную удалить очереди после завершения обновления. Дополнительные сведения о процессе удаления очередей см. в документации по Windows.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления репликации](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  