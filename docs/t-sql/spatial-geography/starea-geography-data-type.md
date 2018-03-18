---
title: "STArea (тип данных geography) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
- STArea (geography Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2082c36f483e1ebe6d532abb6d3335db127b21b1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="starea-geography-data-type"></a>STArea (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает общую площадь поверхности экземпляра **geography**. Результаты для метода STArea() возвращаются в виде квадрата единицы измерения, используемой идентификатором пространственной ссылки экземпляра **geography**. Например, если SRID экземпляра равен 4326, то метод STArea() возвращает результаты в квадратных метрах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **float**  
  
 Тип возвращаемых данных CLR: **SqlDouble**  
  
## <a name="remarks"></a>Примечания  
 Метод STArea() возвращает значение 0, если экземпляр **geography** содержит только объекты размерности 0 и 1 либо является пустым.  
  
> [!NOTE]  
>  Методы, вызываемые для типа данных **geography** и возвращающие метрическое значение, могут возвращать различные результаты в зависимости от идентификатора SRID экземпляра. Дополнительные сведения об идентификаторах SRID см. в разделе [Идентификаторы пространственных ссылок (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется метод `STArea()` для создания экземпляра `Polygon``geography` и вычисляется площадь этого многоугольника.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a>См. также  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
