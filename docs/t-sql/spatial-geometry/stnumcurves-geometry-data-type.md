---
title: "STNumCurves (тип данных geometry) | Документы Microsoft"
ms.custom: 
ms.date: 08/03/2017
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
- STNumCurves method (geometry)
ms.assetid: 20c2fa0b-656b-4519-b34c-cc8f094290d4
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 718289c6785bec8f9bba15ccec76507ac2501f47
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="stnumcurves-geometry-data-type"></a>STNumCurves (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Этот метод возвращает количество кривых в **geometry** экземпляра, если экземпляр является типом одномерных пространственных данных. К типам одномерных пространственных данных относятся **LineString**, **CircularString**, и **CompoundCurve**. `STNumCurves`() поддерживает только простые типы; не работает с **geometry** коллекций, например **MultiLineString**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **геометрии**  
  
 Возвращаемый тип CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Замечания  
 Пустой одномерный **geometry** экземпляр возвращает 0. **Значение NULL** возвращается, когда **geometry** экземпляр не является одномерным экземпляром или неинициализированным экземпляром.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. Использование метода STNumCurves() в экземпляре CircularString  
 В следующем примере описывается получение определенного количества кривых в экземпляре `CircularString`:  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)');`  
  
 `SELECT @g.STNumCurves();`  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>Б. Использование метода STNumCurves() в экземпляре CompoundCurve  
 В следующем примере метод `STNumCurves()` используется для возврата определенного количества кривых в экземпляре `CompoundCurve`.  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))');`  
  
 `SELECT @g.STNumCurves();`  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [Методы OGC для геометрических объектов](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


