---
title: MakeValid (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- MakeValid
- MakeValid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MakeValid (geometry Data Type)
ms.assetid: 38673010-ab77-4ebb-9c4d-b26b79e3b7ea
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 7b966741a1a6183379f7f2b1f4fa45c37e8044eb
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65937530"
---
# <a name="makevalid-geometry-data-type"></a>MakeValid (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Преобразует недопустимый экземпляр **geometry** в экземпляр **geometry** с допустимым типом открытого геопространственного консорциума (OGC).
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемого значения CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Применение этого метода может вызвать изменение типа экземпляра **geometry**, а также привести к небольшому сдвигу точек в экземпляре **geometry**.  
  
## <a name="examples"></a>Примеры  
 В первом примере создается недопустимый экземпляр `LineString`, который перекрывает сам себя, и используется метод `STIsValid()`, чтобы подтвердить, что этот экземпляр является недопустимым. Функция `STIsValid()` возвращает значение 0 для недопустимого экземпляра.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 0);  
SELECT @g.STIsValid();  
```  
  
 Во втором примере, чтобы преобразовать экземпляр в допустимый и проверить, что этот экземпляр действительно допустим, используется метод `MakeValid()`. Функция `STIsValid()` возвращает значение 1 для недопустимого экземпляра.  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.STIsValid();  
```  
  
 В третьем примере проверяется, как был изменен экземпляр для преобразования его в допустимый.  
  
```  
SELECT @g.ToString();  
```  
  
 В этом примере при выборе экземпляра `LineString` значения возвращаются так же, как при использовании допустимого экземпляра `MultiLineString`.  
  
```  
MULTILINESTRING ((0 2, 1 1, 2 2), (1 1, 1 0))  
```  
  
 В следующем примере экземпляр CircularString преобразуется в экземпляр Point.  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 1 1, 1 1)';  
SELECT @g.MakeValid().ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [STIsValid (тип данных geometry)](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [Расширенные методы экземпляров Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

