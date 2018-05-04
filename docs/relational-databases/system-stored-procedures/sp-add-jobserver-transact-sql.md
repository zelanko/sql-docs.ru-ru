---
title: sp_add_jobserver (Transact-SQL) | Документы Microsoft
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
- sp_add_jobserver
- sp_add_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobserver
ms.assetid: 485252cc-0081-490a-9bd1-cbbd68eea286
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 81f1550fbe056932ca6dbeebd709df4afa9d3a39
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spaddjobserver-transact-sql"></a>sp_add_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отправляет указанное задание на указанный сервер.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_jobserver [ @job_id = ] job_id | [ @job_name = ] 'job_name'  
     [ , [ @server_name = ] 'server' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_id =** ] *job_id*  
 Идентификационный номер задания. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name =** ] **"***job_name***"**  
 Имя задания. *job_name* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
 [ **@server_name =** ] **'***server***'**  
 Имя сервера, на который направляется задание. *сервер* — **nvarchar(30)**, значение по умолчанию N'(LOCAL)'. *сервер*может быть либо **(LOCAL)** для локального сервера или имя существующего целевого сервера.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **@automatic_post** существует в **sp_add_jobserver**, но отсутствует в списке аргументов. **@automatic_post** Зарезервировано для внутреннего использования.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] обеспечивает доступный графический способ управления заданиями и рекомендуется для создания и управления инфраструктурой заданий.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Только члены **sysadmin** предопределенной роли сервера могут выполнять **sp_add_jobserver** для заданий, использующих несколько серверов.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-assigning-a-job-to-the-local-server"></a>A. Назначение заданий локальному серверу  
 В следующем примере задание `NightlyBackups` назначается для выполнения на локальном сервере.  
  
> [!NOTE]  
>  В этом примере предполагается, что задание `NightlyBackups` уже существует.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-assigning-a-job-to-run-on-a-different-server"></a>Б. Назначение выполнения заданий на другом сервере  
 В следующем примере назначается выполнение многосерверного задания `Weekly Sales Backups` на сервере `SEATTLE2`.  
  
> [!NOTE]  
>  В этом примере подразумевается, что задание `Weekly Sales Backups` уже существует, и что `SEATTLE2` зарегистрирован в качестве целевого сервера текущего экземпляра.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',  
    @server_name = N'SEATTLE2' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_apply_job_to_targets &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
