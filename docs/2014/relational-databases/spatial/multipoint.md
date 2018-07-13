---
title: MultiPoint | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dbbe51251adf9a681a817aa5e402a23f3b5dde2e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201144"
---
# <a name="multipoint"></a>MultiPoint
  Объект `MultiPoint` является коллекцией из нуля или более точек. Граница у экземпляра `MultiPoint` отсутствует.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `geometry MultiPoint` со значением SRID, равным 23, и двумя точками, с координатами (2, 3) и (7, 8), и значением Z, равным 9,5.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 Данный экземпляр `MultiPoint` может быть также выражен посредством `STMPointFromText()` , как показано ниже.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 В следующем примере метод `STGeometryN()` используется с целью получения описания первой точки коллекции.  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a>См. также  
 [Точка](point.md)   
 [Пространственные данные (SQL Server)](spatial-data-sql-server.md)  
  
  
