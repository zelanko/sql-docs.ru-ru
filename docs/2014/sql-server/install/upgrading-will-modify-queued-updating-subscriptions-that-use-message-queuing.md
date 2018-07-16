---
title: Обновление изменит очереди обновляемых подписок, использующих службу очередей сообщений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication]
- MSMQ [SQL Server replication]
- queues [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
ms.assetid: 97944de3-fbad-4db1-939a-dcd550bf5893
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 37fcfeecfb7160b48d2ed875f76e3b970c29a880
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272370"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a>Обновление изменит обновляемую посредством очередей подписку, использующую службу очередей сообщений
  Помощник по обновлению обнаружил одну или несколько обновляемых посредством очередей подписок, использующих [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (MSMQ). Эта служба больше не поддерживается при репликации, поэтому для использования очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписки будут изменены.  
  
 Только значение **sql** разрешено. Если в существующих публикациях используется служба очередей сообщений, при обновлении следует настроить их для использования очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Приложения, для которых установлено обновление посредством очередей с помощью службы очередей сообщений, следует переписать для их соответствия очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения об обновляемых посредством очередей подписках см. в разделе «Обновляемые подписки для репликации транзакций» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если при обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет запущена служба очередей сообщений, то существующие очереди подписки MSMQ будут удалены.  
  
 Если служба очередей сообщений не запущена, то необходимо вручную удалить очереди после завершения обновления. Дополнительные сведения о процессе удаления очередей см. в документации по Windows.  
  
## <a name="see-also"></a>См. также  
 [Проблемы репликации при обновлении](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
