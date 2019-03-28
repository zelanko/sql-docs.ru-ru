---
title: sp_expired_subscription_cleanup (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_expired_subscription_cleanup
- SP_EXPIRED_SUBSCRIPTION_CLEANUP_TSQL
helpviewer_keywords:
- sp_expired_subscription_cleanup
ms.assetid: 6abc29fe-d77a-4673-9d99-ae31c688012c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c8073b4e02e1eff910654bba635819b94b5cf5b2
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532516"
---
# <a name="spexpiredsubscriptioncleanup-transact-sql"></a>sp_expired_subscription_cleanup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Проверяет состояние всех подписок каждой публикации и удаляет из них те, срок которых истек. Эта хранимая процедура выполняется на издателе в любой базе данных или на распространителе в базе данных распространителя отличается от [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_expired_subscription_cleanup [ [ @publisher = ] 'publisher' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` Имя отличного [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *Публикация* — **sysname**, со значением по умолчанию NULL. Для издателя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот аргумент указывать не следует.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_expired_subscription_cleanup** используется во всех типах репликации.  
  
 **sp_expired_subscription_cleanup** выполняется путем задания истек срок действия подписки очистки для обнаружения и удаления подписки с истекшим сроком из баз данных публикации каждые 24 часа. Если публикация не была синхронизирована с издателем в течение всего срока хранения, то она считается публикацией с истекшим сроком, и все данные такой подписки на стороне издателя удаляются. Дополнительные сведения см. в разделе [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_expired_subscription_cleanup**.  
  
## <a name="see-also"></a>См. также  
 [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md)   
 [sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
