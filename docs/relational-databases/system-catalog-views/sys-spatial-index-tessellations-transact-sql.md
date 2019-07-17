---
title: sys.spatial_index_tessellations (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- spatial_index_tessellations
- sys.spatial_index_tessellations_TSQL
- spatial_index_tessellations_TSQL
- sys.spatial_index_tessellations
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_index_tessellations catalog view
ms.assetid: 8b17a9a4-b57f-4220-8138-fc73581b1670
author: stevestein
ms.author: sstein
ms.openlocfilehash: c4f2f4b8ea0184d063a6423f27fdf2cf9c450a05
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68078650"
---
# <a name="sysspatialindextessellations-transact-sql"></a>sys.spatial_index_tessellations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

 Представляет сведения о схеме тесселяции и параметрах каждого пространственного индекса.  
  
> [!NOTE]  
>  Сведения о тесселяции в см. в разделе [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md).  
  

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Идентификатор объекта, на котором определен индекс. Каждый (object_id, index_id) пары имеет соответствующую запись [sys.spatial_indexes](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md).|  
|index_id|**int**|Идентификатор пространственного индекса, в котором определен столбец.|  
|tessellation_scheme|**sysname**|Имя схемы тесселяции, один из: GEOMETRY_GRID GEOGRAPHY_GRID|  
|bounding_box_xmin|**float(53)**|Координата по оси X нижнего левого угла ограничивающего прямоугольника, один из: NULL = неприменимо для заданной схемы тесселяции (например, GEOGRAPHY_GRID) *n* =, если параметр tessellation_scheme имеет значение x-min GEOMETRY_GRID.                     **Примечание.** Координаты, определяемые параметрами ограничивающего поле интерпретируются для каждого объекта в соответствии с его [идентификатор пространственной ссылки (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).|  
|bounding_box_ymin|**float(53)**|Координата по оси Y нижнего левого угла ограничивающего прямоугольника, один из: NULL = неприменимо для заданной схемы тесселяции (например, GEOGRAPHY_GRID) *n* =, если параметр tessellation_scheme имеет значение y-min GEOMETRY_GRID|  
|bounding_box_xmax|**float(53)**|Координата по оси X в правом верхнем углу ограничивающего прямоугольника, один из: NULL = неприменимо для заданной схемы тесселяции (например, GEOGRAPHY_GRID) *n* =, если параметр tessellation_scheme имеет значение GEOMETRY_GRID, значение координаты x-max|  
|bounding_box_ymax|**float(53)**|Координата Y верхнего правого угла ограничивающего прямоугольника, один из: NULL = неприменимо для заданной схемы тесселяции (например, GEOGRAPHY_GRID) *n* =, если параметр tessellation_scheme имеет значение GEOMETRY_GRID, значение координаты y-max|  
|level_1_grid|**smallint**|Плотность сетки верхнего уровня. Если параметр tessellation_scheme имеет значение GEOMETRY_GRID или GEOGRAPHY_GRID, один из:          16 = сетка 4 на 4 (LOW) 64 = 8 службой "Сетка"-8 (MEDIUM) 256 = 16 службой "Сетка"-16 (ВЫСОКАЯ) NULL = неприменимо для заданного пространственный индекс типа или схемы тесселяции.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_1_grid_desc|**nvarchar(60)**|Плотность сетки верхнего уровня, один из: НИЗКИЙ средний высокой NULL = неприменимо для заданного пространственный индекс типа или схемы тесселяции.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_2_grid|**smallint**|Плотность сетки второго уровня. Если параметр tessellation_scheme имеет значение GEOMETRY_GRID или GEOGRAPHY_GRID, один из: 16 = сетка 4 на 4 (LOW) 64 = 8 службой "Сетка"-8 (MEDIUM) 256 = 16 службой "Сетка"-16 (ВЫСОКАЯ) NULL = неприменимо для заданного пространственный индекс типа или схемы тесселяции.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_2_grid_desc|**nvarchar(60)**|Плотность сетки второго уровня, один из: НИЗКИЙ средний высокой NULL = неприменимо для заданного пространственный индекс типа или схемы тесселяции.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_3_grid|**smallint**|Плотность сетки третьего уровня.   Если параметр tessellation_scheme имеет значение GEOMETRY_GRID или GEOGRAPHY_GRID, один из: 16 = сетка 4 на 4 (LOW) 64 = 8 службой "Сетка"-8 (MEDIUM) 256 = 16 службой "Сетка"-16 (ВЫСОКАЯ) NULL = неприменимо для заданного пространственный индекс типа или схемы тесселяции.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_3_grid_desc|**nvarchar(60)**|Плотность сетки третьего уровня, один из: LOW средний высокой NULL = неприменимо для заданного пространственный индекс типа или схемы тесселяции.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_4_grid|**smallint**|Плотность сетки четвертого уровня. Если параметр tessellation_scheme имеет значение GEOMETRY_GRID или GEOGRAPHY_GRID, один из: 16 = сетка 4 на 4 (LOW) 64 = 8 службой "Сетка"-8 (MEDIUM) 256 = 16 службой "Сетка"-16 (ВЫСОКАЯ) NULL = неприменимо для заданного пространственный индекс типа или схемы тесселяции.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|level_4_grid_desc|**nvarchar(60)**|Плотность сетки четвертого уровня, один из: < НИЗКИМ средний высокой NULL = неприменимо для заданного пространственный индекс типа или схемы тесселяции.  NULL возвращается в том случае, когда используется новая тесселяция SQL Server 11.|  
|cells_per_object|**int**|Число ячеек на пространственный объект, один из: Если параметр tessellation_scheme имеет значение GEOMETRY_GRID или geography_grid, то *n* — число ячеек на объект NULL = неприменимо для заданного пространственный индекс типа или схемы тесселяции|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Представления каталога объектов (Transact-SQL)](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.spatial_indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
