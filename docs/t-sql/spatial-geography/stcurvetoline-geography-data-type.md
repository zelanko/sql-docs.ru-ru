---
title: "STCurveToLine (тип данных geography) | Документы Microsoft"
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
f1_keywords:
- STCurveToLine_TSQL
- STCurveToLine
dev_langs: TSQL
helpviewer_keywords: STCurveToLine method (geography)
ms.assetid: 2f863a85-6168-465a-b32f-bb5e3de58dee
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67b5f37ac6dd928f114ac1c224806387074ea97d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stcurvetoline-geography-data-type"></a>STCurveToLine (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает приближение из многоугольников **geography** экземпляра, содержащего сегменты дуги.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STCurveToLine()  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
## <a name="remarks"></a>Замечания  
 Возвращает **LineString** экземпляра для **CircularString** или **CompoundCurve** экземпляра.  
  
 Возвращает **многоугольника** экземпляра для **CurvePolygon** экземпляра.  
  
 Возврат копии **geography** экземпляры, которые не содержат **CircularString**, **CompoundCurve**, или **CurvePolygon** экземпляров.  
  
 В отличие от спецификации SQL MM этот метод не использует значения по оси z в расчета аппроксимации. Все значения по оси z представленные в названном **geography** экземпляра учитываются.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается экземпляр `LineString`, который представляет собой аппроксимацию из многоугольников для экземпляра `CircularString`:  
  
```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography;  
 SET @g2 = @g1.STCurveToLine();  
 SELECT @g1.STNumPoints() AS G1, @g2.STNumPoints() AS G2;
 ```  
  
## <a name="see-also"></a>См. также:  
 [STLength &#40; тип данных geography &#41;](../../t-sql/spatial-geography/stlength-geography-data-type.md)   
 [STNumPoints &#40; тип данных geography &#41;](../../t-sql/spatial-geography/stnumpoints-geography-data-type.md)   
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
