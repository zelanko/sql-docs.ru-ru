---
description: Пространственные данные (SQL Server)
title: Пространственные данные (SQL Server) | Документация Майкрософт
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a08d8a7c2449b1d9cb1f850290040c18d27a06a5
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97473155"
---
# <a name="spatial-data-sql-server"></a>Пространственные данные (SQL Server)
[!INCLUDE [SQL Server Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/sql-asdb-asdbmi.md)]

  Пространственные данные представляют сведения о физическом расположении и форме геометрических объектов. Этими объектами могут быть точки расположения или более сложные объекты, такие как страны, дороги или озера.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает два пространственных типа данных: **geometry** и **geography** .  
  
-   Пространственный тип данных **geometry** представляет данные в евклидовой (плоской) системе координат.  
  
-   Пространственный тип данных **geography** представляет данные в системе координат для сферической Земли.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]оба эти типа данных реализованы как типы данных среды CLR платформы .NET.  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> Связанные задачи  
 [Создание, конструирование и запрос экземпляров geometry](../../relational-databases/spatial/create-construct-and-query-geometry-instances.md)  
 Описывает методы, которые можно использовать с экземплярами типа данных geometry.  
  
 [Создание, проектирование и создание запросов к экземплярам типа данных geography](../../relational-databases/spatial/create-construct-and-query-geography-instances.md)  
 Описывает методы, которые можно использовать с экземплярами типа данных geography.  
  
 [Запросы пространственных данных для ближайшего соседа](../../relational-databases/spatial/query-spatial-data-for-nearest-neighbor.md)  
 Описывает общий шаблон запроса, используемый для поиска пространственных объектов, расположенных ближе всего к указанному пространственному объекту.  
  
 [Создание, изменение и удаление пространственных индексов](../../relational-databases/spatial/create-modify-and-drop-spatial-indexes.md)  
 Содержит сведения о создании, изменении и удалении пространственного индекса.  
  
## <a name="related-content"></a>См. также  
 [Основные сведения о типах пространственных данных](../../relational-databases/spatial/spatial-data-types-overview.md)  
 Описываются пространственные типы данных.  
  
-   [Point](../../relational-databases/spatial/point.md)  
  
-   [LineString](../../relational-databases/spatial/linestring.md)  
  
-   [CircularString](../../relational-databases/spatial/circularstring.md)  
  
-   [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)  
  
-   [Многоугольник](../../relational-databases/spatial/polygon.md)  
  
-   [CurvePolygon](../../relational-databases/spatial/curvepolygon.md)  
  
-   [MultiPoint](../../relational-databases/spatial/multipoint.md)  
  
-   [MultiLineString](../../relational-databases/spatial/multilinestring.md)  
  
-   [MultiPolygon](../../relational-databases/spatial/multipolygon.md)  
  
-   [GeometryCollection](../../relational-databases/spatial/geometrycollection.md)  
  
 [Общие сведения о пространственных индексах](../../relational-databases/spatial/spatial-indexes-overview.md)  
 Описываются пространственные индексы, тесселяция и схемы тесселяции.  
  
  
