---
title: sp_check_subset_filter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
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
ms.openlocfilehash: 3c1510260a5b381b91a399984121834ca4ce30b5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771306"
---
# <a name="sp_check_subset_filter-transact-sql"></a>sp_check_subset_filter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Используется для проверки допустимости выражения фильтра для любой таблицы. Эта хранимая процедура возвращает информацию о фильтре, включая данные о том, подходит ли данный фильтр для предварительно вычисляемых секций. Эта хранимая процедура запускается в базе данных публикаций на издателе.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_check_subset_filter [ @filtered_table = ] 'filtered_table'  
        , [ @subset_filterclause = ] 'subset_filterclause'  
    [ , [ @has_dynamic_filters = ] has_dynamic_filters OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @filtered_table = ] 'filtered_table'`Имя фильтруемой таблицы. *filtered_table* имеет тип **nvarchar (400)** и не имеет значения по умолчанию.  
  
`[ @subset_filterclause = ] 'subset_filterclause'`Проверяемое предложение фильтра. *subset_filterclause* имеет тип **nvarchar (1000)** и не имеет значения по умолчанию.  
  
`[ @has_dynamic_filters = ] has_dynamic_filters`Имеет значение, если предложение фильтра является параметризованным фильтром строк. *has_dynamic_filters* является **битным**, имеет значение по умолчанию NULL и является выходным параметром. Возвращает значение **1** , если предложение фильтра является параметризованным фильтром строк.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|Имеет значение, если публикация предназначена для использования предварительно вычисленных секций; значение **1** означает, что можно использовать предварительно вычисленные секции, а **0** означает, что их нельзя использовать.|  
|**has_dynamic_filters**|**bit**|Имеет значение, если предоставляемое предложение фильтра включает по крайней мере один параметризованный фильтр строк; значение **1** означает, что используется параметризованный фильтр строк, а значение **0** означает, что такая функция не используется.|  
|**dynamic_filters_function_list**|**nvarchar (500)**|Список функций в фильтрующем выражении, которые динамически фильтруют содержимое статьи. Функции в списке разделяются точкой с запятой.|  
|**uses_host_name**|**bit**|Если в предложении фильтра используется функция [HOST_NAME ()](../../t-sql/functions/host-name-transact-sql.md) , где **1** означает, что эта функция имеется.|  
|**uses_suser_sname**|**bit**|Если в предложении фильтра используется функция [SUSER_SNAME ()](../../t-sql/functions/suser-sname-transact-sql.md) , где **1** означает, что эта функция имеется.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_check_subset_filter** используется в репликации слиянием.  
  
 **sp_check_subset_filter** можно выполнить для любой таблицы, даже если таблица не опубликована. Эта хранимая процедура может использоваться для проверки фильтрующего выражения перед определением отфильтрованной статьи.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_check_subset_filter**.  
  
## <a name="see-also"></a>См. также:  
 [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)  
  
  
