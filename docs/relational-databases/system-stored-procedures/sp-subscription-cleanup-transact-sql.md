---
title: sp_subscription_cleanup (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_subscription_cleanup_TSQL
- sp_subscription_cleanup
helpviewer_keywords:
- sp_subscription_cleanup
ms.assetid: bdc8aaa0-ff2d-40c2-84b2-4ba513ced279
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 74154300cd85e18d17c3f8c6499acb2f331bcdbf
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52759786"
---
# <a name="spsubscriptioncleanup-transact-sql"></a>sp_subscription_cleanup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Очищает метаданные после удаления подписки на подписчике. Для синхронизирующейся подписки транзакций, кроме того, выполняет триггеры немедленного обновления. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_subscription_cleanup [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
    [ , [ @publication = ] 'publication']  
    [ , [ @reserved = ] 'reserved']  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=**] **"***издателя***"**  
 Имя издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publisher_db=**] **"***publisher_db***"**  
 Имя базы данных издателя. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, значение по умолчанию NULL. Если значение равно NULL, будут удалены все подписки, использующие публикацию общего агента в базе данных публикации.  
  
 [  **@reserved=**] **"***зарезервированные***"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_subscription_cleanup** используется в репликации транзакций и моментальных снимков.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_subscription_cleanup**.  
  
## <a name="see-also"></a>См. также  
 [sp_expired_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-expired-subscription-cleanup-transact-sql.md)   
 [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
