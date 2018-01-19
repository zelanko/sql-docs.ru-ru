---
title: "STConvexHull (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: STConvexHull method (geography)
ms.assetid: fb435db7-31bb-4243-9d8b-35379184cfb4
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e15e964e5f2f45b79fb6da569587185e5e468dc9
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="stconvexhull-geography-data-type"></a>STConvexHull (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает объект, представляющий выпуклую оболочку **geography** экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STConvexHull ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
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
  
  
