---
title: "процедура sp_syspolicy_subscribe_to_policy_category (Transact-SQL) | Документы Microsoft"
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
- sp_syspolicy_subscribe_to_policy_category
- sp_syspolicy_subscribe_to_policy_category_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_syspolicy_subscribe_to_policy_category
ms.assetid: de88cc49-bcc8-4dc6-8e59-ad85cfbfb2fb
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5d3ae8b6f35b5135066d9ab7164524406e165219
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spsyspolicysubscribetopolicycategory-transact-sql"></a>sp_syspolicy_subscribe_to_policy_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет подписку на категорию политики для указанной базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_subscribe_to_policy_category [ @policy_category = ] 'policy_category'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@policy_category=** ] **"***policy_category***"**  
 Имя категории политики, на которую подписывается база данных. *policy_category* — **sysname**и является обязательным.  
  
 Чтобы получить значения для *policy_category*, запросите системное представление msdb.dbo.syspolicy_policy_categories.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Процедура sp_syspolicy_subscribe_to_policy_category должна выполняться в контексте базы данных, в которую будет добавляться подписка на категорию политики.  
  
## <a name="permissions"></a>Permissions  
 Необходимо членство в предопределенной роли базы данных db_owner.  
  
## <a name="examples"></a>Примеры  
 В следующем примере добавляется подписка на категорию политики Finance для указанной базы данных.  
  
```  
USE <database_name>;  
  
EXEC sys.sp_syspolicy_subscribe_to_policy_category @policy_category = N'Finance';  
  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Управление на основе политик хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [процедура sp_syspolicy_unsubscribe_from_policy_category &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md)  
  
  
