---
title: sp_replqueuemonitor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_replqueuemonitor
- sp_replqueuemonitor_TSQL
helpviewer_keywords:
- sp_replqueuemonitor
ms.assetid: 6909a3f1-43a2-4df5-a6a5-9e6f347ac841
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 438e00700e62306e28cc25fbdcb1ae62c490a2cd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751412"
---
# <a name="spreplqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Перечисляет сообщения из очереди [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] очереди или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing для очереди обновляемых подписок на указанную публикацию. Если используются очереди [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], эта хранимая процедура выполняется в базе данных подписки на подписчике. Если используется Message Queuing, эта хранимая процедура выполняется в базе данных распространителя на распространителе.  
  
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
 [ **@publisher** =] **"***издателя***"**  
 Имя издателя. *издатель* — **sysname**, значение по умолчанию NULL. На этом сервере должна быть настроена публикация. Значение NULL означает для всех издателей.  
  
 [ **@publisherdb** =] **"***publisher_db***"** ]  
 Имя базы данных публикации. *publisher_db* — **sysname**, значение по умолчанию NULL. Значение NULL означает для всех баз данных публикаций.  
  
 [ **@publication** =] **"***публикации***"** ]  
 Имя публикации. *Публикация*— **sysname**, значение по умолчанию NULL. Значение NULL означает для всех публикаций.  
  
 [ **@tranid** =] **"***tranid***"** ]  
 Идентификатор транзакции. *tranid*— **sysname**, значение по умолчанию NULL. Значение NULL означает для всех транзакций.  
  
 [**@queuetype=** ] **"***значение queuetype***"** ]  
 Тип очереди, в которой хранятся транзакции. *значение queuetype* — **tinyint** значение по умолчанию **0**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Все типы очередей|  
|**1**|служба очередей сообщений|  
|**2**|Очередь [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_replqueuemonitor** используется в репликации моментальных снимков или репликации транзакций с обновления подписок посредством очередей. Сообщения очереди, не содержащие команд SQL или являющиеся частью команды SQL, не отображаются.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_replqueuemonitor**.  
  
## <a name="see-also"></a>См. также  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
