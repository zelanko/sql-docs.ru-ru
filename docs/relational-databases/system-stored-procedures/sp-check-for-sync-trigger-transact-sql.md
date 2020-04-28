---
title: sp_check_for_sync_trigger (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe8cf327ff3db175c57382201ca3918a86770433
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72251242"
---
# <a name="sp_check_for_sync_trigger-transact-sql"></a>sp_check_for_sync_trigger (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Определяет, вызывается ли пользовательский триггер или хранимая процедура в контексте триггера репликации, который используется для немедленно обновляемых подписок. Эта хранимая процедура выполняется на издателе в базе данных публикации или на подписчике в базе данных подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_check_for_sync_trigger [ @tabid = ] 'tabid'   
    [ , [ @trigger_op = ] 'trigger_output_parameters' OUTPUT ]  
    [ , [ @fonpublisher = ] fonpublisher ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [**@tabid =** ] "*Табид*"  
 Идентификатор объекта таблицы, проверяемой на предмет немедленного обновления триггеров. *Табид* имеет **тип int** и не имеет значения по умолчанию.  
  
 [**@trigger_op =** ] выходные данные "*trigger_output_parameters*"  
 Указывает, будет ли выходной параметр возвращать тип вызывающего триггера. *trigger_output_parameters* имеет **тип char (10)** и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Подключаем**|триггер INSERT|  
|**Upd**|триггер UPDATE|  
|**Delete**|триггер DELETE|  
|NULL (по умолчанию)||  
  
`[ @fonpublisher = ] fonpublisher`Указывает расположение, в котором выполняется хранимая процедура. *фонпублишер* имеет **бит**и значение по умолчанию 0. Если значение равно 0, тогда выполнение происходит на подписчике, а если 1, то выполнение происходит на издателе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 указывает на то, что хранимая процедура не вызывается внутри контекста немедленно обновляющегося триггера. 1 указывает, что он вызывается в контексте немедленно обновляемого триггера и является типом триггера, возвращаемого в * \@trigger_op*.  
  
## <a name="remarks"></a>Remarks  
 **sp_check_for_sync_trigger** используется в репликации моментальных снимков и репликации транзакций.  
  
 **sp_check_for_sync_trigger** используется для координации репликации и определяемых пользователем триггеров. Эта хранимая процедура определяет, была ли она вызвана в контексте триггера репликации. Например, можно вызвать процедуру **sp_check_for_sync_trigger** в теле определяемого пользователем триггера. Если **sp_check_for_sync_trigger** возвращает **0**, определяемый пользователем триггер продолжит обработку. Если **sp_check_for_sync_trigger** возвращает **1**, то определяемый пользователем триггер завершает работу. Это гарантирует, что определяемый пользователем триггер не срабатывает при обновлении таблицы триггером репликации.  
  
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
 Код также можно добавить в триггер в таблице на издателе; код аналогичен, но вызов **sp_check_for_sync_trigger** включает дополнительный параметр.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>Разрешения  
 **sp_check_for_sync_trigger** хранимая процедура может выполняться любым пользователем с разрешениями SELECT в системном представлении [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) .  
  
## <a name="see-also"></a>См. также:  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
