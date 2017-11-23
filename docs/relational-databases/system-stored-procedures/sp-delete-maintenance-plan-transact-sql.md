---
title: "sp_delete_maintenance_plan (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_delete_maintenance_plan
- sp_delete_maintenance_plan_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_delete_maintenance_plan
ms.assetid: 6f36b63f-3d18-4d42-9469-2febb6926530
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 87d9d2da47797acd2b18a8b2edb2e69e8d0af405
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="spdeletemaintenanceplan-transact-sql"></a>sp_delete_maintenance_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет указанный план обслуживания.  
  
> [!NOTE]  
>  Эта хранимая процедура используется планами обслуживания базы данных. Эта возможность заменена планами обслуживания, не использующими данную хранимую процедуру. Используйте данную процедуру для поддержки планов обслуживания баз данных в установках, которые были обновлены с предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_maintenance_plan [ @plan_id = ] 'plan_id'   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@plan_id =**] **"***plan_id***"**  
 Указывает идентификатор удаляемого плана обслуживания. *plan_id* — **uniqueidentifier**, и должен быть допустимым идентификатором.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_delete_maintenance_plan** должна запускаться из **msdb** базы данных.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_delete_maintenance_plan**.  
  
## <a name="examples"></a>Примеры  
 Удаление плана обслуживания, созданного с помощью **sp_add_maintenance_plan**.  
  
```  
EXECUTE sp_delete_maintenance_plan 'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC';  
```  
  
## <a name="see-also"></a>См. также:  
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [План обслуживания базы данных хранимой процедуры &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
