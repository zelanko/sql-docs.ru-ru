---
description: sp_syspolicy_update_policy_category_subscription (Transact-SQL)
title: sp_syspolicy_update_policy_category_subscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_update_policy_category_subscription_TSQL
- sp_syspolicy_update_policy_category_subscription
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_update_policy_category_subscription
ms.assetid: d0769566-8f5c-4c8a-84d3-ee17ea6e0cb4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 78f2b47d687c695c50710d045e99494ac61598b8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493003"
---
# <a name="sp_syspolicy_update_policy_category_subscription-transact-sql"></a>sp_syspolicy_update_policy_category_subscription (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Обновляет подписку на категорию политики для указанной базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syspolicy_update_policy_category_subscription [ @policy_category_subscription_id = ] policy_category_subscription_id  
    [ , [ @target_type = ] 'target_type' ]  
    [ , [ @target_object = ] 'target_object' ]  
    , [ @policy_category = ] 'policy_category'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @policy_category_subscription_id = ] policy_category_subscription_id` — Это идентификатор подписки на категорию политики, которую необходимо обновить. *policy_category_subscription_id* имеет **тип int**и является обязательным.  
  
`[ @target_type = ] 'target_type'` Тип целевого объекта подписки на категорию. Аргумент *target_type* имеет тип **sysname**и значение по умолчанию NULL.  
  
 При указании *target_type*значение должно быть равно "Database".  
  
`[ @target_object = ] 'target_object'` Имя базы данных, которая будет подписываться на категорию политики. Аргумент *target_object* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @policy_category = ] 'policy_category'` Имя категории политики, на которую должна подписываться база данных. Аргумент *policy_category* имеет тип **sysname**и значение по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Процедура sp_syspolicy_update_policy_category_subscription должна выполняться в контексте системной базы данных msdb.  
  
 Чтобы получить значения для *policy_category_subscription_id* и для *policy_category*, можно использовать следующий запрос:  
  
```  
SELECT a.policy_category_subscription_id, a.target_type, a.target_object  
    , b.name AS policy_category  
FROM msdb.dbo.syspolicy_policy_category_subscriptions AS a  
INNER JOIN msdb.dbo.syspolicy_policy_categories AS b  
ON a.policy_category_id = b.policy_category_id;  
```  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в предопределенной роли базы данных PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Возможное повышение уровня учетных данных. пользователи в роли PolicyAdministratorRole могут создавать серверные триггеры и планировать выполнение политик, которые могут повлиять на работу экземпляра [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Например, пользователи в роли PolicyAdministratorRole могут создать политику, которая может запретить создание большинства объектов в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Вследствие возможного повышения прав учетных данных роль PolicyAdministratorRole должна предоставляться только пользователям, имеющим право изменять конфигурацию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере существующая подписка на категорию политики обновляется таким образом, что база данных AdventureWorks2012 подписывается на категорию политики Finance.  
  
```  
EXEC msdb.dbo.sp_syspolicy_update_policy_category_subscription @policy_category_subscription_id = 1  
, @target_object = 'AdventureWorks2012'  
, @policy_category = 'Finance';  
  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры управления на основе политик &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_add_policy_category_subscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-subscription-transact-sql.md)   
 [sp_syspolicy_delete_policy_category_subscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-category-subscription-transact-sql.md)  
  
  
