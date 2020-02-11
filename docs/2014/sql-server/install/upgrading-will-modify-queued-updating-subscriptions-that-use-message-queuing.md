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
manager: craigg
ms.openlocfilehash: 1c723050f9e860534c5298df9a487337e319ff91
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091405"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a>Обновление изменит обновляемую посредством очередей подписку, использующую службу очередей сообщений
  Советник по переходу обнаружил, что у вас может быть одна или несколько обновляемых [!INCLUDE[msCoName](../../includes/msconame-md.md)] посредством очередей подписок, использующих очередь сообщений (также называемую MSMQ). Эта служба больше не поддерживается при репликации, поэтому для использования очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписки будут изменены.  
  
 Допускается только значение **SQL** . Если в существующих публикациях используется служба очередей сообщений, при обновлении следует настроить их для использования очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Приложения, для которых установлено обновление посредством очередей с помощью службы очередей сообщений, следует переписать для их соответствия очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения об обновляемых посредством очередей подписках см. в разделе «Обновляемые подписки для репликации транзакций» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если при обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет запущена служба очередей сообщений, то существующие очереди подписки MSMQ будут удалены.  
  
 Если служба очередей сообщений не запущена, то необходимо вручную удалить очереди после завершения обновления. Дополнительные сведения о процессе удаления очередей см. в документации по Windows.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы репликации при обновлении](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
