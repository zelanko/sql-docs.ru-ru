---
title: STDifference (тип данных geography) | Документы Майкрософт
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
- STDifference_TSQL
- STDifference (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDifference (geography Data Type)
ms.assetid: 1cde5054-b91a-41bb-812a-08c9308738af
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8eeb7743ed17f9bd2bbd837b02357723cbb0f49e
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36253936"
---
# <a name="stdifference-geography-data-type"></a>STDifference (тип данных geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает объект, представляющий набор точек одного экземпляра **geography**, который находится за пределами другого экземпляра **geography**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.STDifference ( other_geography )  
```  
  
## <a name="arguments"></a>Аргументы  
 *other_geography*  
 Другой экземпляр **geography**, который показывает, какие точки нужно удалить из экземпляра, для которого вызван метод STDifference().  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geography**  
  
 Тип возвращаемых данных CLR: **SqlGeography**  
  
## <a name="exceptions"></a>Исключения  
 Этот метод вызывает исключение **ArgumentException**, если экземпляр содержит противоположную границу.  
  
## <a name="remarks"></a>Remarks  
 Этот метод всегда возвращает значение NULL, если идентификаторы пространственных ссылок (SRID) экземпляров **geography** не совпадают.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] набор возможных результатов, возвращаемый на сервер, был пополнен экземплярами **FullGlobe**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает пространственные экземпляры, размер которых превышает полусферу. Результат может содержать сегменты дуги, только если во входном экземпляре содержатся сегменты дуги. Этот метод не является точным.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-computing-the-difference-between-two-geography-instances"></a>A. Вычисление разницы между двумя географическими объектами  
 В следующем примере с помощью метода `STDifference()` вычисляется разница между двумя экземплярами **geography**.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STDifference(@h).ToString();  
```  
  
### <a name="b-using-a-fullglobe-with-stdifference"></a>Б. Использование параметра FullGlobe с функцией STDifference()  
 В следующем примере используется экземпляр `FullGlobe`. Первый результат — пустая коллекция `GeometryCollection`, второй результат — экземпляр `Polygon`. `STDifference()` возвращает пустую коллекцию `GeometryCollection`, когда экземпляр `FullGlobe` является параметром. Каждая точка экземпляра `geography` содержится в экземпляре `FullGlobe`.  
  
```
 DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 DECLARE @h geography = 'FULLGLOBE';  
 SELECT @g.STDifference(@h).ToString(),  
 @h.STDifference(@g).ToString();
 ```  
  
## <a name="see-also"></a>См. также:  
 [Методы OGC в экземплярах Geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
