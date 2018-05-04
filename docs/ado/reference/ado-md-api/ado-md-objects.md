---
title: Объекты ADO MD | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, objects
- objects [ADO MD]
ms.assetid: 2a32e873-3282-4520-a7ed-89493f1da80e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9bbf76436f006f7561b5bf7aea43c7450e774209
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ado-md-objects"></a>Объекты ADO MD
|||  
|-|-|  
|[Оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|Представляет позиционные или оси фильтра набора ячеек, содержащий выбранные элементы из одного или нескольких измерений.|  
|[Каталог](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|Сведения многомерной схемой (т. е кубы и базового измерения, иерархии, уровни и элементы) поставщикам многомерных данных (MDP).|  
|[Ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md)|Представляет данные на пересечении координаты по осям, содержащихся в наборе ячеек.|  
|[Набор ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|Представляет результаты многомерного запроса. Представляет коллекцию ячеек, выбранных из кубов или других наборов ячеек.|  
|[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|Представляет куб из многомерной схемой, содержащий набор связанных измерений.|  
|[Измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|Представляет одно из измерений многомерного куба, содержащего иерархии на один или несколько элементов.|  
|[Иерархия](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|Представляет один из способов того, в котором элементы измерения могут статистическую обработку или «накоплены.» Измерение может быть статистически вычислена вдоль одной или нескольких иерархий.|  
|[Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)|Содержит набор элементов, каждый из которых имеет один и тот же ранг в иерархии.|  
|[Член](../../../ado/reference/ado-md-api/member-object-ado-md.md)|Представляет элемент в кубе, уровня дочерних элементов элемента уровня или членом положение вдоль оси набора ячеек.|  
|[Положение](../../../ado/reference/ado-md-api/position-object-ado-md.md)|Представляет набор один или несколько элементов из различных измерений, определяющую точку вдоль оси.|  
  
 Кроме того **каталога** объект подключен к ADO **подключения** объект, который входит в состав стандартной библиотеки ADO:  
  
|Объект|Описание|  
|------------|-----------------|  
|[Соединение](../../../ado/reference/ado-api/connection-object-ado.md)|Представляет открытое соединение с источником данных.|  
  
 Связи между этими объектами проиллюстрированы в [объектная модель ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md).  
  
 Многие объекты ADO MD может содержаться в соответствующую коллекцию. Например [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) объекта может содержаться в [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) коллекцию **каталога**. Дополнительные сведения см. в разделе [ADO MD коллекции](../../../ado/reference/ado-md-api/ado-md-collections.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO MD](../../../ado/reference/ado-md-api/ado-md-api-reference.md)   
 [Примеры кода ADO MD](../../../ado/reference/ado-md-api/ado-md-code-examples.md)   
 [ADO MD коллекций](../../../ado/reference/ado-md-api/ado-md-collections.md)   
 [ADO MD перечисляемые константы](../../../ado/reference/ado-md-api/ado-md-enumerated-constants.md)   
 [Методы ADO MD](../../../ado/reference/ado-md-api/ado-md-methods.md)   
 [Объектная модель ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Свойства многомерных объектов ADO](../../../ado/reference/ado-md-api/ado-md-properties.md)
