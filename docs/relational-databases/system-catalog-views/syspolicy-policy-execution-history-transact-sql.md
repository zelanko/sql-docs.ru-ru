---
title: syspolicy_policy_execution_history (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 246f9ca4d8368f193547758d079169d2252a2d00
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="syspolicypolicyexecutionhistory-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Указывает время выполнения политик, результат каждого выполнения и сведения об ошибках, возникших при выполнении. Следующая таблица описывает столбцы в представлении syspolicy_policy_execution_history.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|Идентификатор записи. Каждая запись указывает на политику и время ее выполнения.|  
|policy_id|**int**|Идентификатор политики.|  
|start_date|**datetime**|Дата и время последней попытки запуска политики.|  
|end_date|**datetime**|Время, когда политика закончила выполняться.|  
|набор по|**бит**|Успешность или неуспешность выполнения политики. 0 = неуспешное завершение, 1 = успешное завершение.|  
|exception_message|**nvarchar(max)**|Сообщение, выданное в результате возникшего исключения.|  
|exception|**nvarchar(max)**|Описание возникшего исключения.|  
  
## <a name="remarks"></a>Замечания  
 [Syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) содержит подробности, связанные с целевыми объектами политик и проверенными выражениями, задающими.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
## <a name="see-also"></a>См. также  
 [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Административные представления на основе политик (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
