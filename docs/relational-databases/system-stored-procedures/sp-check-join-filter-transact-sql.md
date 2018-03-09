---
title: "sp_check_join_filter (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- filter_TSQL
- sp_check_TSQL
- sp_check_join_filter
- sp_check_join_filter_TSQL
- join
- join_TSQL
- filter
- sp_check
helpviewer_keywords:
- sp_check_join_filter
ms.assetid: e9699d59-c8c9-45f6-a561-f7f95084a540
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ab650e6465ac5c872e90acc890a83d17f286b446
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spcheckjoinfilter-transact-sql"></a>sp_check_join_filter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  С помощью этой процедуры проверяется правильность предложения фильтра соединения при проверке фильтра соединения двух таблиц. Кроме того, эта хранимая процедура возвращает данные о предоставленном фильтре соединения, включая сведения о том, можно ли его использовать с предварительно вычисляемыми секциями для данной таблицы. Данная хранимая процедура выполняется в публикации на издателе. Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_check_join_filter [ @filtered_table = ] 'filtered_table'  
        , [@join_table = ] 'join_table'  
        , [ @join_filterclause = ] 'join_filterclause'  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@filtered_table** =] **"***filtered_table***"**  
 Имя фильтруемой таблицы. *filtered_table* — **nvarchar(400)**, не имеет значения по умолчанию.  
  
 [  **@join_table** =] **"***join_table***"**  
 Имя таблицы, соединяемой *filtered_table*. *join_table* — **nvarchar(400)**, не имеет значения по умолчанию.  
  
 [  **@join_filterclause**  =] **"***join_filterclause***"**  
 Проверяемое предложение фильтра соединения. *join_filterclause* — **nvarchar(1000)**, не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|— Если у публикации прав на использование предварительно вычисляемых секций; где **1** означает, что разрешено может использоваться, и **0** означает, что они не могут использоваться.|  
|**has_dynamic_filters**|**bit**|Если в предоставленном предложении фильтра включает по крайней мере одной функции параметризованной фильтрации. где **1** = параметризованная функция фильтрации используется, и **0** означает, что такая функция не используется.|  
|**dynamic_filters_function_list**|**nvarchar(500)**|Список функций в предложении фильтрации, определяющих параметризованный фильтр для статьи, где названия всех функций разделены точкой с запятой.|  
|**uses_host_name**|**bit**|Если [HOST_NAME()](../../t-sql/functions/host-name-transact-sql.md) функция используется в предложении фильтрации, где **1** означает наличие этой функции.|  
|**uses_suser_sname**|**bit**|Если [SUSER_SNAME()](../../t-sql/functions/suser-sname-transact-sql.md) функция используется в предложении фильтрации, где **1** означает наличие этой функции.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_check_join_filter** используется в репликации слиянием.  
  
 **sp_check_join_filter** можно выполнять для любых связанных таблиц, даже если они не опубликованы. С помощью этой хранимой процедуры можно проверять предложение фильтра соединения перед определением фильтра соединения для двух статей.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_check_join_filter**.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
