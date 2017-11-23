---
title: "sp_delete_schedule (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
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
- sp_delete_schedule
- sp_delete_schedule_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_delete_schedule
ms.assetid: 18b2c985-47b8-49c8-82d1-8a4af3d7d33a
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b01f4f3c3487fbd9f68c899e2c9e71dae7efd0b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
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
  
 [  **@force_delete**  =] *force_delete*  
 Указывает, будет ли процедура завершаться с ошибкой, если расписание прикреплено к заданию. *Force_delete* имеет тип bit и значение по умолчанию **0**. Когда *force_delete* — **0**, хранимая процедура завершается ошибкой, если расписание прикреплено к заданию. Когда *force_delete* — **1**, расписание удаляется независимо от того, прикреплено ли оно к заданию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 По умолчанию расписание нельзя удалить, если оно прикреплено к заданию. Удаление расписания, прикрепленного к заданию, укажите значение **1** для *force_delete*. Удаление расписания не приведет к остановке запущенных заданий.  
  
## <a name="permissions"></a>Permissions  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Заметьте, что владелец задания может присоединять его к расписанию и отсоединять от расписания, не являясь владельцем расписания. Однако расписание нельзя удалить, если в результате отсоединения в нем не останется ни одного задания и вызов выполняется не владельцем расписания.  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Только члены **sysadmin** роли можно удалять расписание заданий, принадлежащее другому пользователю.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Реализация заданий](http://msdn.microsoft.com/library/69e06724-25c7-4fb3-8a5b-3d4596f21756)   
 [sp_add_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)  
  
  
