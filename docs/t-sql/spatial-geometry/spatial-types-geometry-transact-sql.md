---
title: "Geometry (Transact-SQL) | Документы Microsoft"
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
- geometry
dev_langs:
- TSQL
helpviewer_keywords:
- spatial data types [SQL Server]
- geometry data type [SQL Server], Transact-SQL
ms.assetid: 3fefdf7b-f931-404c-821c-82c0375eaf51
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2ba0303292df8bb8610831594393f6ec3072b5f3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="spatial-types---geometry-transact-sql"></a>Пространственные типы - geometry (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Плоские Пространственные данные типа, **geometry**, реализован как тип среды CLR (CLR) данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот тип представляет данные в евклидовом пространстве (плоской системе координат).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]поддерживает набор методов для **geometry** пространственный тип данных. Сюда входят методы на **geometry** , определенных стандартом Open Geospatial Consortium (OGC) и набор [!INCLUDE[msCoName](../../includes/msconame-md.md)] расширения для этого стандарта.  
 
 Погрешность геометрические методы может достигать 1.0e-7 * экстентов. Экстенты ссылаться на приблизительное максимальное расстояние между точками **geometry**объекта.
  
## <a name="registering-the-geometry-type"></a>Регистрация типа geometry  
 Тип **geometry** является стандартным и доступен в каждой базе данных. В таблице можно создать столбцы типа **geometry** и обращаться с данными **geometry** так же, как и с данными других типов среды CLR. Может использоваться в материализованных и нематериализованных вычисляемых столбцах.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-showing-how-to-add-and-query-geometry-data"></a>A. Показан способ добавления и запроса геометрических данных  
 В следующих двух примерах иллюстрируется добавление и запрос геометрических данных. В первом примере создается таблица со столбцом идентификаторов и столбцом `geometry` типа `GeomCol1`. Третий столбец обрабатывает столбец `geometry` для представления в формате известного текста (WKT) OGC, используя метод `STAsText()` . Затем вставляются две строки: одна строка содержит объект `LineString` типа `geometry`, а другая — объект `Polygon` .  
  
```tsql 
IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
    DROP TABLE dbo.SpatialTable;  
GO  
  
CREATE TABLE SpatialTable   
    ( id int IDENTITY (1,1),  
    GeomCol1 geometry,   
    GeomCol2 AS GeomCol1.STAsText() );  
GO  
  
INSERT INTO SpatialTable (GeomCol1)  
VALUES (geometry::STGeomFromText('LINESTRING (100 100, 20 180, 180 180)', 0));  
  
INSERT INTO SpatialTable (GeomCol1)  
VALUES (geometry::STGeomFromText('POLYGON ((0 0, 150 0, 150 150, 0 150, 0 0))', 0));  
GO  
```  
  
### <a name="b-returning-the-intersection-of-two-geometry-instances"></a>Б. Возвращается пересечение двух экземпляров геометрических объектов  
 Во втором примере метод `STIntersection()` используется для получения точек, в которых пересекаются два вставленные ранее объекта `geometry` .  
  
```tsql  
DECLARE @geom1 geometry;  
DECLARE @geom2 geometry;  
DECLARE @result geometry;  
  
SELECT @geom1 = GeomCol1 FROM SpatialTable WHERE id = 1;  
SELECT @geom2 = GeomCol1 FROM SpatialTable WHERE id = 2;  
SELECT @result = @geom1.STIntersection(@geom2);  
SELECT @result.STAsText();  
```  
  
### <a name="c-using-geometry-in-a-computed-column"></a>В. Использование типа geometry в вычисляемом столбце  
 В следующем примере создается таблица с материализованным вычисляемым столбцом с помощью **geometry** типа.  
  
```tsql  
IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
    DROP TABLE dbo.SpatialTable;  
GO  
  
CREATE TABLE SpatialTable  
(  
    locationId int IDENTITY(1,1),  
    location geometry,  
    deliveryArea as location.STBuffer(10) persisted  
)  
```  
  
## <a name="see-also"></a>См. также:  
  [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  

