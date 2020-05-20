---
title: sp_replmonitorsubscriptionpendingcmds (T-SQL)
description: Описывает sp_replmonitorsubscriptionpendingcmds хранимую процедуру, которая возвращает сведения о количестве ожидающих выполнения команд для подписки на публикацию транзакций.
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorsubscriptionpendingcmds_TSQL
- sp_replmonitorsubscriptionpendingcmds
helpviewer_keywords:
- sp_replmonitorsubscriptionpendingcmds
ms.assetid: df5b955a-feb0-4863-9b3b-7f71e9653b3d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4f2f0888daf214e91127e8caed3c3bbb04424f0a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82817187"
---
# <a name="sp_replmonitorsubscriptionpendingcmds-transact-sql"></a>sp_replmonitorsubscriptionpendingcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает сведения о количестве ожидающих выполнения команд для подписки на публикацию транзакциями и грубую оценку времени, требуемого для их выполнения. Эта хранимая процедура возвращает одну строку для каждой возвращенной подписки. Эта хранимая процедура, используемая для наблюдения за репликацией, выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replmonitorsubscriptionpendingcmds [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @subscriber_db = ] 'subscriber_db'   
        , [ @subscription_type = ] subscription_type  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя издателя. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publisher_db = ] 'publisher_db'`Имя опубликованной базы данных. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @subscriber = ] 'subscriber'`Имя подписчика. Аргумент *Subscriber* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @subscriber_db = ] 'subscriber_db'`Имя базы данных подписки. Аргумент *subscriber_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @subscription_type = ] subscription_type`Тип подписки. *publication_type* имеет **тип int**, не имеет значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Принудительная подписка|  
|**1**|Подписка по запросу|  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**pendingcmdcount**|**int**|Число команд для подписки, ожидающих завершения|  
|**estimatedprocesstime**|**int**|Примерное количество секунд, необходимых для доставки всех ожидающих команд подписчику.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_replmonitorsubscriptionpendingcmds** используется с репликацией транзакций.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** на распространителе или члены предопределенной роли базы данных **db_owner** в базе данных распространителя могут выполнять **sp_replmonitorsubscriptionpendingcmds**. Члены списка доступа к публикации для публикации, использующей базу данных распространителя, могут выполнять **sp_replmonitorsubscriptionpendingcmds** для возврата ожидающих команд для этой публикации.  
  
## <a name="see-also"></a>См. также  
 [Программный мониторинг репликации](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
