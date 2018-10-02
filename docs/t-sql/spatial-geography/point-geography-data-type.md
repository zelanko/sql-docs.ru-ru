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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4de164536b75684d8c019a9f93db4a9b21415650
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759812"
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
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
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
  
  
