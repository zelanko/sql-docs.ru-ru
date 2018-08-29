---
title: sp_check_for_sync_trigger (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
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
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ed3cd29b694e0e87f207376ad54b06fc0827b45b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43020263"
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
 Идентификатор объекта таблицы, проверяемой на предмет немедленного обновления триггеров. *tabid* — **int** не имеет значения по умолчанию.  
  
 [ **@trigger_op =** ] "*trigger_output_parameters*" выходные данные  
 Указывает, будет ли выходной параметр возвращать тип вызывающего триггера. *trigger_output_parameters* — **char(10)** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Модули**|триггер INSERT|  
|**UPD**|триггер UPDATE|  
|**DEL**|триггер DELETE|  
|NULL (по умолчанию)||  
  
 [  **@fonpublisher =** ] *fonpublisher*  
 Указывает место выполнения хранимой процедуры. *fonpublisher* — **бит**, со значением по умолчанию 0. Если значение равно 0, тогда выполнение происходит на подписчике, а если 1, то выполнение происходит на издателе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 указывает на то, что хранимая процедура не вызывается внутри контекста немедленно обновляющегося триггера. 1 указывает, что он вызывается внутри контекста немедленно обновляющегося триггера и тип триггера записывается в аргументе *@trigger_op*.  
  
## <a name="remarks"></a>Примечания  
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
 Код можно также добавить в триггер таблицы на издателе. используемый код аналогичен, но вызов **sp_check_for_sync_trigger** содержит дополнительный параметр.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>Разрешения  
 **sp_check_for_sync_trigger** хранимая процедура может выполняться любой пользователь, обладающий разрешениями SELECT в [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) системное представление.  
  
## <a name="see-also"></a>См. также  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
