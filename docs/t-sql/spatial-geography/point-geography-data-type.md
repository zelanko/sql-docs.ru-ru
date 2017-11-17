---
title: "Точка (тип данных geography) | Документы Microsoft"
ms.custom: 
ms.date: 07/30/2017
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
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point method
- Point (geography Data Type)
ms.assetid: 0dc6f422-7aae-4016-b7f4-3289fa8f989c
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cefb6e199bbd4617b1fc2f6f71d9bb3997445dc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="point-geography-data-type"></a>Point (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Создает **geography** представляет экземпляр **точки** экземпляра по значениям широты и долготы и Идентификатору пространственной ссылки (SRID).
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Point ( Lat, Long, SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *LAT*  
 — **Float** выражение, представляющее координату по оси x **точки** создается.  
  
 *Long*  
 — **Float** выражение, представляющее координату y элемента **точки** создается. Дополнительные сведения о допустимых широты и долготы см. в разделе [точки](../../relational-databases/spatial/point.md).  
  
 *SRID*  
 — **Int** выражение, представляющее идентификатор SRID **geography** экземпляр, который необходимо вернуть.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **geography**  
  
 Возвращаемый тип CLR: **SqlGeography**  
  
> [!NOTE]  
>  Аргументы для метода точки (тип данных geography) имеют обратные координаты по сравнению с WKT.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `Point()` применяется для создания экземпляра `geography`.  
  
```  
DECLARE @g geography;   
SET @g = geography::Point(47.65100, -122.34900, 4326)  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические географические методы](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  

