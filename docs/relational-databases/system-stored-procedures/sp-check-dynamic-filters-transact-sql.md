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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80cb0fbbd3c6052ebe2d129a31f582c4aa1ee1ef
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824049"
---
# <a name="sp_check_dynamic_filters-transact-sql"></a>sp_check_dynamic_filters (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Отображает сведения о свойствах параметризованного фильтра строк для публикации, в частности о функциях, использованных для формирования отфильтрованной секции данных публикации, а также о том, предоставлено ли публикации право на использование предварительно вычисляемых секций. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_check_dynamic_filters [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|Имеет значение, если публикация предназначена для использования предварительно вычисленных секций; значение **1** означает, что можно использовать предварительно вычисленные секции, а **0** означает, что их нельзя использовать.|  
|**has_dynamic_filters**|**bit**|Имеет значение, если в публикации определен хотя бы один параметризованный фильтр строк; где **1** означает, что один или несколько фильтров параметризованных строк существуют, а значение **0** означает, что динамические фильтры не существуют.|  
|**dynamic_filters_function_list**|**nvarchar (500)**|Список разделенных точкой с запятой функций, которые использованы для фильтрации статей в публикации.|  
|**validate_subscriber_info**|**nvarchar (500)**|Список функций, разделенных знаком «плюс» (+), которые использованы для фильтрации статей в публикации.|  
|**uses_host_name**|**bit**|Если функция [HOST_NAME ()](../../t-sql/functions/host-name-transact-sql.md) используется в параметризованных фильтрах строк, где **1** означает, что эта функция используется для динамической фильтрации.|  
|**uses_suser_sname**|**bit**|Если функция [SUSER_SNAME ()](../../t-sql/functions/suser-sname-transact-sql.md) используется в параметризованных фильтрах строк, где **1** означает, что эта функция используется для динамической фильтрации.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_check_dynamic_filters** используется в репликации слиянием.  
  
 Если публикация была определена для использования предварительно вычисленных секций, **sp_check_dynamic_filters** проверяет наличие нарушений ограничений предварительно вычисленных секций. При обнаружении нарушений возвращается ошибка. Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 Если в определении публикации было предусмотрено использование параметризованных фильтров строк, но ни одного фильтра не обнаружено, возвращается ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_check_dynamic_filters**.  
  
## <a name="see-also"></a>См. также  
 [Управление секциями для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)   
 [sp_check_join_filter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-check-join-filter-transact-sql.md)   
 [sp_check_subset_filter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-check-subset-filter-transact-sql.md)  
  
  
