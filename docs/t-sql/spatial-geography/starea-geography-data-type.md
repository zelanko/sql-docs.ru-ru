---
title: STArea (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STArea (geography Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 817a6325b956f5fc4214597b0b8bc46f6aff49f3
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68042509"
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
  
## <a name="remarks"></a>Remarks  
Метод STArea() возвращает значение 0, если экземпляр **geography** содержит только объекты размерности 0 и 1 либо является пустым.  
  
> [!NOTE]  
>  Методы, вызываемые для типа данных **geography** и возвращающие метрическое значение, могут возвращать различные результаты в зависимости от идентификатора SRID экземпляра. Дополнительные сведения об идентификаторах SRID см. в разделе [Идентификаторы пространственных ссылок (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Примеры  
В следующем примере используется метод `STArea()` для создания экземпляра `Polygon geography` и вычисляется площадь этого многоугольника.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a>См. также:  
[Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
