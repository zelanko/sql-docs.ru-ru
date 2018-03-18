---
title: "STSrid (тип данных geography) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STSrid (geography Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid method
ms.assetid: 6b04f5a7-2e69-4d34-901e-b61ba6ca9c14
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2adbcda7fb699fc4690e0bf9d9b21e83a121508a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="stsrid-geography-data-type"></a>STSrid (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid** является целым числом, представляющим собой идентификатор пространственной ссылки (SRID) экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STSrid  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **int**  
  
 Тип CLR: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 Это свойство можно изменять.  
  
## <a name="examples"></a>Примеры  
 В первом примере создается экземпляр `geography` со значением SRID, равным 4326 (WGS84), и используется метод `STSrid` для подтверждения SRID.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STSrid;  
```  
  
 Во втором примере с помощью метода `STSrid` значение SRID экземпляра изменяется на 4267 (NAD27), затем подтверждается измененное значение SRID.  
  
```  
SET @g.STSrid = 4267;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)   
 [Идентификаторы пространственных ссылок (SRIDs)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
  
