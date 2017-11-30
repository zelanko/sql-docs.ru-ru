---
title: "процедура sp_syspolicy_add_policy_category_subscription (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_add_policy_category_subscription
- sp_syspolicy_add_policy_category_subscription_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_syspolicy_add_policy_category_subscription
ms.assetid: 4284f550-9a3f-4726-8181-15e407fbf08f
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec357296ce840bad84b6a0f1985858684f610a2b
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spsyspolicyaddpolicycategorysubscription-transact-sql"></a>sp_syspolicy_add_policy_category_subscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет подписку на категорию политики для указанной базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_add_policy_category_subscription [ @target_type = ] 'target_type'  
    , [ @target_object = ] 'target_object'  
    , [ @policy_category = ] 'policy_category'  
    [ , [ @policy_category_subscription_id = ] policy_category_subscription_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@target_type=** ] **"***target_type***"**  
 Целевой тип подписки на категорию. *target_type* — **sysname**является обязательным и должно быть присвоено «DATABASE».  
  
 [  **@target_object=** ] **"***target_object***"**  
 — Это имя базы данных, которая будет создана подписка на категорию. *target_object* — **sysname**и является обязательным.  
  
 [  **@policy_category=** ] **"***policy_category***"**  
 — Это имя категории политики необходимо подписаться. *policy_category* — **sysname**и является обязательным.  
  
 Чтобы получить значения для *policy_category*, запросите системное представление msdb.dbo.syspolicy_policy_categories.  
  
 [  **@policy_category_subscription_id=** ] *policy_category_subscription_id*  
 Идентификатор подписки на категорию. *policy_category_subscription_id* — **int**и возвращается как OUTPUT.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Процедура sp_syspolicy_add_policy_category_subscription должна выполняться в контексте системной базы данных msdb.  
  
 Если указать несуществующую категорию политики, то во время выполнения хранимой процедуры будет создана новая категория политики и подписка будет обязательной для всех баз данных. Если затем очистить обязательную подписку для новой категории, то подписка будет применяться только к базе данных, указанной в аргументе *target_object*. Дополнительные сведения об изменении параметра обязательной подписки см. в разделе [sp_syspolicy_update_policy_category (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура выполняется в контексте текущего владельца хранимой процедуры.  
  
## <a name="examples"></a>Примеры  
 В следующем примере для указанной базы данных настраивается подписка на категорию политики с именем «Table Naming Policies».  
  
```  
EXEC msdb.dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
, @target_object = N'AdventureWorks2012'  
, @policy_category = N'Table Naming Policies';  
  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Управление на основе политик хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [процедура sp_syspolicy_update_policy_category_subscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql.md)   
 [процедура sp_syspolicy_unsubscribe_from_policy_category &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md)  
  
  
