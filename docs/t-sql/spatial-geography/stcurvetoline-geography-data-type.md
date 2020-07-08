---
title: STCurveToLine (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STCurveToLine_TSQL
- STCurveToLine
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveToLine method (geography)
ms.assetid: 2f863a85-6168-465a-b32f-bb5e3de58dee
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 61719cd9ddf153c2552bdac3046a7e24ce8deb86
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85704060"
---
# <a name="stcurvetoline-geography-data-type"></a>STCurveToLine (тип данных geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает приближение из многоугольников для экземпляра **geography**, содержащего сегменты дуги.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STCurveToLine()  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Возвращает экземпляр **LineString** для экземпляра **CircularString** или **CompoundCurve**.  
  
 Возвращает экземпляр **Polygon** для экземпляра **CurvePolygon**.  
  
 Возвращает копии экземпляров **geography**, которые не содержат экземпляры **CircularString**, **CompoundCurve** или **CurvePolygon**.  
  
 В отличие от спецификации SQL MM, данный метод не использует значения координаты z для расчета аппроксимации из многоугольников. Любое значение координаты z, представленное в вызываемом экземпляре **geography**, игнорируется.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается экземпляр `LineString`, который представляет собой аппроксимацию из многоугольников для экземпляра `CircularString`:  
  
```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography;  
 SET @g2 = @g1.STCurveToLine();  
 SELECT @g1.STNumPoints() AS G1, @g2.STNumPoints() AS G2;
 ```  
  
## <a name="see-also"></a>См. также:  
 [STLength (тип данных geography)](../../t-sql/spatial-geography/stlength-geography-data-type.md)   
 [STNumPoints (тип данных geography)](../../t-sql/spatial-geography/stnumpoints-geography-data-type.md)   
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
