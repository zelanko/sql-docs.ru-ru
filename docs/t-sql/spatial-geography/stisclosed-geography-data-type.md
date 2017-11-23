---
title: "STIsClosed (тип данных geography) | Документы Microsoft"
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
- STIsClosed (geography Data Type)
- STIsClosed_TSQL
dev_langs: TSQL
helpviewer_keywords: STIsClosed method
ms.assetid: eba1643f-07c4-4500-8643-b7e90f908147
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 707a7b289874bb4181d660cb63ab399cd4cdd11d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="stisclosed-geography-data-type"></a>STIsClosed (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает 1, если начальную и конечную точки заданного **geography** экземпляра одинаковы. Возвращает значение 1 для **geography** типы коллекций, если каждый содержащийся **geography** экземпляр закрыт. Возвращает значение 0, если экземпляр является незамкнутым.  
  
 Это **geography** поддерживает метод тип **FullGlobe** экземпляры или Пространственные экземпляры, размер которых превышает полусферу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIsClosed ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Тип возвращаемого значения: **бит**  
  
 Возвращаемый тип CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Замечания  
 Этот метод возвращает 0, если любые фигуры **geography** экземпляра являются точки, или если экземпляр пуст.  
  
 Этот метод возвращает значение true, если **FullGlobe** экземпляр **многоугольника** или другим типом экземпляра.  
  
 Все **многоугольника** считаются замкнутыми.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Polygon` и вызывается метод `STIsClosed()`, который определяет, является ли экземпляр `Polygon` замкнутым.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
