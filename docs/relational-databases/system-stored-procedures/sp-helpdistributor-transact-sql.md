---
title: "sp_helpdistributor (Transact-SQL) | Документы Microsoft"
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
- sp_helpdistributor_TSQL
- sp_helpdistributor
helpviewer_keywords:
- sp_helpdistributor
ms.assetid: 37b0983e-3b69-4f0f-977e-20efce0a0b97
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f8436c56ec260fdf2f22d5f6ecdb7a1c3102d6be
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpdistributor-transact-sql"></a>sp_helpdistributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит сведения о распространителе, базы данных распространителя, рабочем каталоге, и [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи агента. Эта хранимая процедура выполняется на издателе для базы данных публикации или любой базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdistributor [ [ @distributor= ] 'distributor' OUTPUT ]  
    [ , [ @distribdb= ] 'distribdb' OUTPUT ]  
    [ , [ @directory= ] 'directory' OUTPUT ]  
    [ , [ @account= ] 'account' OUTPUT ]  
    [ , [ @min_distretention= ] min_distretention OUTPUT ]  
    [ , [ @max_distretention= ] max_distretention OUTPUT ]  
    [ , [ @history_retention= ] history_retention OUTPUT ]  
    [ , [ @history_cleanupagent= ] 'history_cleanupagent' OUTPUT ]  
    [ , [ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @local = ] 'local' ]  
    [ , [ @rpcsrvname= ] 'rpcsrvname' OUTPUT ]  
    [ , [ @publisher_type = ] 'publisher_type' OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@distributor=**] **"***распространителя***"** выходных данных  
 Имя распространителя. Распространитель — **sysname**, значение по умолчанию  **%** , который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@distribdb=**] **"***distribdb***"** выходных данных  
 Имя базы данных распространителя. *distribdb* — **sysname**, значение по умолчанию  **%** , который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@directory=**] **"***каталога***"** выходных данных  
 Рабочий каталог. *каталог* — **nvarchar(255)**, значение по умолчанию  **%** , который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@account=**] **"***учетной записи***" выходные данные**  
 Учетная запись пользователя [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. *Учетная запись*— **nvarchar(255)**, значение по умолчанию  **%** , который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@min_distretention=**] *min_distretention***выходных данных**  
 Минимальный срок хранения распространения в часах. *min_distretention* — **int**, значение по умолчанию **-1**.  
  
 [  **@max_distretention=**] *max_distretention***выходных данных**  
 Максимальный срок хранения распространения в часах. *max_distretention* — **int**, значение по умолчанию **-1**.  
  
 [  **@history_retention=**] *history_retention***выходных данных**  
 Срок хранения истории в часах. *history_retention* — **int**, значение по умолчанию **-1**.  
  
 [  **@history_cleanupagent=**] **"***history_cleanupagent***" выходные данные**  
 Имя агента очистки журнала. *history_cleanupagent* — **nvarchar(100)**, значение по умолчанию  **%** , который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@distrib_cleanupagent =**] **"***distrib_cleanupagent***" выходные данные**  
 Имя агента очистки распространения. *distrib_cleanupagent* — **nvarchar(100)**, значение по умолчанию  **%** , который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@publisher=**] **"***издатель***"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
 [  **@local=**] **"***локального***"**  
 Указывает, должен ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получать значения локального сервера. *локальный* — **nvarchar(5)**, значение по умолчанию NULL.  
  
 [  **@rpcsrvname=**] **"***rpcsrvname***" выходные данные**  
 Имя сервера, инициирующего удаленные вызовы процедуры. *rpcsrvname* — **sysname**, значение по умолчанию  **%** , который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@publisher_type** =] **"***publisher_type***" выходные данные**  
 Тип издателя. *publisher_type* — **sysname**, значение по умолчанию  **%** , который является единственным значением, которое возвращает результирующий набор.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**распространитель**|**sysname**|Имя распространителя.|  
|**База данных распространителя**|**sysname**|Имя базы данных распространителя.|  
|**каталог**|**nvarchar(255)**|Имя рабочего каталога.|  
|**Учетная запись**|**nvarchar(255)**|Имя учетной записи пользователя Windows.|  
|**Min Распр хранения**|**int**|Минимальный срок хранения распространения.|  
|**Max Распр хранения**|**int**|Максимальный срок хранения распространения.|  
|**срок хранения журнала**|**int**|Срок хранения журнала.|  
|**агента очистки журнала**|**nvarchar(100)**|Имя агента очистки журнала.|  
|**агента очистки распространителя**|**nvarchar(100)**|Имя агента очистки распространителя.|  
|**Имя сервера RPC**|**sysname**|Имя удаленного или локального распространителя.|  
|**Имя входа RPC**|**sysname**|Имя входа, используемое при удаленных вызовах процедур удаленного распространителя.|  
|**Тип издателя**|**sysname**|Тип издателя; возможны следующие варианты:<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helpdistributor** используется во всех типах репликации.  
  
 Если один или несколько выходных параметров задаются при выполнении **sp_helpdistributor**, все выходные параметры, присваивается значение NULL, присваиваются значения при выходе и результирующий набор не возвращается. Если выходных параметров нет, результирующий набор возвращается.  
  
## <a name="permissions"></a>Permissions  
 Следующие столбцы результирующего набора или выходные параметры возвращаются членам **sysadmin** предопределенной роли сервера на издателе и **db_owner** предопределенной роли базы данных в базе данных публикации:  
  
|Столбец результирующего набора|Выходной параметр|  
|-----------------------|----------------------|  
|account|**@account**|  
|min distrib retention|**@min_distretention**|  
|max distrib retention|**@max_distretention**|  
|history retention|**@history_retention**|  
|history cleanup agent|**@history_cleanupagent**|  
|distribution cleanup agent|**@distrib_cleanupagent**|  
|rpc login name|none|  
  
 Пользователям из списка доступа публикации распространителя возвращается следующий столбец результирующего набора:  
  
-   directory.  
  
 Следующие столбцы результирующего набора возвращаются всем пользователям:  
  
|Столбец результирующего набора|Выходной параметр|  
|-----------------------|----------------------|  
|distributor|**@distributor**|  
|база данных распространителя|**@distribdb**|  
|rpc server name|**@rpcsrvname**|  
|publisher type|**@publisher_type**|  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
