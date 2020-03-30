---
title: STSrid (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STSrid (geography Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid method
ms.assetid: 6b04f5a7-2e69-4d34-901e-b61ba6ca9c14
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4561b52049da9c051b7e8eda3835545f600c0e70
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68120778"
---
# <a name="stsrid-geography-data-type"></a>STSrid (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid** является целым числом, представляющим собой идентификатор пространственной ссылки (SRID) экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STSrid  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
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
  
  
