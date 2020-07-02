---
title: sp_delete_jobschedule (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_jobschedule
- sp_delete_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobschedule
ms.assetid: 82fbb48b-603a-4016-a7fb-1ce17fb76919
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 56d2a7cb69c838df7b11892306a00d848c6c5be4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750629"
---
# <a name="sp_delete_jobschedule-transact-sql"></a>sp_delete_jobschedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Удаляет расписание для задания.  
  
 **sp_delete_jobschedule** предоставляется только для обратной совместимости.  
  
  
## <a name="remarks"></a>Примечания  
 Расписанием задач теперь можно управлять независимо от них самих. Чтобы удалить расписание из задания, используйте **sp_detach_schedule**. Чтобы удалить расписание, используйте **sp_delete_schedule**.  
  
> **Примечание. sp_delete_jobschedule** не поддерживает расписания, присоединенные к нескольким заданиям. Если существующий скрипт вызывает **sp_delete_jobschedule** для удаления расписания, присоединенного к нескольким заданиям, процедура возвращает ошибку.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены роли **sysadmin** могут удалять любые расписания заданий. Пользователи, не являющиеся членами роли **sysadmin** , могут удалять только те расписания заданий, которыми они владеют.  
  
## <a name="see-also"></a>См. также  
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)   
 [Просмотр или изменение заданий](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_help_jobschedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobschedule-transact-sql.md)   
 [sp_update_jobschedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobschedule-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
