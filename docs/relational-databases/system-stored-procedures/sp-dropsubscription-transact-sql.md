---
title: sp_dropsubscription (Transact-SQL) | Документация Майкрософт
description: Удаляет подписки на публикацию в статьях, публикациях или подписках на издателе. Эта хранимая процедура выполняется на издателе в базе данных публикации.
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c8c13030b1232a01aac14ac936323c05c540ab1f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89536568"
---
# <a name="sp_dropsubscription-transact-sql"></a>sp_dropsubscription (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

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
`[ @publication = ] 'publication'` Имя связанной публикации. Аргумент *publication* имеет тип **sysname**и значение по умолчанию NULL. Если задано значение **ALL**, то все подписки для всех публикаций указанного подписчика отменяются. параметр *publication* является обязательным.  
  
`[ @article = ] 'article'` Имя статьи. Аргумент *article* имеет тип **sysname**и значение по умолчанию NULL. Если **все**, то подписки на все статьи для каждой указанной публикации и подписчика удаляются. Используйте **все** для публикаций, которые допускают немедленное обновление.  
  
`[ @subscriber = ] 'subscriber'` Имя подписчика, для которого будут удалены подписки. Аргумент *Subscriber* имеет тип **sysname**и не имеет значения по умолчанию. Если **все**, то все подписки для всех подписчиков удаляются.  
  
`[ @destination_db = ] 'destination_db'` Имя целевой базы данных. Аргумент *destination_db* имеет тип **sysname**и значение по умолчанию NULL. Если имеет значение NULL, то все подписки от этого подписчика удаляются.  
  
`[ @ignore_distributor = ] ignore_distributor`  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @reserved = ] 'reserved'`  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_dropsubscription** используется в моментальных снимках и репликации транзакций.  
  
 Если удаляется подписка на статью в публикации с немедленной синхронизацией, то нельзя добавить ее обратно до тех пор, пока не будут удалены подписки на все статьи в публикации и, затем, не добавлены все одновременно обратно.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropsubscription-tran_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , предопределенной роли базы данных **db_owner** или пользователя, создавшего подписку, могут выполнять **sp_dropsubscription**.  
  
## <a name="see-also"></a>См. также  
 [Удаление принудительной подписки](../../relational-databases/replication/delete-a-push-subscription.md)   
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
