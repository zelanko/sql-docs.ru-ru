---
title: syspolicy_policies (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syspolicy_policies_TSQL
- syspolicy_policies
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policies view
ms.assetid: aecf35bb-187e-4f80-870f-48081b88974e
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 5eb4c6d9586b2e7b6e946b461e9d6c200042223c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031255"
---
# <a name="syspolicypolicies-transact-sql"></a>syspolicy_policies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает одну строку для каждой политики управления на основе политик в данном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. syspolicy_policies принадлежит схеме dbo в базе данных msdb. Следующая таблица описывает столбцы в представлении syspolicy_policies.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|policy_id|**int**|Идентификатор политики.|  
|name|**sysname**|Имя политики.|  
|condition_id|**int**|Идентификатор условия, обеспечиваемого или проверяемого данной политикой.|  
|root_condition_id|**int**|Только для внутреннего применения.|  
|date_created|**datetime**|Дата и время создания политики.|  
|execution_mode|**int**|Режим оценки для политики. Возможны следующие значения:<br /><br /> 0 = по запросу<br /><br /> В этом режиме политика непосредственно указывается пользователем.<br /><br /> 1 = при изменении: запретить<br /><br /> В этом автоматизированном режиме для предотвращения нарушения политики используются триггеры DDL.<br /><br /> 2 = при изменении: только внесение в журнал<br /><br /> В этом автоматизированном режиме используется уведомление о событии для определения политики при возникновении соответствующего изменения и производится регистрация нарушений политики.<br /><br /> 4 = по расписанию<br /><br /> В этом автоматизированном режиме для периодического определения политики используется задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В этом режиме производится регистрация нарушений политики.<br /><br /> Примечание: Значение 3 не возможное значение.|  
|policy_category|**int**|Идентификатор категории политики управления на основе политик, к которой принадлежит данная политика. Если политика принадлежит к группе по умолчанию, значение этого параметра равно NULL.|  
|schedule_uid|**uniqueidentifier**|Если execution_mode по расписанию, содержит идентификатор расписания; в противном случае имеет значение NULL.|  
|description|**nvarchar(max)**|Описание политики. Столбец описания является необязательным и может принимать значение NULL.|  
|help_text|**nvarchar(4000)**|Текст гиперссылки, к которой принадлежит help_link.|  
|help_link|**nvarchar(2083)**|Дополнительная гиперссылка справки, присвоенная политике создателем этой политики.|  
|object_set_id|**int**|Идентификатор набора объектов, оцениваемого политикой.|  
|is_enabled|**bit**|Указывает, включена (1) или отключена (0) политика в данный момент.|  
|job_id|**uniqueidentifier**|Если execution_mode по расписанию, содержит идентификатор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задание агента, запускающего политику.|  
|created_by|**sysname**|Имя пользователя, создавшего политику.|  
|modified_by|**sysname**|Имя пользователя, изменившего эту политику последним. Содержит значение NULL, если изменений не было.|  
|date_modified|**datetime**|Дата и время создания политики. Содержит значение NULL, если изменений не было.|  
  
## <a name="remarks"></a>Примечания  
 При устранении неполадок управления на основе политик с помощью запроса [syspolicy_conditions](../../relational-databases/system-catalog-views/syspolicy-conditions-transact-sql.md) представление, чтобы определить, включена ли политика. В этом представлении также содержатся сведения о создателе политики и о том, кто ее последний раз изменял.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="see-also"></a>См. также  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Административные представления на основе политик (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
