---
description: Управление заданиями в масштабе предприятия
title: Управление заданиями в масштабе предприятия
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e54498ffd749417a6ae4991cfcdaeeb1c91a85d8
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036537"
---
# <a name="manage-jobs-across-an-enterprise"></a>Управление заданиями в масштабе предприятия
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

При внесении изменений в определения многосерверных заданий вне среды [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] необходимо поместить их в список скачивания, чтобы целевые серверы могли снова скачать обновленную задачу. Чтобы убедиться в том, что целевые серверы получили текущие определения заданий, после обновления многосерверной задачи разместите инструкцию INSERT следующим образом:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
Чтобы уведомить целевой сервер об изменении многосерверной задачи, необходимо выполнить указанную выше команду после использования одной из этих процедур:  
  
-   [sp_add_jobstep (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
-   [sp_update_jobstep (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)  
  
-   [sp_delete_jobstep (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)  
  
-   [Управление событиями](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
-   [sp_detach_schedule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
    > [!NOTE]  
    > Необязательно вызывать процедуру **sp_post_msx_operation** после вызова **sp_update_job** или **sp_delete_job**, поскольку эти хранимые процедуры автоматически размещают необходимые изменения в списке скачивания.  
  
Типичные задачи для управления задачами в масштабах предприятия:  
  
**Проверка состояния целевого сервера**  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql.md)  
  
-   [Управляющие объекты SQL Server (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
**Изменение целевого сервера для задания**  
  
-   [Среда SQL Server Management Studio](../../ssms/agent/modify-the-target-servers-for-a-job.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)  
  
-   [Управляющие объекты SQL Server (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
**Изменение местоположения целевого сервера**  
  
-   [Среда SQL Server Management Studio](../../ssms/agent/specify-a-target-server-s-location-sql-server-management-studio.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql.md)  
  
-   [Управляющие объекты SQL Server (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
**Синхронизация часов целевых серверов**  
  
-   [Среда SQL Server Management Studio](../../ssms/agent/synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)  
  
**Принудительный опрос главного сервера целевым сервером**  
  
-   [Среда SQL Server Management Studio](../../ssms/agent/force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
[Управление событиями](../../ssms/agent/manage-events.md)  
