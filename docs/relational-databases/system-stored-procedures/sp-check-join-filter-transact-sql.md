---
title: sp_check_join_filter (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28589be83c62f705457e990b328be98e88905568
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771273"
---
# <a name="sp_check_join_filter-transact-sql"></a>sp_check_join_filter (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  С помощью этой процедуры проверяется правильность предложения фильтра соединения при проверке фильтра соединения двух таблиц. Кроме того, эта хранимая процедура возвращает данные о предоставленном фильтре соединения, включая сведения о том, можно ли его использовать с предварительно вычисляемыми секциями для данной таблицы. Данная хранимая процедура выполняется в публикации на издателе. Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_check_join_filter [ @filtered_table = ] 'filtered_table'  
        , [@join_table = ] 'join_table'  
        , [ @join_filterclause = ] 'join_filterclause'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @filtered_table = ] 'filtered_table'`Имя фильтруемой таблицы. *filtered_table* имеет тип **nvarchar (400)** и не имеет значения по умолчанию.  
  
`[ @join_table = ] 'join_table'`Имя таблицы, присоединяемой к *filtered_table*. *join_table* имеет тип **nvarchar (400)** и не имеет значения по умолчанию.  
  
`[ @join_filterclause = ] 'join_filterclause'`Проверяемое предложение фильтра соединений. *join_filterclause* имеет тип **nvarchar (1000)** и не имеет значения по умолчанию.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|Имеет значение, если публикация предназначена для предварительно вычисленных секций; значение **1** означает, что прекомуптед секции можно использовать, а **0** означает, что их нельзя использовать.|  
|**has_dynamic_filters**|**bit**|Имеет значение, если предоставляемое предложение фильтра включает по крайней мере одну функцию параметризованной фильтрации; где **1** означает, что используется параметризованная функция фильтрации, а значение **0** означает, что такая функция не используется.|  
|**dynamic_filters_function_list**|**nvarchar (500)**|Список функций в предложении фильтрации, определяющих параметризованный фильтр для статьи, где названия всех функций разделены точкой с запятой.|  
|**uses_host_name**|**bit**|Если в предложении фильтра используется функция [HOST_NAME ()](../../t-sql/functions/host-name-transact-sql.md) , где **1** означает, что эта функция имеется.|  
|**uses_suser_sname**|**bit**|Если в предложении фильтра используется функция [SUSER_SNAME ()](../../t-sql/functions/suser-sname-transact-sql.md) , где **1** означает, что эта функция имеется.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_check_join_filter** используется в репликации слиянием.  
  
 **sp_check_join_filter** можно выполнить для всех связанных таблиц, даже если они не опубликованы. С помощью этой хранимой процедуры можно проверять предложение фильтра соединения перед определением фильтра соединения для двух статей.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_check_join_filter**.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры репликации &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
