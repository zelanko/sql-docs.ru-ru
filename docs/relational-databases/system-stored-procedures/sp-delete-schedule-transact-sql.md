---
title: sp_delete_schedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_schedule
- sp_delete_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_schedule
ms.assetid: 18b2c985-47b8-49c8-82d1-8a4af3d7d33a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8fe6f851ffb3ab15781d5a2ffbbcaca3bf15829f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85862799"
---
# <a name="sp_delete_schedule-transact-sql"></a>sp_delete_schedule (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет расписание.  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_schedule { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @force_delete = ] force_delete  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @schedule_id = ] schedule_id`Идентификационный номер расписания для удаления. *schedule_id* имеет **тип int**и значение по умолчанию NULL.  
  
> **Примечание.** Необходимо указать либо *schedule_id* , либо *schedule_name* , но нельзя указать оба значения.  
  
`[ @schedule_name = ] 'schedule_name'`Имя удаляемого расписания. Аргумент *schedule_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
> **Примечание.** Необходимо указать либо *schedule_id* , либо *schedule_name* , но нельзя указать оба значения.  
  
`[ @force_delete = ] force_delete`Указывает, должна ли процедура завершаться ошибкой, если расписание присоединено к заданию. *Force_delete* имеет бит и значение по умолчанию **0**. Если *force_delete* равен **0**, хранимая процедура завершается ошибкой, если расписание присоединено к заданию. Если *force_delete* равен **1**, расписание удаляется независимо от того, присоединено ли к заданию расписание.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 По умолчанию расписание нельзя удалить, если оно прикреплено к заданию. Чтобы удалить расписание, присоединенное к заданию, укажите значение **1** для *force_delete*. Удаление расписания не приведет к остановке запущенных заданий.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Заметьте, что владелец задания может присоединять его к расписанию и отсоединять от расписания, не являясь владельцем расписания. Однако расписание нельзя удалить, если в результате отсоединения в нем не останется ни одного задания и вызов выполняется не владельцем расписания.  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Только члены роли **sysadmin** могут удалять расписание заданий, принадлежащее другому пользователю.  
  
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
  
  
