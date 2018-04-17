---
title: Хранимая процедура sp_helpreplfailovermode (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- sp_helpreplfailovermode
- sp_helpreplfailovermode_TSQL
helpviewer_keywords:
- sp_helpreplfailovermode
ms.assetid: d1090e42-6840-4bf6-9aa9-327fd8987ec2
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dd85f6f45b7104c73b83b08d6fc434eb14e9c70b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpreplfailovermode-transact-sql"></a>Хранимая процедура sp_helpreplfailovermode (Transact-SQL)
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
 [  **@publisher=**] **"***издатель***"**  
 Имя издателя, участвующего в обновлении этого подписчика. *издатель* — **sysname**, не имеет значения по умолчанию. Издатель уже должен быть настроен для публикации.  
  
 [  **@publisher_db =**] **"***publisher_db***"**  
 Имя базы данных публикации. *publisher_db* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации, участвующей в обновлении этого подписчика. *Публикация*— **sysname**, не имеет значения по умолчанию.  
  
 [  **@failover_mode_id=**] **"***failover_mode_id***" выходные данные**  
 Возвращает целочисленное значение режима отработки отказа и является **ВЫВОДА** параметра. *failover_mode_id* — **tinyint** значение по умолчанию **0**. Он возвращает **0** для немедленного обновления и **1** обновления посредством очередей.  
  
 [**@failover_mode=**] **"***failover_mode***" выходные данные**  
 Возвращает режим, в котором выполняются изменения данных на подписчике. *failover_mode* — **nvarchar(10)** значение по умолчанию NULL. — **ВЫВОДА** параметра.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Немедленно**|Немедленное обновление: изменения, выполненные на подписчике, немедленно распространяются на издатель с использованием протокола двухфазной фиксации (2PC).|  
|**В очереди**|Запрошенное обновление: изменения, выполненные на подписчике, помещаются в очередь.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **Хранимая процедура sp_helpreplfailovermode** используется в репликации моментальных снимков или репликации транзакций, для которых подписки включены для немедленного обновления с обновлением посредством очередей при отработке отказа в случае сбоя.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_helpreplfailovermode**.  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_setreplfailovermode &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md)  
  
  
