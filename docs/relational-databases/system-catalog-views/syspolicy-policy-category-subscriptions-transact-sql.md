---
title: syspolicy_policy_category_subscriptions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_category_subscriptions_TSQL
- syspolicy_policy_category_subscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_group_subscriptions view
ms.assetid: b3b3a7d7-0b78-46c0-9755-045f7a5692b9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 304e904ab95e4be58ba2a373bd6ed9c11131049f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094888"
---
# <a name="syspolicy_policy_category_subscriptions-transact-sql"></a>syspolicy_policy_category_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Это представление выводит по одной строке для каждой подписки на управление на основе политик в данном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждая строка описывает пару, состоящую из целевого объекта и категории политики. В следующей таблице приведено описание столбцов представления syspolicy_policy_group_subscriptions.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|policy_category_subscription_id|**int**|Идентификатор записи.|  
|target_type|**имеет sysname**|Тип объекта базы данных, который является целевым для этой подписки.|  
|target_object|**имеет sysname**|Имя целевого объекта.|  
|policy_category_id|**int**|Идентификатор категории политики, которая применяется к этому объекту.|  
  
## <a name="remarks"></a>Remarks  
 В представлении отображаются целевые объекты, подписанные на категории политик.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Представления управления на основе политик &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
