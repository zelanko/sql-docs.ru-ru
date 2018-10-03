---
title: sp_check_subset_filter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_check_TSQL
- sp_check_subset_filter
- filter
- subset
- subset_TSQL
- sp_check
- sp_check_subset_filter_TSQL
helpviewer_keywords:
- sp_check_subset_filter
ms.assetid: 525cfcfc-f317-478d-ba84-72e62285f160
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7c5c3df76ad1e2751f2997eb48899b86beb260e0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47848502"
---
# <a name="spchecksubsetfilter-transact-sql"></a>sp_check_subset_filter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используется для проверки допустимости выражения фильтра для любой таблицы. Эта хранимая процедура возвращает информацию о фильтре, включая данные о том, подходит ли данный фильтр для предварительно вычисляемых секций. Эта хранимая процедура запускается в базе данных публикаций на издателе.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_check_subset_filter [ @filtered_table = ] 'filtered_table'  
        , [ @subset_filterclause = ] 'subset_filterclause'  
    [ , [ @has_dynamic_filters = ] has_dynamic_filters OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@filtered_table**=] **"***filtered_table***"**  
 Имя фильтруемой таблицы. *filtered_table* — **nvarchar(400)**, не имеет значения по умолчанию.  
  
 [ **@subset_filterclause** =] **"***subset_filterclause***"**  
 Проверяемое предложение фильтра соединения. *subset_filterclause* — **nvarchar(1000)**, не имеет значения по умолчанию.  
  
 [ **@has_dynamic_filters**=] *has_dynamic_filters*  
 Показывает, что выражение фильтра является параметризованным фильтром строк. *has_dynamic_filters* — **бит**, значение по умолчанию NULL и является выходным параметром. Возвращает значение **1** когда выражение фильтра является параметризованным фильтром строк.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|— Если публикации предоставлено право использования предварительно вычисляемых секций; где **1** означает, что предварительно вычисляемые секции могут быть использованы, и **0** означает, что они не могут использоваться.|  
|**has_dynamic_filters**|**bit**|Если в предоставленном предложении фильтра включает по крайней мере один параметризованный фильтр строк; где **1** означает, что используется параметризованный фильтр строк, и **0** означает, что такая функция не используется.|  
|**dynamic_filters_function_list**|**nvarchar(500)**|Список функций в фильтрующем выражении, которые динамически фильтруют содержимое статьи. Функции в списке разделяются точкой с запятой.|  
|**uses_host_name**|**bit**|Если [HOST_NAME()](../../t-sql/functions/host-name-transact-sql.md) функция используется в предложении фильтрации, где **1** означает наличие этой функции.|  
|**uses_suser_sname**|**bit**|Если [SUSER_SNAME()](../../t-sql/functions/suser-sname-transact-sql.md) функция используется в предложении фильтрации, где **1** означает наличие этой функции.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_check_subset_filter** используется в репликации слиянием.  
  
 **sp_check_subset_filter** может выполняться для любой таблицы, даже если таблица не публикуется. Эта хранимая процедура может использоваться для проверки фильтрующего выражения перед определением отфильтрованной статьи.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_check_subset_filter**.  
  
## <a name="see-also"></a>См. также  
 [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)  
  
  
