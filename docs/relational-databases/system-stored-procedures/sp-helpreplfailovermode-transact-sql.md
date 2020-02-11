---
title: sp_helpreplfailovermode (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplfailovermode
- sp_helpreplfailovermode_TSQL
helpviewer_keywords:
- sp_helpreplfailovermode
ms.assetid: d1090e42-6840-4bf6-9aa9-327fd8987ec2
author: stevestein
ms.author: sstein
ms.openlocfilehash: b998a11acd71175e8868b669d9491822f60d2b33
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73632752"
---
# <a name="sp_helpreplfailovermode-transact-sql"></a>Хранимая процедура sp_helpreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает режим отработки отказа подписки. Эта хранимая процедура выполняется на подписчике в любой базе данных. Дополнительные сведения о режимах отработки отказа см. в разделе [обновляемые подписки для репликации транзакций](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpreplfailovermode [ @publisher= ] 'publisher'   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]   
    [ , [ @failover_mode_id= ] 'failover_mode_id'OUTPUT]   
    [ , [ @failover_mode = ] 'failover_mode'OUTPUT]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'`Имя издателя, участвующего в обновлении этого подписчика. параметр *Publisher* имеет тип **sysname**и не имеет значения по умолчанию. Издатель уже должен быть настроен для публикации.  
  
`[ @publisher_db = ] 'publisher_db'`Имя базы данных публикации. Аргумент *publisher_db* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @publication = ] 'publication'`Имя публикации, участвующей в обновлении этого подписчика. Аргумент *publication*имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @failover_mode_id = ] 'failover_mode_id' OUTPUT`Возвращает целочисленное значение режима отработки отказа и является **выходным** параметром. *failover_mode_id* имеет тип **tinyint** и значение по умолчанию **0**. Он возвращает **0** для немедленного обновления и **1** для обновления посредством очередей.  
  
`[ @failover_mode = ] 'failover_mode' OUTPUT`Возвращает режим, в котором изменения данных выполняются на подписчике. *FAILOVER_MODE* имеет тип **nvarchar (10)** и значение по умолчанию NULL. Параметр является **выходным** .  
  
|Значение|Description|  
|-----------|-----------------|  
|**приведен**|Немедленное обновление: изменения, выполненные на подписчике, немедленно распространяются на издатель с использованием протокола двухфазной фиксации (2PC).|  
|**в очереди**|Запрошенное обновление: изменения, выполненные на подписчике, помещаются в очередь.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpreplfailovermode** используется в репликации моментальных снимков или репликации транзакций, для которой подписки включены для немедленного обновления с обновлением посредством очереди при отработке отказа, в случае сбоя.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_helpreplfailovermode**.  
  
## <a name="see-also"></a>См. также:  
 [sp_setreplfailovermode &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)  
  
  
