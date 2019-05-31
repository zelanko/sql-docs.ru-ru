---
title: Point (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: ddd506ca3e78dd4ad5a12cfb108ca539e094cb4e
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2019
ms.locfileid: "65937996"
---
# <a name="point-geography-data-type"></a>Point (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Создает экземпляр **geography**, представляющий экземпляр **Point**, по значениям широты и долготы и идентификатору пространственной ссылки (SRID).
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Point ( Lat, Long, SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Lat*  
 Выражение **float**, представляющее координату по оси X создаваемого экземпляра **Point**.  
  
 *Long*  
 Выражение типа **float**, представляющее координату по оси Y создаваемого экземпляра **Point**. Дополнительные сведения о допустимых значениях широты и долготы см. в разделе [Point](../../relational-databases/spatial/point.md).  
  
 *SRID*  
 Выражение типа **int**, представляющее идентификатор пространственной ссылки (SRID) возвращаемого экземпляра **geography**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемого значения CLR: **SqlGeography**  
  
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
  
  
