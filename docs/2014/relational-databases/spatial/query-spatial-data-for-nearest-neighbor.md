---
title: Запросы к пространственным данным для поиска ближайшего соседа | Документация Майкрософт
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 7af4ad5d-484e-45b4-aa16-83c33b358bb6
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 099771b9900d4c39de40b176cde5c92fa0c95462
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66014112"
---
# <a name="query-spatial-data-for-nearest-neighbor"></a>Запросы пространственных данных для ближайшего соседа
  При работе с пространственными данными часто применяется запрос ближайшего соседа. Запрос ближайшего соседа находит пространственные объекты, расположенные ближе всего к указанному пространственному объекту. Например, компонент поиска магазинов на веб-сайте часто должен находить магазины, которые расположены ближе всего к текущему положению клиента.  
  
 Запросы ближайшего соседа могут формулироваться в ряде различных допустимых форматов запроса, но если запрос ближайшего соседа использует пространственный индекс, то должен применяться следующий синтаксис.  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
SELECT TOP ( number )  
        [ WITH TIES ]  
        [ * | expression ]   
        [, ...]  
    FROM spatial_table_reference, ...   
        [ WITH   
            (   
                [ INDEX ( index_ref ) ]   
                [ , SPATIAL_WINDOW_MAX_CELLS = <value>]   
                [ ,... ]   
            )   
        ]  
    WHERE   
        column_ref.STDistance ( @spatial_ object )   
            {   
                [ IS NOT NULL ] | [ < const ] | [ > const ]   
                | [ <= const ] | [ >= const ] | [ <> const ] ]   
            }  
            [ AND { other_predicate } ]   
    }  
    ORDER BY column_ref.STDistance ( @spatial_ object ) [ ,...n ]  
[ ; ]  
  
```  
  
## <a name="nearest-neighbor-query-and-spatial-indexes"></a>Запросы ближайшего соседа и пространственные индексы  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при выполнении запросов ближайшего соседа к столбцам пространственных данных часто применяются предложения `TOP` и `ORDER BY`. Предложение `ORDER BY` содержит вызов метода `STDistance()` для типа данных пространственного столбца. Предложение `TOP` задает количество возвращаемых запросом объектов.  
  
 Для того чтобы запрос ближайшего соседа использовал пространственный индекс, должны выполняться следующие требования.  
  
1.  В одном из пространственных столбцов должен иметься пространственный индекс, а метод `STDistance()` должен использовать этот столбец в предложениях `WHERE` и `ORDER BY`.  
  
2.  Предложение `TOP` не может содержать инструкцию `PERCENT`.  
  
3.  Предложение `WHERE` должно содержать метод `STDistance()`.  
  
4.  Если в предложении `WHERE` имеется несколько предикатов, то предикат, содержащий метод `STDistance()`, должен соединяться с другими предикатами условием `AND`. Метод `STDistance()` не может входить в необязательную часть предложения `WHERE`.  
  
5.  Первое выражение в предложении `ORDER BY` должно вызывать метод `STDistance()`.  
  
6.  В первом выражении `STDistance()` в предложении `ORDER BY` должен использоваться порядок сортировки `ASC`.  
  
7.  Все строки, для которых `STDistance` возвращает `NULL`, должны исключаться фильтром.  
  
> [!WARNING]  
>  Методы, принимающие в качестве аргументов типы данных `geography` или `geometry`, возвращают значение `NULL`, если идентификаторы SRID для типов не совпадают.  
  
 В запросах ближайшего соседа рекомендуется использовать новые тесселяции пространственных индексов. Дополнительные сведения о тесселяциях пространственных индексов см. в разделе [Пространственные данные (SQL Server)](spatial-data-sql-server.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода показывается запрос ближайшего соседа, в котором может применяться пространственный индекс. В примере используется таблица `Person.Address` базы данных `AdventureWorks2012` .  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
WHERE SpatialLocation.STDistance(@g) IS NOT NULL  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 Создание пространственного индекса на столбце SpatialLocation для демонстрации того, как запрос ближайшего соседа использует пространственный индекс. Дополнительные сведения о создании пространственных индексов см. в разделе [Create, Modify, and Drop Spatial Indexes](create-modify-and-drop-spatial-indexes.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода показывается запрос ближайшего соседа, в котором не может применяться пространственный индекс.  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 В запросе отсутствует предложение `WHERE`, использующее `STDistance()` указанным в разделе синтаксиса образом, поэтому данный запрос не может использовать пространственный индекс.  
  
## <a name="see-also"></a>См. также  
 [Пространственные данные (SQL Server)](spatial-data-sql-server.md)  
  
  
