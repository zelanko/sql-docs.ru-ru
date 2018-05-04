---
title: sp_check_dynamic_filters (Transact-SQL) | Документы Microsoft
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
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d3b4258d298bc6bdda45f6eae36e802facd2d23c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
|**can_use_partition_groups**|**бит**|— Если публикации предоставлено право использования предварительно вычисляемых секций; где **1** означает, что предварительно вычисляемые секции могут быть использованы, и **0** означает, что они не могут использоваться.|  
|**has_dynamic_filters**|**бит**|— Если хотя бы один параметризованный фильтр строк был определен в публикации; где **1** означает, что существует один или несколько параметризованных фильтров строк, и **0** означает, что существует нет динамических фильтров.|  
|**dynamic_filters_function_list**|**nvarchar(500)**|Список разделенных точкой с запятой функций, которые использованы для фильтрации статей в публикации.|  
|**validate_subscriber_info**|**nvarchar(500)**|Список функций, разделенных знаком «плюс» (+), которые использованы для фильтрации статей в публикации.|  
|**uses_host_name**|**бит**|Если [HOST_NAME()](../../t-sql/functions/host-name-transact-sql.md) функция используется в параметризованном фильтре строк, где **1** означает, что эта функция используется для динамической фильтрации.|  
|**uses_suser_sname**|**бит**|Если [SUSER_SNAME()](../../t-sql/functions/suser-sname-transact-sql.md) функция используется в параметризованном фильтре строк, где **1** означает, что эта функция используется для динамической фильтрации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_check_dynamic_filters** используется в репликации слиянием.  
  
 Если публикации было предусмотрено использование предварительно вычисляемых секций **sp_check_dynamic_filters** проверяет наличие любых нарушений ограничений для предварительно вычисляемых секций. При обнаружении нарушений возвращается ошибка. Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 Если в определении публикации было предусмотрено использование параметризованных фильтров строк, но ни одного фильтра не обнаружено, возвращается ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_check_dynamic_filters**.  
  
## <a name="see-also"></a>См. также  
 [Управление секциями для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)   
 [sp_check_join_filter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-check-join-filter-transact-sql.md)   
 [sp_check_subset_filter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-check-subset-filter-transact-sql.md)  
  
  
