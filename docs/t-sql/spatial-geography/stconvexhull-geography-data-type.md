---
title: "STConvexHull (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STConvexHull method (geography)
ms.assetid: fb435db7-31bb-4243-9d8b-35379184cfb4
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a8376d12352994cd768b806f5ce47463196d4bfd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stconvexhull-geography-data-type"></a>STConvexHull (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает объект, представляющий выпуклую оболочку **geography** экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STConvexHull ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Замечания  
 Возвращает `FullGlobe` для объекта **geography** экземпляр, который угол конверта которого больше 90 градусов.  
  
 Возвращает пустую коллекцию **geography** коллекции для пустого **geography** экземпляра.  
  
 Возвращает **null** для неинициализированного **geography** экземпляра.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-stconvexhull-on-an-uninitialized-geography-instance"></a>A. Использование функции STConvexHull() в неинициализированном экземпляре географического объекта  
 В следующем примере используется `STConvexHull()` в неинициализированном **geography** экземпляра.  
  
```
 DECLARE @g geography;  
 SELECT @g.STConvexHull();
 ```  
  
### <a name="b-using-stconvexhull-on-an-empty-geography-instance"></a>Б. Использование функции STConvexHull() в пустом экземпляре географического объекта  
 В следующем примере используется `STConvexHull()` в пустом экземпляре `Polygon`.  
  
```
 DECLARE @g geography = 'POLYGON EMPTY';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
### <a name="c-finding-the-convex-hull-of-a-non-convex-polygon-instance"></a>В. Обнаружение выпуклой оболочки невыпуклого экземпляра объекта Polygon  
 В следующем примере метод `STConvexHull()` используется для поиска выпуклой оболочки невыпуклого экземпляра `Polygon`.  
  
```  
 DECLARE @g geography;  
 SET @g = geography::Parse('POLYGON((-120.533 46.566, -118.283 46.1, -122.3 47.45, -120.533 46.566))');  
 SELECT @g.STConvexHull().ToString();  
```  
  
### <a name="d-finding-the-convex-hull-on-a-geography-instance-with-an-envelope-angle-larger-than-90-degrees"></a>Г. Обнаружение выпуклой оболочки экземпляра географического объекта с углом пакета больше 90 градусов  
 В следующем примере используется `STConvexHull()` на **geography** экземпляра с углом пакета больше 90 градусов.  
  
```
 DECLARE @g geography = 'POLYGON((20.533 46.566, -18.283 46.1, -22.3 47.45, 20.533 46.566))';  
 SELECT @g.STConvexHull().ToString();
 ```  
  
  

