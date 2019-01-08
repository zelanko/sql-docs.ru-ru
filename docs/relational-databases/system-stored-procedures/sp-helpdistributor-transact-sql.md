---
title: sp_helpdistributor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributor_TSQL
- sp_helpdistributor
helpviewer_keywords:
- sp_helpdistributor
ms.assetid: 37b0983e-3b69-4f0f-977e-20efce0a0b97
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 63441a20a5ac4f6faed366c06fc55638073b09f4
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591398"
---
# <a name="sphelpdistributor-transact-sql"></a>sp_helpdistributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит сведения о распространителе, базе данных распространителя, рабочем каталоге, и [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи агента. Эта хранимая процедура выполняется на издателе для базы данных публикации или любой базы данных.  
  
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
 [  **@distributor=**] **"**_распространителя_**"** выходных данных  
 Имя распространителя. Распространитель — **sysname**, значение по умолчанию **%**, который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@distribdb=**] **"**_distribdb_**"** выходных данных  
 Имя базы данных распространителя. *distribdb* — **sysname**, значение по умолчанию **%**, который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@directory=**] **"**_directory_**"** выходных данных  
 Рабочий каталог. *каталог* — **nvarchar(255)**, значение по умолчанию **%**, который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@account=**] **"**_учетной записи_**" выходные данные**  
 Учетная запись пользователя [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. *Учетная запись*— **nvarchar(255)**, значение по умолчанию **%**, который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@min_distretention=**] _min_distretention_**выходных данных**  
 Минимальный срок хранения распространения в часах. *min_distretention* — **int**, значение по умолчанию **-1**.  
  
 [  **@max_distretention=**] _max_distretention_**выходных данных**  
 Максимальный срок хранения распространения в часах. *max_distretention* — **int**, значение по умолчанию **-1**.  
  
 [  **@history_retention=**] _history_retention_**выходных данных**  
 Срок хранения истории в часах. *history_retention* — **int**, значение по умолчанию **-1**.  
  
 [  **@history_cleanupagent=**] **"**_history_cleanupagent_**" выходные данные**  
 Имя агента очистки журнала. *history_cleanupagent* — **nvarchar(100)**, значение по умолчанию **%**, который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@distrib_cleanupagent =**] **"**_distrib_cleanupagent_**" выходные данные**  
 Имя агента очистки распространения. *distrib_cleanupagent* — **nvarchar(100)**, значение по умолчанию **%**, который является единственным значением, которое возвращает результирующий набор.  
  
 [  **@publisher=**] **"**_издателя_**"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
 [  **@local=**] **"**_локального_**"**  
 Указывает, должен ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получать значения локального сервера. *локальный* — **nvarchar(5)**, значение по умолчанию NULL.  
  
 [  **@rpcsrvname=**] **"**_rpcsrvname_**" выходные данные**  
 Имя сервера, инициирующего удаленные вызовы процедуры. *rpcsrvname* — **sysname**, значение по умолчанию **%**, который является единственным значением, которое возвращает результирующий набор.  
  
 [ **@publisher_type**=] **"**_publisher_type_**" выходные данные**  
 Тип издателя. *publisher_type* — **sysname**, значение по умолчанию **%**, который является единственным значением, которое возвращает результирующий набор.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**распространитель**|**sysname**|Имя распространителя.|  
|**База данных распространителя**|**sysname**|Имя базы данных распространителя.|  
|**Каталог**|**nvarchar(255)**|Имя рабочего каталога.|  
|**Учетная запись**|**nvarchar(255)**|Имя учетной записи пользователя Windows.|  
|**Min Распр хранения**|**int**|Минимальный срок хранения распространения.|  
|**Max Распр хранения**|**int**|Максимальный срок хранения распространения.|  
|**срок хранения журнала**|**int**|Срок хранения журнала.|  
|**агента очистки журнала**|**Nvarchar(100)**|Имя агента очистки журнала.|  
|**агента очистки распространителя**|**Nvarchar(100)**|Имя агента очистки распространителя.|  
|**Имя сервера RPC**|**sysname**|Имя удаленного или локального распространителя.|  
|**Имя входа RPC**|**sysname**|Имя входа, используемое при удаленных вызовах процедур удаленного распространителя.|  
|**Тип издателя**|**sysname**|Тип издателя; возможны следующие варианты:<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_helpdistributor** используется во всех типах репликации.  
  
 Если один или несколько выходных параметров указаны при выполнении **sp_helpdistributor**, все выходные параметры, присваивается значение NULL, присваиваются значения при выходе, и результирующий набор не возвращается. Если выходных параметров нет, результирующий набор возвращается.  
  
## <a name="permissions"></a>Разрешения  
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
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
