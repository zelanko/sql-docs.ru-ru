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
ms.openlocfilehash: 8333e805c50f4b8084f8463877c361917097b547
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "70745386"
---
# <a name="sp_helpdistributor-transact-sql"></a>sp_helpdistributor (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Выводит сведения о распространителе, базе данных распространителя, рабочем каталоге и [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи агента пользователя. Эта хранимая процедура выполняется на издателе для базы данных публикации или любой базы данных.  
  
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
`[ @distributor = ] 'distributor' OUTPUT`Имя распространителя. Аргумент распространитель имеет тип **sysname**и значение **%** по умолчанию, которое является единственным значением, возвращающим результирующий набор.  
  
`[ @distribdb = ] 'distribdb' OUTPUT`Имя базы данных распространителя. *дистрибдб* имеет тип **sysname**и значение по умолчанию **%**, которое является единственным значением, возвращающим результирующий набор.  
  
`[ @directory = ] 'directory' OUTPUT`Рабочий каталог. *Каталог* имеет тип **nvarchar (255)** и значение по умолчанию **%**, которое является единственным значением, возвращающим результирующий набор.  
  
`[ @account = ] 'account' OUTPUT`— Это [!INCLUDE[msCoName](../../includes/msconame-md.md)] учетная запись пользователя Windows. *учетная запись*имеет тип **nvarchar (255)** и значение **%** по умолчанию, которое является единственным значением, возвращающим результирующий набор.  
  
`[ @min_distretention = ] _min_distretentionOUTPUT`Минимальный срок хранения распространения в часах. *min_distretention* имеет **тип int**и значение по умолчанию **-1**.  
  
`[ @max_distretention = ] _max_distretentionOUTPUT`Максимальный срок хранения распространения в часах. *max_distretention* имеет **тип int**и значение по умолчанию **-1**.  
  
`[ @history_retention = ] _history_retentionOUTPUT`Срок хранения журнала в часах. *history_retention* имеет **тип int**и значение по умолчанию **-1**.  
  
`[ @history_cleanupagent = ] 'history_cleanupagent' OUTPUT`Имя агента очистки журнала. *history_cleanupagent* имеет тип **nvarchar (100)** и значение по умолчанию **%**, которое является единственным значением, возвращающим результирующий набор.  
  
`[ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT`Имя агента очистки распространителя. *distrib_cleanupagent* имеет тип **nvarchar (100)** и значение по умолчанию **%**, которое является единственным значением, возвращающим результирующий набор.  
  
`[ @publisher = ] 'publisher'`Имя издателя. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @local = ] 'local'`Указывает, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны ли быть получены значения локального сервера. *Local* имеет тип **nvarchar (5)** и значение по умолчанию NULL.  
  
`[ @rpcsrvname = ] 'rpcsrvname' OUTPUT`Имя сервера, который выдает удаленные вызовы процедур. *рпксрвнаме* имеет тип **sysname**и значение по умолчанию **%**, которое является единственным значением, возвращающим результирующий набор.  
  
`[ @publisher_type = ] 'publisher_type' OUTPUT`Тип издателя издателя. Аргумент *publisher_type* имеет тип **sysname**и значение по **%** умолчанию, которое является единственным значением, возвращающим результирующий набор.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**распространение**|**sysname**|Имя распространителя.|  
|**база данных распространителя**|**sysname**|Имя базы данных распространителя.|  
|**каталоги**|**nvarchar(255)**|Имя рабочего каталога.|  
|**организации**|**nvarchar(255)**|Имя учетной записи пользователя Windows.|  
|**min distrib retention**|**int**|Минимальный срок хранения распространения.|  
|**max distrib retention**|**int**|Максимальный срок хранения распространения.|  
|**history retention**|**int**|Срок хранения журнала.|  
|**history cleanup agent**|**nvarchar (100)**|Имя агента очистки журнала.|  
|**distribution cleanup agent**|**nvarchar (100)**|Имя агента очистки распространителя.|  
|**rpc server name**|**sysname**|Имя удаленного или локального распространителя.|  
|**rpc login name**|**sysname**|Имя входа, используемое при удаленных вызовах процедур удаленного распространителя.|  
|**тип издателя**|**sysname**|Тип издателя; возможны следующие варианты:<br /><br /> **MSSQLSERVER**<br /><br /> **СУБД**<br /><br /> **ORACLE GATEWAY.**|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpdistributor** используется во всех типах репликации.  
  
 Если при выполнении **sp_helpdistributor**указаны один или несколько выходных параметров, то всем выходным параметрам, установленным в значение null, присваиваются значения при выходе, а результирующий набор не возвращается. Если выходных параметров нет, результирующий набор возвращается.  
  
## <a name="permissions"></a>Разрешения  
 Следующие столбцы результирующего набора или выходные параметры возвращаются членам предопределенной роли сервера **sysadmin** на издателе и предопределенной роли базы данных **db_owner** в базе данных публикации:  
  
|Столбец результирующего набора|Выходной параметр|  
|-----------------------|----------------------|  
|account|**\@учетной записи**|  
|min distrib retention|**\@min_distretention**|  
|max distrib retention|**\@max_distretention**|  
|history retention|**\@history_retention**|  
|history cleanup agent|**\@history_cleanupagent**|  
|distribution cleanup agent|**\@distrib_cleanupagent**|  
|rpc login name|none|  
  
 Пользователям из списка доступа публикации распространителя возвращается следующий столбец результирующего набора:  
  
-   directory.  
  
 Следующие столбцы результирующего набора возвращаются всем пользователям:  
  
|Столбец результирующего набора|Выходной параметр|  
|-----------------------|----------------------|  
|distributor|**\@распространение**|  
|база данных распространителя|**\@дистрибдб**|  
|rpc server name|**\@рпксрвнаме**|  
|publisher type|**\@publisher_type**|  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств распространителя и издателя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
