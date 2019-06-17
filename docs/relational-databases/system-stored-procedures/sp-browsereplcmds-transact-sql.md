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
manager: craigg
ms.openlocfilehash: 7918e257428fd85ddb54867ee5144f45a3bf89f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62996368"
---
# <a name="spbrowsereplcmds-transact-sql"></a>sp_browsereplcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
`[ @xact_seqno_start = ] 'xact_seqno_start'` Указывает минимально значениями точный порядковый номер для возврата. *xact_seqno_start* — **nchar(22)** , значение по умолчанию 0x00000000000000000000.  
  
`[ @xact_seqno_end = ] 'xact_seqno_end'` Указывает наибольший точный порядковый номер для возврата. *xact_seqno_end* — **nchar(22)** , значение по умолчанию 0xFFFFFFFFFFFFFFFFFFFF.  
  
`[ @originator_id = ] 'originator_id'` Указывает, если команды с указанным *originator_id* возвращаются. *originator_id* — **int**, значение по умолчанию NULL.  
  
`[ @publisher_database_id = ] 'publisher_database_id'` Указывает, если команды с указанным *publisher_database_id* возвращаются. *publisher_database_id* — **int**, значение по умолчанию NULL.  
  
`[ @article_id = ] 'article_id'` Указывает, если команды с указанным *article_id* возвращаются. *article_id* — **int**, значение по умолчанию NULL.  
  
`[ @command_id = ] command_id` — Это расположение команды в [MSrepl_commands &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msrepl-commands-transact-sql.md) для декодирования. *command_id* — **int**, значение по умолчанию NULL. Если указан, все остальные параметры должны быть указаны также и *xact_seqno_start*должен быть идентичен *xact_seqno_end*.  
  
`[ @agent_id = ] agent_id` Указывает, что возвращены только команды для конкретного агента репликации. *agent_id* — **int**, со значением по умолчанию NULL.  
  
`[ @compatibility_level = ] compatibility_level` — Это версия [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на котором *compatibility_level* — **int**, со значением по умолчанию 9000000.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**varbinary(16)**|Последовательный номер команды.|  
|**originator_srvname**|**sysname**|Сервер, на котором была начата транзакция.|  
|**originator_db**|**sysname**|База данных, в которой была начата транзакция.|  
|**article_id**|**int**|Идентификатор статьи.|  
|**type**|**int**|Тип команды.|  
|**partial_command**|**bit**|Обозначает, является ли эта команда частичной.|  
|**hashKey**|**int**|Только для внутреннего применения.|  
|**originator_publication_id**|**int**|Идентификатор публикации, в которой началась транзакция.|  
|**originator_db_version**|**int**|Версия базы данных, в которой началась транзакция.|  
|**originator_lsn**|**varbinary(16)**|Указывает регистрационный номер транзакции в журнале (номер LSN) для команды в порождающей публикации. Используется для одноранговой репликации транзакций.|  
|**команда**|**nvarchar(1024)**|Команда языка [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|**command_id**|**int**|Идентификатор команды в [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md).|  
  
 Длинные команды в результирующих наборах могут быть разбиты на несколько строк.  
  
## <a name="remarks"></a>Примечания  
 **sp_browsereplcmds** используется в репликации транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или членами **db_owner** или **replmonitor** предопределенных ролей базы данных в базе данных распространителя могут выполнять процедуру **sp_browsereplcmds**.  
  
## <a name="see-also"></a>См. также  
 [sp_replcmds (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
