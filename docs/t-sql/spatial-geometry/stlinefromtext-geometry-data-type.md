---
title: STLineFromText (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STLineFromText (geometry Data Type)
- STLineFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STLineFromText (geometry Data Type)
ms.assetid: 430508ad-207b-4dee-a4d1-4ddf25e6b4a9
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: a0a912e4ab228617537e9c28e9a5cecc4a0278fe
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "72278138"
---
# <a name="stlinefromtext-geometry-data-type"></a>STLineFromText (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает экземпляр **geometry** из WKT-представления открытого геопространственного консорциума (OGC) вместе со значениями Z (высота) и M (мера), сопровождающими экземпляр.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
STLineFromText ( 'linestring_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Аргументы  
 *linestring_tagged_text*  
 Представление в формате WKT возвращаемого экземпляра **geometryLineString**. *linestring_tagged_text* является выражением типа **nvarchar(max)** .  
  
 *SRID*  
 Выражение типа **int**, представляющее идентификатор пространственной ссылки (SRID) возвращаемого экземпляра **geometryLineString**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Тип возвращаемого значения CLR: **SqlGeometry**  
  
 Тип OGC: **LineString**  
  
## <a name="remarks"></a>Remarks  
Если входные данные имеют неверный формат, метод вызовет исключение **FormatException**. Нотация трехмерной измеряемой геометрии WKT из спецификации консорциума OGC "Simple Features for SQL" версии 1.2.1 не поддерживается. Ознакомьтесь с примерами для поддерживаемого представления значений Z (повышение) и M (измерение).
  
## <a name="examples"></a>Примеры  
 В следующих примерах метод `STLineFromText()` применяется для создания экземпляра `geometry`.

### <a name="example-1-two-dimension-geometry-wkt"></a>Пример 1: Двумерная геометрия WKT
```  
DECLARE @g geometry;  
SET @g = geometry::STLineFromText('LINESTRING (100 100, 200 200)', 0);  
SELECT @g.ToString();  
```  
  
### <a name="example-2-three-dimension-geometry-wkt"></a>Пример 2. Трехмерная геометрия WKT
```  
DECLARE @g geometry;  
SET @g = geometry::STLineFromText('LINESTRING (100 100 100, 200 200 200)', 0);  
SELECT @g.ToString();  
``` 

### <a name="example-3-two-dimension-measured-geometry-wkt"></a>Пример 3. Двумерная измеряемая геометрия WKT
```  
DECLARE @g geometry;  
SET @g = geometry::STLineFromText('LINESTRING (100 100 NULL 100, 200 200 NULL 200)', 0);  
SELECT @g.ToString();  
``` 

### <a name="example-4-three-dimension-measured-geometry-wkt"></a>Пример 4. Трехмерная измеряемая геометрия WKT
```  
DECLARE @g geometry;  
SET @g = geometry::STLineFromText('LINESTRING (100 100 100 100, 200 200 200 200)', 0);  
SELECT @g.ToString();  
``` 
## <a name="see-also"></a>См. также:  
 [Статические геометрические методы OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

