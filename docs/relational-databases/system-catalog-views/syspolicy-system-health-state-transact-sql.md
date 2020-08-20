---
description: syspolicy_system_health_state (Transact-SQL)
title: syspolicy_system_health_state (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_system_health_state_TSQL
- syspolicy_system_health_state
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_system_health_state view
ms.assetid: 00815106-9fe4-481d-a9e1-a256101887f4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 66a99f117b9c6d8de7a92d328da812869a594f73
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493782"
---
# <a name="syspolicy_system_health_state-transact-sql"></a>syspolicy_system_health_state (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Это представление выводит по одной строке для всех возможных сочетаний политик (на основе которых производится управление) с выражениями целевых запросов. Представление syspolicy_system_health_state используется для проверки исправности политик сервера программным образом. В следующей таблице приведено описание столбцов представления syspolicy_system_health_state.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|health_state_id|**bigint**|Идентификатор записи состояния работоспособности политики.|  
|policy_id|**int**|Идентификатор политики.|  
|last_run_date|**datetime**|Дата и время последнего запуска политики.|  
|target_query_expression_with_id|**nvarchar(400)**|Целевое выражение со значениями, присвоенными для определения переменных, которые определяют целевой объект, по отношению к которому оцениваются политики.|  
|target_query_expression|**nvarchar(max)**|Выражение, определяющее целевой объект, по отношению к которому оцениваются политики.|  
|набор по|**bit**|Состояние работоспособности цели в аспекте данной политики:<br /><br /> 0 = неуспешное завершение;<br /><br /> 1 = успешное завершение.|  
  
## <a name="remarks"></a>Remarks  
 Представление syspolicy_system_health_state отображает самое последнее состояние работоспособности целевого выражения запроса для каждой активной (включенной) политики. Обозреватель объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и страница «Данные обозревателя объектов» собирают состояние исправности политик из этого представления для отображения критического состояния работоспособности.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="see-also"></a>См. также:  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Административные представления на основе политик (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
