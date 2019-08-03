---
title: sp_replcmds (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replcmds_TSQL
- sp_replcmds
helpviewer_keywords:
- sp_replcmds
ms.assetid: 7e932f80-cc6e-4109-8db4-2b7c8828df73
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3d60de0f459ec1224f6023e8ee848227fdc17ece
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771009"
---
# <a name="spreplcmds-transact-sql"></a>sp_replcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает команды для транзакций, помеченных для репликации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Процедуру **sp_replcmds** следует запускать только для устранения неполадок с репликацией.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @maxtrans = ] maxtrans`Число транзакций, о которых возвращаются сведения. *maxtrans* имеет **тип int**и значение по умолчанию **1**, которое указывает следующую транзакцию, ожидающую распространения.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Идентификатор статьи**|**int**|Идентификатор статьи.|  
|**partial_command**|**bit**|Показывает, частичная эта команда или нет.|  
|**команда**|**varbinary (1024)**|Значение команды.|  
|**xactid**|**binary(10)**|Идентификатор транзакции.|  
|**xact_seqno**|**varbinary (16)**|Номер последовательности транзакции.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**command_id**|**int**|Идентификатор команды в [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md).|  
|**command_type**|**int**|Тип команды.|  
|**originator_srvname**|**sysname**|Сервер, на котором была начата транзакция.|  
|**originator_db**|**sysname**|База данных, в которой была начата транзакция.|  
|**пкхаш**|**int**|Только для внутреннего применения.|  
|**originator_publication_id**|**int**|Идентификатор публикации, в которой началась транзакция.|  
|**originator_db_version**|**int**|Версия базы данных, в которой началась транзакция.|  
|**originator_lsn**|**varbinary (16)**|Указывает регистрационный номер транзакции в журнале (номер LSN) для команды в порождающей публикации.|  
  
## <a name="remarks"></a>Примечания  
 хранимая процедура **sp_replcmds** используется процессом чтения журнала в репликации транзакций.  
  
 Репликация обрабатывает первый клиент, выполняющий хранимую процедуру **sp_replcmds** в заданной базе данных, как средство чтения журнала.  
  
 Эта процедура может формировать команды для таблиц с заданным владельцем или не квалифицировать имя таблицы (по умолчанию). Дополнение квалификатора в виде имени таблицы позволяет реплицировать данные из таблиц, принадлежащих конкретному пользователю, в таблицы, принадлежащие этому же пользователю, но находящиеся в другой базе данных.  
  
> [!NOTE]  
>  Поскольку имя таблицы в базе данных-источнике квалифицируется именем владельца, владелец таблицы в базе данных назначения должен иметь то же самое имя.  
  
 Клиенты, пытающиеся запустить хранимую процедуру **sp_replcmds** в той же базе данных, получают ошибку 18752 до тех пор, пока первый клиент не отключится. После отключения первого клиента можно запустить хранимую процедуру **sp_replcmds**на другом клиенте и становиться новым средством чтения журнала.  
  
 Предупреждение с номером [!INCLUDE[msCoName](../../includes/msconame-md.md)] 18759 добавляется как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в журнал ошибок, так и в [!INCLUDE[msCoName](../../includes/msconame-md.md)] журнал приложений Windows, если хранимая команда **sp_replcmds** не может выполнить репликацию текстовой команды, так как текстовый указатель не был извлечен в том же операции.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять хранимую процедуру **sp_replcmds**.  
  
## <a name="see-also"></a>См. также  
 [Сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [хранимая процедура sp_repldone &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
