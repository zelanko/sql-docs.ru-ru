---
title: При обновлении будут изменены обновляемые посредством очередей подписки, использующие службу очередей сообщений | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication]
- MSMQ [SQL Server replication]
- queues [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
ms.assetid: 97944de3-fbad-4db1-939a-dcd550bf5893
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d44cbad43d75634cbf8660110cc879522265c54d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058861"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a>Обновление изменит обновляемую посредством очередей подписку, использующую службу очередей сообщений
  Советник по переходу обнаружил, что у вас может быть одна или несколько обновляемых посредством очередей подписок, использующих [!INCLUDE[msCoName](../../includes/msconame-md.md)] очередь сообщений (также называемую MSMQ). Эта служба больше не поддерживается при репликации, поэтому для использования очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписки будут изменены.  
  
 Допускается только значение **SQL** . Если в существующих публикациях используется служба очередей сообщений, при обновлении следует настроить их для использования очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Приложения, для которых установлено обновление посредством очередей с помощью службы очередей сообщений, следует переписать для их соответствия очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения об обновляемых посредством очередей подписках см. в разделе «Обновляемые подписки для репликации транзакций» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если при обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет запущена служба очередей сообщений, то существующие очереди подписки MSMQ будут удалены.  
  
 Если служба очередей сообщений не запущена, то необходимо вручную удалить очереди после завершения обновления. Дополнительные сведения о процессе удаления очередей см. в документации по Windows.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы репликации при обновлении](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
