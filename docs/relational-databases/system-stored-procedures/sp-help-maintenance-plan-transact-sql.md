---
title: "sp_help_maintenance_plan (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_maintenance_plan_TSQL
- sp_help_maintenance_plan
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_maintenance_plan
ms.assetid: e972a510-960e-41d6-93c5-c71cd581a585
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e5669438c159010e1b5011418df913c3c2743aff
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sphelpmaintenanceplan-transact-sql"></a>sp_help_maintenance_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об указанном плане обслуживания. Если конкретный план не указан, то данная хранимая процедура возвращает сведения обо всех планах обслуживания.  
  
> **Примечание:** Эта хранимая процедура используется планами обслуживания базы данных. Эта возможность заменена планами обслуживания, не использующими данную хранимую процедуру. Используйте данную процедуру для поддержки планов обслуживания баз данных в установках, которые были обновлены с предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_maintenance_plan [ [ @plan_id = ] 'plan_id' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@plan_id =**] **'***plan_id***'**  
 Задает идентификатор плана обслуживания. *plan_id* — **UNIQUEIDENTIFIER**. Значение по умолчанию — NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если *plan_id* указано, **sp_help_maintenance_plan** возвращает три таблицы: плана и базы данных, а также задание.  
  
### <a name="plan-table"></a>Таблица Plan  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|Идентификатор плана обслуживания.|  
|**plan_name**|**sysname**|Имя плана обслуживания.|  
|**date_created**|**datetime**|Дата создания плана обслуживания.|  
|**Владелец**|**sysname**|Владелец плана обслуживания.|  
|**max_history_rows**|**int**|Максимальное количество строк, выделенное для журнала плана обслуживания в системной таблице.|  
|**remote_history_server**|**int**|Имя удаленного сервера, на который может быть записан хронологический отчет.|  
|**max_remote_history_rows**|**int**|Максимальное количество строк, выделенное в системной таблице на удаленном сервере, куда может быть записан хронологический отчет.|  
|**user_defined_1**|**int**|Значение по умолчанию — NULL.|  
|**user_defined_2**|**nvarchar(100)**|Значение по умолчанию — NULL.|  
|**user_defined_3**|**datetime**|Значение по умолчанию — NULL.|  
|**user_defined_4**|**uniqueidentifier**|Значение по умолчанию — NULL.|  
  
### <a name="database-table"></a>Таблица Database  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|**database_name**|Имя всех баз данных, связанных с планом обслуживания. *database_name* — **sysname**.|  
  
### <a name="job-table"></a>Таблица Job  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|**job_id**|Идентификатор всех заданий, связанных с планом обслуживания. *Аргумент job_id* — **uniqueidentifier**.|  
  
## <a name="remarks"></a>Remarks  
 **sp_help_maintenance_plan** в **msdb** базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_help_maintenance_plan**.  
  
## <a name="examples"></a>Примеры  
 В этом примере возвращаются сведения описательного характера о плане обслуживания FAD6F2AB-3571-11D3-9D4A-00C04FB925FC.  
  
```  
EXECUTE   sp_help_maintenance_plan   
   N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC';  
```  
  
## <a name="see-also"></a>См. также  
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [План обслуживания базы данных хранимой процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
