---
title: syspolicy_system_health_state (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syspolicy_system_health_state_TSQL
- syspolicy_system_health_state
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_system_health_state view
ms.assetid: 00815106-9fe4-481d-a9e1-a256101887f4
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97759823fe4b4979da359f3ef0497466424c068b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="syspolicysystemhealthstate-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Это представление выводит по одной строке для всех возможных сочетаний политик (на основе которых производится управление) с выражениями целевых запросов. Используйте представление syspolicy_system_health_state для программной проверки политики работоспособности сервера. Следующая таблица описывает столбцы в представлении syspolicy_system_health_state.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|health_state_id|**bigint**|Идентификатор записи состояния работоспособности политики.|  
|policy_id|**int**|Идентификатор политики.|  
|last_run_date|**datetime**|Дата и время последнего запуска политики.|  
|target_query_expression_with_id|**nvarchar(400)**|Целевое выражение со значениями, присвоенными для определения переменных, которые определяют целевой объект, по отношению к которому оцениваются политики.|  
|target_query_expression|**nvarchar(max)**|Выражение, определяющее целевой объект, по отношению к которому оцениваются политики.|  
|набор по|**бит**|Состояние работоспособности цели в аспекте данной политики:<br /><br /> 0 = неуспешное завершение;<br /><br /> 1 = успешное завершение.|  
  
## <a name="remarks"></a>Замечания  
 Syspolicy_system_health_state, представление отображает самое недавнее состояние работоспособности выражения целевого запроса для каждой активной (включенной) политики. Обозреватель объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и страница «Данные обозревателя объектов» собирают состояние исправности политик из этого представления для отображения критического состояния работоспособности.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="see-also"></a>См. также  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Административные представления на основе политик (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
