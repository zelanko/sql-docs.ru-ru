---
description: sp_replqueuemonitor (Transact-SQL)
title: sp_replqueuemonitor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replqueuemonitor
- sp_replqueuemonitor_TSQL
helpviewer_keywords:
- sp_replqueuemonitor
ms.assetid: 6909a3f1-43a2-4df5-a6a5-9e6f347ac841
author: markingmyname
ms.author: maghan
ms.openlocfilehash: db91c3bef035398fa98d8eeb88f68bbd1c5cf09a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534935"
---
# <a name="sp_replqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Выводит очередь сообщений из [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] очереди или [!INCLUDE[msCoName](../../includes/msconame-md.md)] очереди сообщений для подписок, обновляемых посредством очередей, в указанную публикацию. Если используются очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], эта хранимая процедура выполняется в базе данных подписки на подписчике. Если используется Message Queuing, эта хранимая процедура выполняется в базе данных распространителя на распространителе.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replqueuemonitor [ @publisher = ] 'publisher'  
    [ , [ @publisherdb = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @tranid = ] 'tranid' ]  
    [ , [ @queuetype = ] 'queuetype' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` Имя издателя. Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL. На этом сервере должна быть настроена публикация. Значение NULL означает для всех издателей.  
  
`[ @publisherdb = ] 'publisher_db' ]` Имя базы данных публикации. Аргумент *publisher_db* имеет тип **sysname**и значение по умолчанию NULL. Значение NULL означает для всех баз данных публикаций.  
  
`[ @publication = ] 'publication' ]` Имя публикации. Аргумент *publication*имеет тип **sysname**и значение по умолчанию NULL. Значение NULL означает для всех публикаций.  
  
`[ @tranid = ] 'tranid' ]` Идентификатор транзакции. *транид*имеет тип **sysname**и значение по умолчанию NULL. Значение NULL означает для всех транзакций.  
  
`[ @queuetype = ] 'queuetype' ]` Тип очереди, в которой хранятся транзакции. *значение queuetype* имеет тип **tinyint** со значением по умолчанию **0**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Все типы очередей|  
|**1**|служба очередей сообщений|  
|**2**|Очередь [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_replqueuemonitor** используется в репликации моментальных снимков или репликации транзакций с подписками, обновляемыми посредством очередей. Сообщения очереди, не содержащие команд SQL или являющиеся частью команды SQL, не отображаются.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_replqueuemonitor**.  
  
## <a name="see-also"></a>См. также:  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
