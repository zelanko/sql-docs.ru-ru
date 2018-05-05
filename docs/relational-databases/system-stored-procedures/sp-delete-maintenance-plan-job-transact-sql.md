---
title: sp_delete_maintenance_plan_job (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sp_delete_maintenance_plan_job
- sp_delete_maintenance_plan_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_maintenance_plan_job
ms.assetid: 1c2148c3-2928-4d9b-b1c8-3512cfbd6a63
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7c0d97b23a69cfa695b4b4dbde3729f622d47487
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spdeletemaintenanceplanjob-transact-sql"></a>sp_delete_maintenance_plan_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отменяет привязку указанного плана обслуживания от указанного задания.  
  
> [!NOTE]  
>  Эта хранимая процедура используется планами обслуживания базы данных. Эта возможность заменена планами обслуживания, не использующими данную хранимую процедуру. Используйте данную процедуру для поддержки планов обслуживания баз данных в установках, которые были обновлены с предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_maintenance_plan_job [ @plan_id = ] 'plan_id' ,   
   [ @job_id = ] 'job_id'   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@plan_id =**] **"***plan_id***"**  
 Указывает идентификатор плана обслуживания. *plan_id* — **uniqueidentifier**, и должен быть допустимым идентификатором.  
  
 [ **@job_id =**] **'***job_id***'**  
 Указывает идентификатор задания, с которым связан план обслуживания. *Аргумент job_id* — **uniqueidentifier**, и должен быть допустимым идентификатором.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_delete_maintenance_plan_job** должна запускаться из **msdb** базы данных.  
  
 Если все задания удалены из плана обслуживания, рекомендуется выполнить процедуру **sp_delete_maintenance_plan_db** для удаления из плана оставшихся баз данных.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_delete_maintenance_plan_job**.  
  
## <a name="examples"></a>Примеры  
 В этом примере задание B8FCECB1-E22C-11D2-AA64-00C04F688EAE удаляется из плана обслуживания.  
  
```  
EXECUTE   sp_delete_maintenance_plan_job N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'B8FCECB1-E22C-11D2-AA64-00C04F688EAE';  
```  
  
## <a name="see-also"></a>См. также  
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Хранимые процедуры плана обслуживания базы данных &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
