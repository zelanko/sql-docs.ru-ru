---
title: sp_enum_sqlagent_subsystems (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_enum_sqlagent_subsystems
- sp_enum_sqlagent_subsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_sqlagent_subsystems
ms.assetid: 019a3c9d-bac3-495b-a70a-2c19f1d2e20e
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ad4a380353dddd0bf17a25952b81220f2f2e6a2d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spenumsqlagentsubsystems-transact-sql"></a>sp_enum_sqlagent_subsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список подсистем агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_enum_sqlagent_subsystems  
```  
  
## <a name="arguments"></a>Аргументы  
 Нет  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Подсистема**|**nvarchar(40)**|Имя подсистемы.|  
|**Описание**|**nvarchar(512)**|Описание подсистемы.|  
|**subsystem_dll**|**nvarchar(510)**|Модуль DLL, содержащий подсистемы.|  
|**agent_exe**|**nvarchar(510)**|Исполняемый модуль, который используется подсистемой.|  
|**start_entry_point**|**nvarchar(30)**|Процедура, вызываемая агентом SQL Server при пошаговом выполнении задания.|  
|**event_entry_point**|**nvarchar(30)**|Процедура, вызываемая агентом SQL Server при пошаговом выполнении задания.|  
|**stop_entry_point**|**nvarchar(30)**|Процедура, вызываемая агентом SQL Server при пошаговом выполнении задания.|  
|**max_worker_threads**|**int**|Максимальное число потоков, запускаемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для этой подсистемы.|  
|**subsystem_id**|**int**|Идентификатор подсистемы.|  
  
## <a name="remarks"></a>Замечания  
 Процедура перечисляет подсистемы, доступные для экземпляра.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена предопределенная роль базы данных **SQLAgentOperatorRole** в базе данных **msdb** .  
  
 Дополнительные сведения о **SQLAgentOperatorRole**, в разделе [SQL Server Agent Fixed Database Roles](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности агента SQL Server](http://msdn.microsoft.com/library/d770d35c-c8de-4e00-9a85-7d03f45a0f0d)   
 [sp_add_jobstep (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
  
