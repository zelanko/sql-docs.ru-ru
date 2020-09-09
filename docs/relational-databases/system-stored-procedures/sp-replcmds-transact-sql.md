---
description: sp_replcmds (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ec1209e23885026c4f64994d5b0605e36e6fde5d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538624"
---
# <a name="sp_replcmds-transact-sql"></a>sp_replcmds (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Возвращает команды для транзакций, помеченных для репликации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  Процедура **sp_replcmds** должна выполняться только для устранения неполадок с репликацией.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @maxtrans = ] maxtrans` Число транзакций, о которых возвращаются сведения. *maxtrans* имеет **тип int**и значение по умолчанию **1**, которое указывает следующую транзакцию, ожидающую распространения.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Идентификатор статьи**|**int**|Идентификатор статьи.|  
|**partial_command**|**bit**|Показывает, частичная эта команда или нет.|  
|**command**|**varbinary (1024)**|Значение команды.|  
|**xactid**|**binary(10)**|Идентификатор транзакции.|  
|**xact_seqno**|**varbinary (16)**|Номер последовательности транзакции.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**command_id**|**int**|Идентификатор команды в [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md).|  
|**command_type**|**int**|Тип команды.|  
|**originator_srvname**|**sysname**|Сервер, на котором была начата транзакция.|  
|**originator_db**|**sysname**|База данных, в которой была начата транзакция.|  
|**pkHash**|**int**|Только для внутреннего применения.|  
|**originator_publication_id**|**int**|Идентификатор публикации, в которой началась транзакция.|  
|**originator_db_version**|**int**|Версия базы данных, в которой началась транзакция.|  
|**originator_lsn**|**varbinary (16)**|Указывает регистрационный номер транзакции в журнале (номер LSN) для команды в порождающей публикации.|  
  
## <a name="remarks"></a>Примечания  
 **sp_replcmds** используется процессом чтения журнала в репликации транзакций.  
  
 Репликация обрабатывает первый клиент, выполняющий **sp_replcmds** в заданной базе данных как средство чтения журнала.  
  
 Эта процедура может формировать команды для таблиц с заданным владельцем или не квалифицировать имя таблицы (по умолчанию). Дополнение квалификатора в виде имени таблицы позволяет реплицировать данные из таблиц, принадлежащих конкретному пользователю, в таблицы, принадлежащие этому же пользователю, но находящиеся в другой базе данных.  
  
> [!NOTE]  
>  Поскольку имя таблицы в базе данных-источнике квалифицируется именем владельца, владелец таблицы в базе данных назначения должен иметь то же самое имя.  
  
 Клиенты, пытающиеся выполнить **sp_replcmds** в одной и той же базе данных, получают ошибку 18752 до тех пор, пока первый клиент не отключится. После отключения первого клиента другой клиент может выполнить **sp_replcmds**и станет новым средством чтения журнала.  
  
 Предупреждение с номером 18759 добавляется как в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнал ошибок, так и в [!INCLUDE[msCoName](../../includes/msconame-md.md)] журнал приложений Windows, если **sp_replcmds** не удается выполнить репликацию текстовой команды, поскольку текстовый указатель не был получен в той же транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_replcmds**.  
  
## <a name="see-also"></a>См. также  
 [Сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
