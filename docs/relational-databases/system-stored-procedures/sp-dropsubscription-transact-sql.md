---
title: sp_dropsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropsubscription
- sp_dropsubscription_TSQL
helpviewer_keywords:
- sp_dropsubscription
ms.assetid: 7551f345-5510-4684-ab53-f9057249d13a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 08e25ee6f2de589c3d7367c140bd0ea63d4cec1e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52812975"
---
# <a name="spdropsubscription-transact-sql"></a>sp_dropsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет подписки на некоторую статью, публикацию или набор подписок на издателе. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dropsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
        , [ @subscriber= ] 'subscriber'  
    [ , [ @destination_db= ] 'destination_db' ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=** ] **"**_публикации_**"**  
 Имя связанной публикации. *Публикация* — **sysname**, значение по умолчанию NULL. Если **все**, все подписки для всех публикаций для указанного подписчика будут отменены. *Публикация* является обязательным параметром.  
  
 [  **@article=** ] **"**_статье_**"**  
 Имя статьи. *статья* — **sysname**, со значением по умолчанию NULL. Если **все**, указанные подписки на все статьи для каждой публикации и подписчика будут удалены. Используйте **все** для публикаций, которые разрешено немедленное обновление.  
  
 [  **@subscriber=** ] **"**_subscribe_r **"**  
 Имя подписчика, подписки которого будут удалены. *подписчик* — **sysname**, не имеет значения по умолчанию. Если **все**, удаляются все подписки для всех подписчиков.  
  
 [  **@destination_db=** ] **"**_destination_db_**"**  
 Имя целевой базы данных. *destination_db* — **sysname**, значение по умолчанию NULL. Если имеет значение NULL, то все подписки от этого подписчика удаляются.  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@reserved=** ] **"**_зарезервированные_**"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropsubscription** используется в репликации моментальных снимков и репликации транзакций.  
  
 Если удаляется подписка на статью в публикации с немедленной синхронизацией, то нельзя добавить ее обратно до тех пор, пока не будут удалены подписки на все статьи в публикации и, затем, не добавлены все одновременно обратно.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropsubscription-tran_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера, **db_owner** предопределенной роли базы данных, или пользователь, создавший подписку могут выполнять процедуру **sp_dropsubscription**.  
  
## <a name="see-also"></a>См. также  
 [Удаление принудительной подписки](../../relational-databases/replication/delete-a-push-subscription.md)   
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
