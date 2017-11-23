---
title: "syspolicy_policy_category_subscriptions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_category_subscriptions_TSQL
- syspolicy_policy_category_subscriptions
dev_langs: TSQL
helpviewer_keywords: syspolicy_policy_group_subscriptions view
ms.assetid: b3b3a7d7-0b78-46c0-9755-045f7a5692b9
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a5e9ffa5b4e2c005a85966ea4ee989b1f8938d1c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syspolicypolicycategorysubscriptions-transact-sql"></a>syspolicy_policy_category_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Это представление выводит по одной строке для каждой подписки на управление на основе политик в данном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждая строка описывает пару целевой объект и политики категории. Следующая таблица описывает столбцы в представлении syspolicy_policy_group_subscriptions.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|policy_category_subscription_id|**int**|Идентификатор записи.|  
|target_type|**sysname**|Тип объекта базы данных, который является целевым для этой подписки.|  
|target_object|**sysname**|Имя целевого объекта.|  
|policy_category_id|**int**|Идентификатор категории политики, которая применяется к этому объекту.|  
  
## <a name="remarks"></a>Замечания  
 В представлении отображаются целевые объекты, подписанные на категории политик.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Административные представления на основе политик (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
