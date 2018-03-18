---
title: "Point (тип данных geometry) | Документы Майкрософт"
ms.custom: 
ms.date: 08/03/2017
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
- Point (geometry Data Type)
ms.assetid: 7a2e593a-4d4c-4214-b0c5-02d1ac46bc66
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 89f1a91310ea7ccbc6d4ab8724022c3463e4ea8d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="point-geometry-data-type"></a>Point (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Создает экземпляр **geometry**, который представляет экземпляр **Point**, на основе его значений X и Y и идентификатора SRID.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Point ( X, Y, SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *X*  
 Выражение **float**, представляющее координату по оси X создаваемого экземпляра **Point**.  
  
 *да*  
 Выражение типа **float**, представляющее координату по оси Y создаваемого экземпляра **Point**.  
  
 *SRID*  
 Выражение типа **int**, представляющее идентификатор пространственной ссылки (SRID) возвращаемого экземпляра **geometry**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемых данных CLR: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `Point()` применяется для создания экземпляра `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Point(1, 10, 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические геометрические методы](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

