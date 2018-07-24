---
title: STIsClosed (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STIsClosed (geography Data Type)
- STIsClosed_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIsClosed method
ms.assetid: eba1643f-07c4-4500-8643-b7e90f908147
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 832e2a44f091e256350988c20410e05559aaa2ca
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000033"
---
# <a name="stisclosed-geography-data-type"></a>STIsClosed (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает значение 1, если начальная и конечная точки заданного экземпляра **geography** совпадают. Возвращает 1 для типов коллекции **geography**, если каждый содержащийся экземпляр **geography** замкнут. Возвращает значение 0, если экземпляр является незамкнутым.  
  
 Этот метод типа данных **geography** поддерживает экземпляры **FullGlobe** или пространственные экземпляры, размер которых больше полушария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STIsClosed ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **bit**  
  
 Тип возвращаемых данных CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Этот метод возвращает значение 0, если среди фигур экземпляра **geography** есть точки или если экземпляр является пустым.  
  
 Метод возвращает значение true, если экземпляр **FullGlobe** имеет тип **Polygon** или является другим типом экземпляра.  
  
 Все экземпляры **Polygon** считаются замкнутыми.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается экземпляр `Polygon` и вызывается метод `STIsClosed()`, который определяет, является ли экземпляр `Polygon` замкнутым.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
