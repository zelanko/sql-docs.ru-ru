---
title: sys. pdw_permanent_table_mappings (Transact-SQL)
ms.custom: ''
ms.date: 07/24/2020
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: mstehrani
ms.author: emtehran
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 12261e8e38e75edf7dd596ca2b3499100cfff5ad
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646844"
---
# <a name="syspdw_permanent_table_mappings-transact-sql"></a>sys. pdw_permanent_table_mappings (Transact-SQL)
[!INCLUDE [applies-to-version/asa](../../includes/applies-to-version/asa.md)]

  Привязывает постоянные пользовательские таблицы к именам внутренних объектов с помощью **object_id**. Рекомендуется для повышения производительности по сравнению с **sys. pdw_table_mappings**.  
  
> [!NOTE]
> **sys. pdw_permanent_table_mappings** содержит сопоставления с постоянными таблицами и не включает сопоставления временных таблиц.

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|physical_name|**nvarchar (36)**|Физическое имя таблицы.<br /><br /> **physical_name** и **object_id** формируют ключ для этого представления.||  
|object_id|**int**|Идентификатор объекта для таблицы. См. статью [sys. objects &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **physical_name** и **object_id** формируют ключ для этого представления.||  
  
## <a name="see-also"></a>См. также  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  (Представления каталога в службе "Хранилище данных SQL" и Parallel Data Warehouse)  
 [sys. pdw_index_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)  
  
  
