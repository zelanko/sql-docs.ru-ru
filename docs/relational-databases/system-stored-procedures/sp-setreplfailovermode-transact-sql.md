---
title: Хранимая процедура sp_setreplfailovermode (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_setreplfailovermode
- sp_setreplfailovermode_TSQL
helpviewer_keywords:
- sp_setreplfailovermode
ms.assetid: ca98a4c3-bea4-4130-88d7-79e0fd1e85f6
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 876394cf1f70aec14898a329d24504b1dc1f5878
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spsetreplfailovermode-transact-sql"></a>Хранимая процедура sp_setreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Позволяет установить режим отработки отказа для подписок, включенных для немедленного обновления с отработкой отказа с обновлением посредством очередей. Эта хранимая процедура выполняется на подписчике в базе данных подписки. Дополнительные сведения о режимах отработки отказа см. в разделе [обновляемые подписки для репликации транзакций](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_setreplfailovermode [ @publisher= ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication= ] 'publication' ]  
    [ , [ @failover_mode= ] 'failover_mode' ]  
    [ , [ @override = ] override ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publisher=**] **"***издатель***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию. Публикация уже должна существовать.  
  
 [  **@publisher_db =**] **"***publisher_db***"**  
 Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации. *Публикация*— **sysname**, не имеет значения по умолчанию.  
  
 [**@failover_mode=**] **"***failover_mode***"**  
 Режим отработки отказа для подписок. *failover_mode* — **nvarchar(10)** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**немедленное** или **синхронизации**|Изменения данных на подписчике массово копируются на издатель по мере их возникновения.|  
|**В очереди**|Изменения данных сохраняются в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] очереди.|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Служба очереди сообщений рекомендуется к использованию и больше не поддерживается.  
  
 [ **@override**=] *переопределения*  
 Только для внутреннего применения.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **Хранимая процедура sp_setreplfailovermode** используется в репликации моментальных снимков или репликации транзакций для которых подписки включены, либо обновления с переходом на немедленное обновление посредством очередей или немедленного обновления с переходом в очередь обновление.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_setreplfailovermode**.  
  
## <a name="see-also"></a>См. также  
 [Переключение между режимами обновления для обновляемой подписки транзакций](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
