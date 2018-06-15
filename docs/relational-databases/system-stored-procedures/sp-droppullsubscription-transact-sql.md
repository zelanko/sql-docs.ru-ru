---
title: sp_droppullsubscription (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_droppullsubscription
- sp_droppullsubscription_TSQL
helpviewer_keywords:
- sp_droppullsubscription
ms.assetid: 7352d94a-f8f2-42ea-aaf1-d08c3b5a0e76
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f87d5298d9f67c349a71faf8cff95b2ac23304d0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32989682"
---
# <a name="spdroppullsubscription-transact-sql"></a>sp_droppullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет подписку в текущей базе данных подписчика. Эта хранимая процедура выполняется на подписчике в базе данных подписки по запросу.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_droppullsubscription [ @publisher= ] 'publisher'  
        , [ @publisher_db= ] 'publisher_db'  
        , [ @publication= ] 'publication'  
    [ , [ @reserved= ] reserved ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=** ] **"***издатель***"**  
 Имя удаленного сервера. *издатель* — **sysname**, не имеет значения по умолчанию. Если **все**, удаляется подписка на всех издателей.  
  
 [  **@publisher_db=** ] **"***publisher_db***"**  
 Имя базы данных издателя. *publisher_db* — **sysname**, не имеет значения по умолчанию. **все** означает все базы данных издателя.  
  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию. Если **все**, удаляется подписка на все публикации.  
  
 [  **@reserved=** ] *зарезервированные*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_droppullsubscription** используется в репликации моментальных снимков и репликации транзакций.  
  
 **sp_droppullsubscription** удаляет соответствующую строку в [MSreplication_subscriptions &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) таблицы и соответствующего агента распространителя на подписчике. Если ни одной строки остаются в [MSreplication_subscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md), он удаляет таблицу.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-droppullsubscription-_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или пользователь, создавший подписку по запросу могут выполнять процедуру **sp_droppullsubscription**. **Db_owner** предопределенной роли базы данных может выполнять только в том случае **sp_droppullsubscription** Если пользователь, создавший подписку по запросу, принадлежит к этой роли.  
  
## <a name="see-also"></a>См. также  
 [Удаление подписки по запросу](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
