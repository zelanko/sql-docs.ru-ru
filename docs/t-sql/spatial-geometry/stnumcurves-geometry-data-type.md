---
title: STNumCurves (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geometry)
ms.assetid: 20c2fa0b-656b-4519-b34c-cc8f094290d4
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 947baac6cd2a562bc24469bcf9554aca7a735ae7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="stnumcurves-geometry-data-type"></a>STNumCurves (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Этот метод возвращает число кривых в экземпляре **geometry**, представленном типом одномерных пространственных данных. К одномерным пространственным типам данных относятся **LineString**, **CircularString** и **CompoundCurve**. Метод `STNumCurves`() поддерживает только простые типы; он не поддерживает коллекции **geometry**, такие как **MultiLineString**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Пустой одномерный экземпляр **geometry** возвращает значение 0. Значение **NULL** возвращается, если экземпляр **geometry** не является одномерным или неинициализированным экземпляром.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. Использование метода STNumCurves() в экземпляре CircularString  
 В следующем примере описывается получение определенного количества кривых в экземпляре `CircularString`:  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>Б. Использование метода STNumCurves() в экземпляре CompoundCurve  
 В следующем примере метод `STNumCurves()` используется для возврата определенного количества кривых в экземпляре `CompoundCurve`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Методы OGC в экземплярах Geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

