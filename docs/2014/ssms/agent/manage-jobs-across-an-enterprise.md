---
title: Управление заданиями в масштабе предприятия | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3f051b3de9ba88354f5fded8cd1f429e3b277747
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52812436"
---
# <a name="manage-jobs-across-an-enterprise"></a>Управление заданиями в масштабе предприятия
  При внесении изменений в определения многосерверных задач вне среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] необходимо поместить их в список скачивания, чтобы целевые серверы могли скачать обновленную задачу. Чтобы убедиться в том, что целевые серверы получили текущие определения заданий, после обновления многосерверной задачи разместите инструкцию INSERT следующим образом:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
 Чтобы уведомить целевой сервер об изменении многосерверной задачи, необходимо выполнить указанную выше команду после использования одной из этих процедур:  
  
-   [sp_add_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [sp_update_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)  
  
-   [sp_delete_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)  
  
-   [sp_attach_schedule (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [процедуру sp_detach_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql)  
  
    > [!NOTE]  
    >  Необязательно вызывать процедуру **sp_post_msx_operation** после вызова **sp_update_job** или **sp_delete_job**, поскольку эти хранимые процедуры автоматически размещают необходимые изменения в списке скачивания.  
  
 Типичные задачи для управления задачами в масштабах предприятия:  
  
 **Проверка состояния целевого сервера**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql)  
  
-   [Управляющие объекты SQL Server (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 **Изменение целевого сервера для задания**  
  
-   [Среда SQL Server Management Studio](modify-the-target-servers-for-a-job.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  
-   [Управляющие объекты SQL Server (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 **Изменение местоположения целевого сервера**  
  
-   [Среда SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)  
  
-   [Управляющие объекты SQL Server (SMO)](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
 **Синхронизация часов целевых серверов**  
  
-   [Среда SQL Server Management Studio](synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)  
  
 **Принудительный опрос главного сервера целевым сервером**  
  
-   [Среда SQL Server Management Studio](force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)  
  
## <a name="see-also"></a>См. также  
 [Управление событиями](manage-events.md)  
  
  
