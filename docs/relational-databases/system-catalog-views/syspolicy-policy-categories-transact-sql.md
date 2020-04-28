---
title: syspolicy_policy_categories (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_categories
- syspolicy_policy_categories_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_groups view
ms.assetid: 65f080c7-771f-4cf6-a7a0-88882c637f8d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: af9086ba9de7d9c61bcedecd4331e7e0e77d6489
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68121121"
---
# <a name="syspolicy_policy_categories-transact-sql"></a>syspolicy_policy_categories (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Это представление выводит по одной строке на каждую категорию политики, используемую в управлении на основе политик в данном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Категории политик помогают организовать многочисленные политики. В следующей таблице описываются столбцы представления syspolicy_policy_groups.  
 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|policy_category_id|**int**|Идентификатор категории политики.|  
|name|**sysname**|Имя категории политики.|  
|mandate_database_subscriptions|**bit**|Указывает, применима ли категория политики ко всем базам данных в экземпляре без явной подписки (1), или категория политики должна быть применена к базе данных с помощью явной подписки (0).|  
  
## <a name="remarks"></a>Remarks  
 Выводит список групп политик управления на основе политик.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Административные представления на основе политик (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
