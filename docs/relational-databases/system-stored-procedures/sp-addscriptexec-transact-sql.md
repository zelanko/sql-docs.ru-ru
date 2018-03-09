---
title: "sp_addscriptexec (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addscriptexec
- sp_addscriptexec_TSQL
helpviewer_keywords:
- sp_addscriptexec
ms.assetid: 1627db41-6a80-45b6-b0b9-c0b7f9a1c886
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13f3104f91c785252f573e653d3344a03091dd13
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spaddscriptexec-transact-sql"></a>sp_addscriptexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отсылает SQL-скрипт (SQL-файл) всем подписчикам публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addscriptexec [ @publication = ] publication  
    [ , [ @scriptfile = ] 'scriptfile' ]  
    [ , [ @skiperror = ] 'skiperror' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=** ] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@scriptfile=** ] **"***scriptfile***"**  
 Полный путь к файлу скрипта SQL. *ScriptFile* — **nvarchar(4000)**, не имеет значения по умолчанию.  
  
 [  **@skiperror=** ] **"***skiperror***"**  
 Показывает, должен ли агент распространителя или агент слияния останавливаться при возникновении ошибки во время обработки скрипта. *SkipError* — **бит**, значение по умолчанию 0.  
  
 **0** = агент остановится.  
  
 **1** = агент пропустит ошибку и продолжит выполнение скрипта.  
  
 [  **@publisher=** ] **"***издатель***"**  
 Указывает значение, отличное от[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не должны использоваться при публикации из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_addscriptexec** используется в транзакционной репликации и репликации слиянием.  
  
 **sp_addscriptexec** не используется в репликации моментальных снимков.  
  
 Для использования **sp_addscriptexec**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетная запись службы должна чтение и запись разрешения для разрешения расположения и чтения моментальных снимков в расположении, где сценарии хранятся.  
  
 [Программы sqlcmd](../../tools/sqlcmd-utility.md) используется для выполнения сценария на стороне подписчика, и сценарий выполняется в контексте безопасности, используемый агентом распространителя или агентом слияния при подключении к базе данных подписки. При запуске агента в предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [osql, программа](../../tools/osql-utility.md) используется вместо [sqlcmd](../../tools/sqlcmd-utility.md).  
  
 **sp_addscriptexec** полезен применения скриптов к подписчикам и использует [sqlcmd](../../tools/sqlcmd-utility.md) для применения содержимое скрипта к подписчику. Однако, поскольку конфигурации подписчика могут различаться, скрипты, протестированные до отправки к издателю, могут по-прежнему вызывать ошибки у подписчика. *skiperror* предоставляет возможность агента распространителя или агенту слияния пропускать ошибки и продолжать работу. Используйте [sqlcmd](../../tools/sqlcmd-utility.md) Чтобы протестировать скрипты перед запуском **sp_addscriptexec**.  
  
> [!NOTE]  
>  Пропущенные ошибки по-прежнему будут фиксироваться в журнале агента для последующей справки.  
  
 С помощью **sp_addscriptexec** для файла скрипта для публикаций, использующих FTP для доставки моментальных снимков поддерживается только для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчиков.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_addscriptexec**.  
  
## <a name="see-also"></a>См. также:  
 [Выполнять скрипты во время синхронизации &#40; Программирование репликации Transact-SQL &#41;](../../relational-databases/replication/execute-scripts-during-synchronization-replication-transact-sql-programming.md)   
 [Синхронизация данных](../../relational-databases/replication/synchronize-data.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
