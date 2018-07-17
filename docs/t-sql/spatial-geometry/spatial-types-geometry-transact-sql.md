---
title: geometry (Transact-SQL) | Документы Майкрософт
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
- geometry
dev_langs:
- TSQL
helpviewer_keywords:
- spatial data types [SQL Server]
- geometry data type [SQL Server], Transact-SQL
ms.assetid: 3fefdf7b-f931-404c-821c-82c0375eaf51
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 84fefb61be47f566e64803983c5d5723e3d202cc
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36242176"
---
# <a name="spatial-types---geometry-transact-sql"></a>Пространственные типы — geometry (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Плоский пространственный тип данных **geometry** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реализуется как тип данных среды CLR. Этот тип представляет данные в евклидовом пространстве (плоской системе координат).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает набор методов для пространственного типа данных **geometry**. К этим методам относятся методы **geometry**, определенные стандартом OGC, и набор расширений [!INCLUDE[msCoName](../../includes/msconame-md.md)] для этого стандарта.  
 
 Допустимая погрешность методов geometry может составлять до 1.0e-7 * экстентов. Экстенты ссылаются на приблизительное максимальное расстояние между точками объекта **geometry**.
  
## <a name="registering-the-geometry-type"></a>Регистрация типа geometry  
 Тип **geometry** является стандартным и доступен в каждой базе данных. В таблице можно создать столбцы типа **geometry** и обращаться с данными **geometry** так же, как и с данными других типов среды CLR. Может использоваться в материализованных и нематериализованных вычисляемых столбцах.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-showing-how-to-add-and-query-geometry-data"></a>A. Отображение добавления и запроса данных типа geometry  
 В следующих двух примерах иллюстрируется добавление и запрос данных типа geometry. В первом примере создается таблица со столбцом идентификаторов и столбцом `geometry` типа `GeomCol1`. Третий столбец обрабатывает столбец `geometry` для представления в формате известного текста (WKT) OGC, используя метод `STAsText()`. Затем вставляются две строки: одна строка содержит экземпляр `LineString` типа `geometry`, а другая — экземпляр `Polygon`.  
  
```sql 
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
  
### <a name="b-returning-the-intersection-of-two-geometry-instances"></a>Б. Возвращение пересечения двух экземпляров geometry  
 Во втором примере метод `STIntersection()` используется для получения точек, в которых пересекаются два вставленных ранее экземпляра `geometry`.  
  
```sql  
DECLARE @geom1 geometry;  
DECLARE @geom2 geometry;  
DECLARE @result geometry;  
  
SELECT @geom1 = GeomCol1 FROM SpatialTable WHERE id = 1;  
SELECT @geom2 = GeomCol1 FROM SpatialTable WHERE id = 2;  
SELECT @result = @geom1.STIntersection(@geom2);  
SELECT @result.STAsText();  
```  
  
### <a name="c-using-geometry-in-a-computed-column"></a>В. Использование типа geometry в вычисляемом столбце  
 В следующем примере создается таблица с материализованным вычисляемым столбцом типа **geometry**.  
  
```sql  
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
  
## <a name="see-also"></a>См. также  
  [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
