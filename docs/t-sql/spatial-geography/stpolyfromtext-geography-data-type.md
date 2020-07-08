---
title: STPolyFromText (тип данных geography) | Документы Майкрософт
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPolyFromText_TSQL
- STPolyFromText (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPolyFromText method
ms.assetid: d7e6a2bb-d301-49fb-9202-c70a9d169b4d
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: d44b0ea05b2917235c89d6f98f496a4b6dcfac51
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85701975"
---
# <a name="stpolyfromtext-geography-data-type"></a>STPolyFromText (географический тип данных)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Возвращает экземпляр **geography** из WKT-представления открытого геопространственного консорциума (OGC) вместе со значениями Z (высота) и M (мера), сопровождающими экземпляр.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STPolyFromText ( 'polygon_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *polygon_tagged_text*  
 Представление в формате WKT возвращаемого экземпляра **geographyPolygon**. *polygon_tagged_text* является выражением типа **nvarchar(max)** .  
  
 *SRID*  
 Выражение типа **int**, представляющее идентификатор пространственной ссылки (SRID) возвращаемого экземпляра **geographyPolygon**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
 Тип OGC: **Polygon**  
  
## <a name="remarks"></a>Remarks  
 Если входные данные имеют неверный формат, метод вызовет исключение **FormatException**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере метод `STPolyFromText()` применяется для создания экземпляра `geography`.  
  
```  
DECLARE @g geography;  
SET @g = geography::STPolyFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>См. также:  
 [Статические географические методы OGC](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
