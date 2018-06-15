---
title: geography (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- geography
dev_langs:
- TSQL
helpviewer_keywords:
- geography data type [SQL Server], Transact-SQL
- spatial data types [SQL Server]
ms.assetid: d9e4952a-1841-4465-a64b-11e9288dba1d
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 03fa1c2b82196d119e69d5073e34de8f7be43234
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33062238"
---
# <a name="spatial-types---geography"></a>Пространственные типы — geography
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Географический пространственный тип данных **geography** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реализуется как тип данных среды CLR .NET. Этот тип представляет данные в системе координат круглой земли. Тип данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **geography** хранит данные эллипсоидальной (сферической) Земли, такие как координаты широты и долготы GPS.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает набор методов для пространственного типа данных **geography**. К ним относятся методы для работы с типом **geography**, как они определены в спецификации открытого геопространственного консорциума (OGC), а также набор расширений [!INCLUDE[msCoName](../../includes/msconame-md.md)] для этого стандарта.  
 
 Допустимая погрешность методов **geography** может составлять до 1,0e-7 * экстентов. Экстенты ссылаются на приблизительное максимальное расстояние между точками объекта **geography**.
  

## <a name="registering-the-geography-type"></a>Регистрация типа geography  
 Тип **geography** является стандартным и доступен в каждой базе данных. В таблице можно создать столбцы типа **geography** и обращаться с данными **geography** так же, как с данными других предусмотренных в системе типов. Может использоваться в материализованных и нематериализованных вычисляемых столбцах.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-showing-how-to-add-and-query-geography-data"></a>A. Демонстрация добавления и запроса географических данных  
 В следующих примерах иллюстрируется добавление и запрос географических данных. В первом примере создается таблица со столбцом идентификаторов и столбцом `geography` типа `GeogCol1`. Третий столбец обрабатывает столбец `geography` для представления в формате известного текста (WKT) OGC, используя метод `STAsText()`. Затем вставляются две строки: одна строка содержит экземпляр `LineString` типа `geography`, а другая — экземпляр `Polygon`.  
  
```  
IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
    DROP TABLE dbo.SpatialTable;  
GO  
  
CREATE TABLE SpatialTable   
    ( id int IDENTITY (1,1),  
    GeogCol1 geography,   
    GeogCol2 AS GeogCol1.STAsText() );  
GO  
  
INSERT INTO SpatialTable (GeogCol1)  
VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656 )', 4326));  
  
INSERT INTO SpatialTable (GeogCol1)  
VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653 , -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
GO  
```  
  
### <a name="b-returning-the-intersection-of-two-geography-instances"></a>Б. Получение точек пересечения двух экземпляров географического объекта  
 В следующем примере используется метод `STIntersection()` для получения точек, где пересекаются два ранее вставленных объекта `geography`.  
  
```  
DECLARE @geog1 geography;  
DECLARE @geog2 geography;  
DECLARE @result geography;  
  
SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
SELECT @result = @geog1.STIntersection(@geog2);  
SELECT @result.STAsText();  
```  
  
### <a name="c-using-geography-in-a-computed-column"></a>В. Использование типа geography в вычисляемом столбце  
 В приведенном ниже примере создается таблица с материализованным вычисляемым столбцом типа **geography**.  
  
```  
IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
    DROP TABLE dbo.SpatialTable;  
GO  
  
CREATE TABLE SpatialTable  
(  
    locationId int IDENTITY(1,1),  
    location geography,  
    deliveryArea as location.STBuffer(10) persisted  
)  
```  
  
## <a name="see-also"></a>См. также:  
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)   

  
  
