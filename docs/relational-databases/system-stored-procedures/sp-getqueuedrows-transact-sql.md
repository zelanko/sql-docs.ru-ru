---
title: sp_getqueuedrows (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- sp_getqueuedrows_TSQL
- sp_getqueuedrows
helpviewer_keywords:
- sp_getqueuedrows
ms.assetid: 139e834f-1988-4b4d-ac81-db1f89ea90e8
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 7ec0e31b852a1aea3cfd964a47660fd4953c196d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spgetqueuedrows-transact-sql"></a>sp_getqueuedrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Извлекает строки на подписчике, имеющие отложенные обновления в очереди. Эта хранимая процедура выполняется на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_getqueuedrows [ @tablename = ] 'tablename'  
    [ , [ @owner = ] 'owner'  
    [ , [ @tranid = ] 'transaction_id' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@tablename =**] **"***tablename***"**  
 Имя таблицы. *TableName* — **sysname**, не имеет значения по умолчанию. Таблица должна быть частью очереди подписок.  
  
 [  **@owner =**] **"***владельца***"**  
 Владелец подписки. *владелец* — **sysname**, значение по умолчанию NULL.  
  
 [  **@tranid =** ] **"***transaction_id***"**  
 Позволяет осуществлять фильтрацию вывода по идентификатору транзакции. *transaction_id* — **nvarchar(70)**, значение по умолчанию NULL. Если указан, будет отображен идентификатор транзакции, связанный с командой в очереди. Если указать значение NULL, будут отображены все команды в очереди.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Показывает все строки, которые в настоящее время имеют по крайней мере одну транзакцию в очереди для подписанной таблицы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Действие**|**nvarchar(10)**|Тип операции для выполнения при синхронизации.<br /><br /> INS= вставка.<br /><br /> DEL = удаление.<br /><br /> UPD = обновление.|  
|**Tranid**|**nvarchar(70)**|Идентификатор транзакции, под которым выполнялась команда.|  
|**Таблица column1... n**||Значение для каждого столбца таблицы, указанной в *tablename*.|  
|**MSrepl_tran_version**|**uniqueidentifier**|Этот столбец используется для отслеживания изменений для реплицируемых данных и для обнаружения конфликтов на издателе. Этот столбец добавлен к таблице автоматически.|  
  
## <a name="remarks"></a>Замечания  
 **sp_getqueuedrows** используется на подписчиках, участвующих в очереди обновлений.  
  
 **sp_getqueuedrows** находит строки данной таблицы по подписке базы данных, которые участвовали в очереди обновления, но в настоящее время не были разрешены агентом чтения очереди.  
  
## <a name="permissions"></a>Разрешения  
 **sp_getqueuedrows** требуются разрешения SELECT на таблицу, указанную в *tablename*.  
  
## <a name="see-also"></a>См. также  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Обнаружение и разрешение конфликтов обновлений посредством очередей](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
