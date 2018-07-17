---
title: Управление именами для входа и паролями при репликации | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server replication]
- logins [SQL Server replication], managing
- security [SQL Server replication], logins
- passwords [SQL Server replication]
- security [SQL Server replication], passwords
ms.assetid: 277759f9-b0da-4524-8abe-0460cdab69ec
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fe2c3baa67c0cb38becf3373004b1ac61e4448eb
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351426"
---
# <a name="manage-logins-and-passwords-in-replication"></a>Управление именами входа и паролями в репликации
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При настройке репликации укажите имена входа и пароли для агентов репликации. После настройки репликации можно изменить имена входа и пароли. Дополнительные сведения см. в статье [View and Modify Replication Security Settings](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md). Если вы измените пароль для учетной записи, которая используется агентом репликации, выполните процедуру [sp_changereplicationserverpasswords &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changereplicationserverpasswords-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)  (Модель безопасности агента репликации)  
 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Безопасность и защита (репликация)](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
