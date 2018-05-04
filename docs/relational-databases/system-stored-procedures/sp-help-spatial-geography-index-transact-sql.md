---
title: sp_help_spatial_geography_index (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index
- sp_help_spatial_geography_index_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_index procedure
ms.assetid: c9bf5675-eafc-4d71-bfdb-da963384fa0c
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8fad78d619b84ccf4188bb7c67bfe85cc7d16096
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpspatialgeographyindex-transact-sql"></a>sp_help_spatial_geography_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает имена и значения для указанного набора свойств о **geography** пространственного индекса. Результат запроса возвращается в виде таблицы. Можно задать возврат основного набора свойств или всех свойств индекса.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_spatial_geography_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 В разделе [аргументов и свойств пространственного индекса хранимые процедуры](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="properties"></a>Свойства  
 В разделе [аргументов и свойств пространственного индекса хранимые процедуры](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Разрешения  
 Пользователю должна быть назначена роль PUBLIC для получения доступа к процедуре. Необходимо разрешение READ ACCESS на сервере и объекте.  
  
## <a name="remarks"></a>Замечания  
  
## <a name="example"></a>Пример  
 В следующем примере используется `sp_help_spatial_geography_index` исследовать **geography** пространственный индекс **SIndx_SpatialTable_geography_col2** определен в таблице **geography_col** для определенного образца запроса в **@qs**. Этот пример возвращает только основные свойства указанного индекса.  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
exec sp_help_spatial_geography_index 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs;  
```  
  
 Ограничивающий прямоугольник **geography** экземпляра является вся планета.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры пространственного индекса](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
