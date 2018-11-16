---
title: sp_help_spatial_geometry_index (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geometry_index
- sp_help_spatial_geometry_index_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geometry_index procedure
ms.assetid: f1bcefb1-09c8-4b49-8c51-5d471065849f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: dcdbc24f817ec618b0d89ec8c9a4128bbd604f33
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51658403"
---
# <a name="sphelpspatialgeometryindex-transact-sql"></a>sp_help_spatial_geometry_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает имена и значения для указанного набора свойств о **geometry** пространственного индекса. Результат запроса возвращается в виде таблицы. Можно задать возврат основного набора свойств или всех свойств индекса.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_spatial_geometry_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput'   
     [ , [ @query_sample = ] 'query_sample']   
```  
  
## <a name="arguments"></a>Аргументы  
 См. в разделе [аргументов и свойств пространственного индекса хранимых процедур](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 См. в разделе [аргументов и свойств пространственного индекса хранимых процедур](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Разрешения  
 Пользователю должна быть назначена роль PUBLIC для получения доступа к процедуре. Необходимо разрешение READ ACCESS на сервере и объекте.  
  
## <a name="remarks"></a>Примечания  
 Свойства, которые содержат значения NULL, не включаются в набор возвращаемых значений.  
  
## <a name="example"></a>Пример  
 В следующем примере используется `sp_help_spatial_geometry_index` для анализа пространственного индекса **SIndx_SpatialTable_geometry_col2** определен в таблице **geometry_col** для определенного образца запроса в **@qs**. Этот пример возвращает только основные свойства указанного индекса.  
  
```  
declare @qs geometry  
        ='POLYGON((-90.0 -180.0, -90.0 180.0, 90.0 180.0, 90.0 -180.0, -90.0 -180.0))';  
exec sp_help_spatial_geometry_index 'geometry_col', 'SIndx_SpatialTable_geometry_col2', 0, @qs;  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры пространственного индекса](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geometry_index_xml](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)   
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
