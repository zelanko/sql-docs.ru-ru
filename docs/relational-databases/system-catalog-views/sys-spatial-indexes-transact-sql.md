---
title: sys. spatial_indexes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.spatial_indexes_TSQL
- spatial_indexes
- spatial_indexes_TSQL
- sys.spatial_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_indexes catalog view
ms.assetid: 40e967d5-2e8d-45af-bf5e-5251493cf7cb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a5264661a94b4802d6f06ab1af8ae74436b63b09
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833984"
---
# <a name="sysspatial_indexes-transact-sql"></a>sys.spatial_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Представляет в главном индексе сведения о пространственных индексах.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|\<наследуемые столбцы>||Наследует столбцы из [sys. indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).|  
|spatial_index_type|**tinyint**|Тип пространственного индекса:<br /><br /> 1 = геометрический пространственный индекс<br /><br /> 2 = географический пространственный индекс|  
|spatial_index_type_desc|**nvarchar(60)**|Описание типа пространственного индекса:<br /><br /> GEOMETRY = геометрический пространственный индекс<br /><br /> GEOGRAPHY = географический пространственный индекс|  
|tessellation_scheme|**sysname**|Имя схемы тесселяции:<br /><br /> GEOMETRY_GRID, GEOMETRY_AUTO_GRID,<br /><br /> GEOGRAPHY_GRID, GEOGRAPHY_AUTO_GRID<br /><br /> Примечание. сведения о схемах тесселяции см. в разделе [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md).|  
|\<наследуемые столбцы>||Наследует столбцы из [sys. indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).<br /><br /> Унаследованные столбцы has_filter и filter_definition отображаются после столбцов, которые относятся к пространственным индексам.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также  
 [sys. Objects &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. spatial_index_tessellations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-spatial-index-tessellations-transact-sql.md)   
 [sys. indexes &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys. index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)  
  
  
