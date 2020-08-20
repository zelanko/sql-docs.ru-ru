---
description: sp_stop_job (Transact-SQL)
title: sp_stop_job (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_stop_job_TSQL
- sp_stop_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_stop_job
ms.assetid: 64b4cc75-99a0-421e-b418-94e37595bbb0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2314cec4cbb66893eb77ed6c8b025355c319de71
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473692"
---
# <a name="sp_stop_job-transact-sql"></a>sp_stop_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Дает указание агенту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] остановить выполнение текущего задания.  

  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_stop_job   
      [@job_name =] 'job_name'  
    | [@job_id =] job_id   
    | [@originating_server =] 'master_server'  
    | [@server_name =] 'target_server'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_name = ] 'job_name'` Имя останавливаемого задания. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @job_id = ] job_id` Идентификационный номер останавливаемого задания. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @originating_server = ] 'master_server'` Имя главного сервера. Если указано, останавливаются все многосерверные задания. *master_server* имеет тип **nvarchar (128)** и значение по умолчанию NULL. Этот параметр следует указывать только при вызове **sp_stop_job** на целевом сервере.  
  
> [!NOTE]  
>  Может быть задан только один из первых трех аргументов.  
  
`[ @server_name = ] 'target_server'` Имя конкретного целевого сервера, на котором необходимо отключить многосерверное задание. *target_server* имеет тип **nvarchar (128)** и значение по умолчанию NULL. Этот параметр следует указывать только при вызове **sp_stop_job** на главном сервере для многосерверного задания.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 **sp_stop_job** отправляет сигнал об ошибке в базу данных. Некоторые процессы можно немедленно остановить, и некоторые из них должны достичь стабильной точки (или точки входа в путь к коду), прежде чем их можно будет остановить. Для завершения некоторых длительных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)], таких как BACKUP, RESTORE, и некоторых команд DBCC может потребоваться много времени. При их выполнении может потребоваться некоторое время, прежде чем задание будет отменено. Остановка задания приведет к регистрации записи «Задание отменено» в журнале заданий.  
  
 Если задание в данный момент выполняет шаг типа **CmdExec** или **PowerShell**, то выполняемый процесс (например, MyProgram.exe) принудительно завершается преждевременно. Преждевременное завершение может привести к непредсказуемому поведению, например файлы, используемые процессом, могут остаться открытыми. Следовательно, **sp_stop_job** следует использовать только в крайних обстоятельствах, если задание содержит шаги типа **CmdExec** или **PowerShell**.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Члены **SQLAgentUserRole** и **SQLAgentReaderRole** могут прекращать только те задания, которыми они владеют. Члены **SQLAgentOperatorRole** могут прекращать все локальные задания, включая те, которые принадлежат другим пользователям. Члены **роли sysadmin** могут прекращать выполнение всех локальных и многосерверных заданий.  
  
## <a name="examples"></a>Примеры  
 В следующем примере останавливается задание с именем `Weekly Sales Data Backup`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_stop_job  
    N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_delete_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
