---
title: Пространственные данные (SQL Server) | Документация Майкрософт
ms.date: 06/14/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: dccec5ca3c42f605145853b2e864e861b17535fb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063028"
---
# <a name="spatial-data-sql-server"></a>Пространственные данные (SQL Server)
  Пространственные данные представляют сведения о физическом расположении и форме геометрических объектов. Этими объектами могут быть точки расположения или более сложные объекты, такие как страны, дороги или озера.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает два пространственных типа данных: `geometry` и `geography`.  
  
-   Тип `geometry` представляет данные в Евклидовой (плоской) системе координат.  
  
-   Тип `geography` представляет данные в системе координат круглой земли.  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]оба эти типа данных реализованы как типы данных среды CLR платформы .NET.  
  
> [!IMPORTANT]  
>  Подробное описание и примеры использования новых возможностей обработки пространственных данных в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]можно получить, загрузив технический документ [Новые функции обработки пространственных данных в SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> Связанные задачи  
 [Создание, конструирование и запрос экземпляров geometry](create-construct-and-query-geometry-instances.md)  
 Описывает методы, которые можно использовать с экземплярами типа данных geometry.  
  
 [Создание, проектирование и создание запросов к экземплярам типа данных geography](create-construct-and-query-geography-instances.md)  
 Описывает методы, которые можно использовать с экземплярами типа данных geography.  
  
 [Запросы пространственных данных для ближайшего соседа](query-spatial-data-for-nearest-neighbor.md)  
 Описывает общий шаблон запроса, используемый для поиска пространственных объектов, расположенных ближе всего к указанному пространственному объекту.  
  
 [Создание, изменение и удаление пространственных индексов](create-modify-and-drop-spatial-indexes.md)  
 Содержит сведения о создании, изменении и удалении пространственного индекса.  
  
## <a name="related-content"></a>См. также  
 [Основные сведения о типах пространственных данных](spatial-data-types-overview.md)  
 Описываются пространственные типы данных.  
  
-   [Point](point.md)  
  
-   [LineString](linestring.md)  
  
-   [CircularString](circularstring.md)  
  
-   [CompoundCurve](compoundcurve.md)  
  
-   [Многоугольник](polygon.md)  
  
-   [CurvePolygon](curvepolygon.md)  
  
-   [MultiPoint](multipoint.md)  
  
-   [MultiLineString](multilinestring.md)  
  
-   [MultiPolygon](multipolygon.md)  
  
-   [GeometryCollection](geometrycollection.md)  
  
 [Общие сведения о пространственных индексах](spatial-indexes-overview.md)  
 Описываются пространственные индексы, тесселяция и схемы тесселяции.  
  
  
