---
title: sp_delete_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_schedule
- sp_delete_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_schedule
ms.assetid: 18b2c985-47b8-49c8-82d1-8a4af3d7d33a
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0a531b3673320e3c1e521e68c511e21b7976d1af
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394338"
---
# <a name="spdeleteschedule-transact-sql"></a>sp_delete_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет расписание.  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_schedule { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @force_delete = ] force_delete  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@schedule_id=** ] *schedule_id*  
 Идентификационный номер удаляемого расписания. *schedule_id* — **int**, значение по умолчанию NULL.  
  
> **Примечание:** либо *schedule_id* или *schedule_name* должен быть указан, но не оба аргумента одновременно.  
  
 [  **@schedule_name=** ] **"***schedule_name***"**  
 Имя удаляемого расписания. *schedule_name* — **sysname**, значение по умолчанию NULL.  
  
> **Примечание:** либо *schedule_id* или *schedule_name* должен быть указан, но не оба аргумента одновременно.  
  
 [ **@force_delete** =] *force_delete*  
 Указывает, будет ли процедура завершаться с ошибкой, если расписание прикреплено к заданию. *Force_delete* имеет тип bit и значение по умолчанию **0**. Когда *force_delete* — **0**, хранимая процедура завершается неудачей, если расписание прикреплено к заданию. Когда *force_delete* — **1**, расписание удаляется независимо от того, прикреплено ли оно к заданию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 По умолчанию расписание нельзя удалить, если оно прикреплено к заданию. Удаление расписания, прикрепленного к заданию, укажите значение **1** для *force_delete*. Удаление расписания не приведет к остановке запущенных заданий.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Заметьте, что владелец задания может присоединять его к расписанию и отсоединять от расписания, не являясь владельцем расписания. Однако расписание нельзя удалить, если в результате отсоединения в нем не останется ни одного задания и вызов выполняется не владельцем расписания.  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Только члены **sysadmin** роли можно удалять расписание заданий, которая принадлежит другому пользователю.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-deleting-a-schedule"></a>A. Удаление расписания  
 В данном примере удаляется расписание `NightlyJobs`. Расписание, прикрепленное к какому-либо заданию, удалено не будет.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
### <a name="b-deleting-a-schedule-attached-to-a-job"></a>Б. Удаление расписания, прикрепленного к заданию  
 В следующем примере расписание `RunOnce` удаляется независимо от того, прикреплено ли оно к заданию.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_schedule  
    @schedule_name = 'RunOnce',  
    @force_delete = 1;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Реализация заданий](../../ssms/agent/implement-jobs.md)   
 [sp_add_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)  
  
  
