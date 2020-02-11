---
title: sp_browsereplcmds (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsereplcmds_TSQL
- sp_browsereplcmds
helpviewer_keywords:
- sp_browsereplcmds
ms.assetid: 30abcb41-1d18-4f43-a692-4c80914c0450
author: stevestein
ms.author: sstein
ms.openlocfilehash: d049a5e96d9c7212467595aa70cd44db727bdf6e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68769000"
---
# <a name="sp_browsereplcmds-transact-sql"></a>sp_browsereplcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает в пригодной для чтения версии результирующий набор реплицируемых команд, хранящихся в базе данных распространителя, и используется как инструмент диагностики. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_browsereplcmds [ [ @xact_seqno_start = ] 'xact_seqno_start' ]  
    [ , [ @xact_seqno_end = ] 'xact_seqno_end' ]   
    [ , [ @originator_id = ] 'originator_id' ]  
    [ , [ @publisher_database_id = ] 'publisher_database_id' ]  
    [ , [ @article_id = ] 'article_id' ]  
    [ , [ @command_id= ] command_id ]  
    [ , [ @agent_id = ] agent_id ]  
    [ , [ @compatibility_level = ] compatibility_level ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @xact_seqno_start = ] 'xact_seqno_start'`Указывает самый точный порядковый номер, который необходимо вернуть. *xact_seqno_start* имеет тип **nchar (22)** и значение по умолчанию 0x00000000000000000000.  
  
`[ @xact_seqno_end = ] 'xact_seqno_end'`Задает наибольший точный порядковый номер для возврата. *xact_seqno_end* имеет тип **nchar (22)** и значение по умолчанию 0xFFFFFFFFFFFFFFFFFFFF.  
  
`[ @originator_id = ] 'originator_id'`Указывает, возвращаются ли команды с указанным *originator_id* . *originator_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @publisher_database_id = ] 'publisher_database_id'`Указывает, возвращаются ли команды с указанным *publisher_database_id* . *publisher_database_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @article_id = ] 'article_id'`Указывает, возвращаются ли команды с указанным *article_id* . *article_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @command_id = ] command_id`— Это расположение команды в MSrepl_commands &#40;декодировании [&#41;Transact-SQL](../../relational-databases/system-tables/msrepl-commands-transact-sql.md) . *command_id* имеет **тип int**и значение по умолчанию NULL. Если указано, необходимо также указать все остальные параметры, а *xact_seqno_start*должны быть идентичны *xact_seqno_end*.  
  
`[ @agent_id = ] agent_id`Указывает, что возвращаются только команды для конкретного агента репликации. *agent_id* имеет **тип int**и значение по умолчанию NULL.  
  
`[ @compatibility_level = ] compatibility_level`Версия [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в которой *COMPATIBILITY_LEVEL* имеет **тип int**и значение по умолчанию 9000000.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**varbinary (16)**|Последовательный номер команды.|  
|**originator_srvname**|**имеет sysname**|Сервер, на котором была начата транзакция.|  
|**originator_db**|**имеет sysname**|База данных, в которой была начата транзакция.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**type**|**int**|Тип команды.|  
|**partial_command**|**bit**|Обозначает, является ли эта команда частичной.|  
|**hashkey**|**int**|Только для внутреннего применения.|  
|**originator_publication_id**|**int**|Идентификатор публикации, в которой началась транзакция.|  
|**originator_db_version**|**int**|Версия базы данных, в которой началась транзакция.|  
|**originator_lsn**|**varbinary (16)**|Указывает регистрационный номер транзакции в журнале (номер LSN) для команды в порождающей публикации. Используется для одноранговой репликации транзакций.|  
|**кнопки**|**nvarchar(1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)]кнопки.|  
|**command_id**|**int**|Идентификатор команды в [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md).|  
  
 Длинные команды в результирующих наборах могут быть разбиты на несколько строк.  
  
## <a name="remarks"></a>Remarks  
 **sp_browsereplcmds** используется в репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или члены предопределенных ролей базы данных **db_owner** или **replmonitor** в базе данных распространителя могут выполнять **sp_browsereplcmds**.  
  
## <a name="see-also"></a>См. также:  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
