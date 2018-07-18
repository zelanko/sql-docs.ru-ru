---
title: sp_replcmds (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_replcmds_TSQL
- sp_replcmds
helpviewer_keywords:
- sp_replcmds
ms.assetid: 7e932f80-cc6e-4109-8db4-2b7c8828df73
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3690b3eaad187b341e4ad31fae1068aa56e45b05
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33001431"
---
# <a name="spreplcmds-transact-sql"></a>sp_replcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает команды для транзакций, помеченных для репликации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
> [!IMPORTANT]  
>  **Sp_replcmds** процедура должна запускаться только для устранения неполадок с репликацией.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@maxtrans=**] *maxtrans*  
 Число транзакций, сведения о которых необходимо возвратить. *maxtrans* — **int**, значение по умолчанию **1**, который указывает следующую транзакцию, ожидающую распространения.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Идентификатор статьи**|**int**|Идентификатор статьи.|  
|**partial_command**|**бит**|Показывает, частичная эта команда или нет.|  
|**команда**|**varbinary(1024)**|Значение команды.|  
|**xactid**|**binary(10)**|Идентификатор транзакции.|  
|**xact_seqno**|**varbinary(16)**|Номер последовательности транзакции.|  
|**publication_id**|**int**|Идентификатор публикации.|  
|**command_id**|**int**|Идентификатор команды в [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md).|  
|**command_type**|**int**|Тип команды.|  
|**originator_srvname**|**sysname**|Сервер, на котором была начата транзакция.|  
|**originator_db**|**sysname**|База данных, в которой была начата транзакция.|  
|**pkHash**|**int**|Только для внутреннего применения.|  
|**originator_publication_id**|**int**|Идентификатор публикации, в которой началась транзакция.|  
|**originator_db_version**|**int**|Версия базы данных, в которой началась транзакция.|  
|**originator_lsn**|**varbinary(16)**|Указывает регистрационный номер транзакции в журнале (номер LSN) для команды в порождающей публикации.|  
  
## <a name="remarks"></a>Замечания  
 **sp_replcmds** используется процессом чтения журнала в репликации транзакций.  
  
 Репликация рассматривает первого клиента, который работает **sp_replcmds** внутри конкретной базы данных, как читателя журнала.  
  
 Эта процедура может формировать команды для таблиц с заданным владельцем или не квалифицировать имя таблицы (по умолчанию). Дополнение квалификатора в виде имени таблицы позволяет реплицировать данные из таблиц, принадлежащих конкретному пользователю, в таблицы, принадлежащие этому же пользователю, но находящиеся в другой базе данных.  
  
> [!NOTE]  
>  Поскольку имя таблицы в базе данных-источнике квалифицируется именем владельца, владелец таблицы в базе данных назначения должен иметь то же самое имя.  
  
 Клиенты, пытающиеся запустить **sp_replcmds** в той же базе данных получают ошибку 18752, пока первый клиент не отключается. После отключения первого клиента, может запускаться другим клиентом **sp_replcmds**, и становится читателем журнала.  
  
 Добавляется предупреждающее сообщение 18759 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнал ошибок и [!INCLUDE[msCoName](../../includes/msconame-md.md)] журнала приложений Windows, если **sp_replcmds** не может реплицировать текстовую команду, поскольку текстовый указатель не получен в той же транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_replcmds**.  
  
## <a name="see-also"></a>См. также  
 [Сообщения об ошибках](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
