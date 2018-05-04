---
title: sp_check_for_sync_trigger (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a77f5bfd92ca2af52e6d8949a98e4aa24c908534
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spcheckforsynctrigger-transact-sql"></a>sp_check_for_sync_trigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет, вызывается ли пользовательский триггер или хранимая процедура в контексте триггера репликации, который используется для немедленно обновляемых подписок. Эта хранимая процедура выполняется на издателе в базе данных публикации или на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_check_for_sync_trigger [ @tabid = ] 'tabid'   
    [ , [ @trigger_op = ] 'trigger_output_parameters' OUTPUT ]  
    [ , [ @fonpublisher = ] fonpublisher ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@tabid =** ] "*tabid*"  
 Идентификатор объекта таблицы, проверяемой на предмет немедленного обновления триггеров. *tabid* — **int** без значения по умолчанию.  
  
 [ **@trigger_op =** ] "*trigger_output_parameters*" выходные данные  
 Указывает, будет ли выходной параметр возвращать тип вызывающего триггера. *trigger_output_parameters* — **char(10)** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Модули**|триггер INSERT|  
|**UPD**|триггер UPDATE|  
|**DEL**|триггер DELETE|  
|NULL (по умолчанию)||  
  
 [  **@fonpublisher =** ] *fonpublisher*  
 Указывает место выполнения хранимой процедуры. *fonpublisher* — **бит**, значение по умолчанию 0. Если значение равно 0, тогда выполнение происходит на подписчике, а если 1, то выполнение происходит на издателе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 указывает на то, что хранимая процедура не вызывается внутри контекста немедленно обновляющегося триггера. 1 показывает, что вызов происходит внутри контекста немедленно обновляющегося триггера, а тип триггера записывается в *@trigger_op*.  
  
## <a name="remarks"></a>Замечания  
 **sp_check_for_sync_trigger** используется в репликации моментальных снимков и репликации транзакций.  
  
 **sp_check_for_sync_trigger** используется для координации между репликацией и пользовательскими триггерами. Эта хранимая процедура определяет, была ли она вызвана в контексте триггера репликации. Например, можно вызвать процедуру **sp_check_for_sync_trigger** в теле определяемого пользователем триггера. Если **sp_check_for_sync_trigger** возвращает **0**, пользовательский триггер продолжает обработку. Если **sp_check_for_sync_trigger** возвращает **1**, пользовательский триггер завершает работу. Это гарантирует, что определяемый пользователем триггер не срабатывает при обновлении таблицы триггером репликации.  
  
## <a name="example"></a>Пример  
 В следующем примере показан код, который может использоваться в триггере таблицы подписчика.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int  
SELECT @table_id = object_id('tablename')  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT  
IF @retcode = 1  
RETURN  
```  
  
## <a name="example"></a>Пример  
 Код можно также добавить в триггер таблицы на издателе. Это аналогичный код, однако вызов **sp_check_for_sync_trigger** содержит дополнительный параметр.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>Разрешения  
 **sp_check_for_sync_trigger** хранимая процедура может выполняться в любой пользователь, обладающий разрешениями SELECT в [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) системного представления.  
  
## <a name="see-also"></a>См. также  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
