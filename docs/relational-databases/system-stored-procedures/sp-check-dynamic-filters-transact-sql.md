---
title: sp_check_dynamic_filters (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- dynamic_filters_TSQL
- sp_check_TSQL
- check
- sp_check_dynamic filter
- check_TSQL
- filters_TSQL
- check_dynamic_filters_TSQL
- dynamic filters
- filters
- check dynamic filters
- sp_check_dynamic filter_TSQL
- sp_check_for_sync_trigger_TSQL
- sp_check
helpviewer_keywords:
- sp_check_dynamic_filters
ms.assetid: dd7760db-a3a5-460f-bd97-b8d436015e19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 979b61238b6d4f8faa39c90e116434426321273f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52811446"
---
# <a name="spcheckdynamicfilters-transact-sql"></a>sp_check_dynamic_filters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения о свойствах параметризованного фильтра строк для публикации, в частности о функциях, использованных для формирования отфильтрованной секции данных публикации, а также о том, предоставлено ли публикации право на использование предварительно вычисляемых секций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_check_dynamic_filters [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publication**=] **"***публикации***"**  
 Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|— Если публикации предоставлено право использования предварительно вычисляемых секций; где **1** означает, что предварительно вычисляемые секции могут быть использованы, и **0** означает, что они не могут использоваться.|  
|**has_dynamic_filters**|**bit**|— Если хотя бы один параметризованный фильтр строк был определен в публикации; где **1** означает, что существует один или несколько параметризованных фильтров строк, и **0** означает, что существует нет динамических фильтров.|  
|**dynamic_filters_function_list**|**nvarchar(500)**|Список разделенных точкой с запятой функций, которые использованы для фильтрации статей в публикации.|  
|**validate_subscriber_info**|**nvarchar(500)**|Список функций, разделенных знаком «плюс» (+), которые использованы для фильтрации статей в публикации.|  
|**uses_host_name**|**bit**|Если [HOST_NAME()](../../t-sql/functions/host-name-transact-sql.md) функция используется в параметризованном фильтре строк, где **1** означает, что эта функция используется для динамической фильтрации.|  
|**uses_suser_sname**|**bit**|Если [SUSER_SNAME()](../../t-sql/functions/suser-sname-transact-sql.md) функция используется в параметризованном фильтре строк, где **1** означает, что эта функция используется для динамической фильтрации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_check_dynamic_filters** используется в репликации слиянием.  
  
 Если публикации было предусмотрено использование предварительно вычисляемых секций **sp_check_dynamic_filters** выявляет нарушения ограничений для предварительно вычисляемых секций. При обнаружении нарушений возвращается ошибка. Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 Если в определении публикации было предусмотрено использование параметризованных фильтров строк, но ни одного фильтра не обнаружено, возвращается ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_check_dynamic_filters**.  
  
## <a name="see-also"></a>См. также  
 [Управление секциями для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)   
 [sp_check_join_filter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-check-join-filter-transact-sql.md)   
 [sp_check_subset_filter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-check-subset-filter-transact-sql.md)  
  
  
