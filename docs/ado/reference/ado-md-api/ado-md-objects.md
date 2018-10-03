---
title: Многомерные объекты ADO | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, objects
- objects [ADO MD]
ms.assetid: 2a32e873-3282-4520-a7ed-89493f1da80e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e7f6cb865ec06e1031cd627316821ef4f666a64
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828715"
---
# <a name="ado-md-objects"></a>Многомерные объекты ADO
|||  
|-|-|  
|[Axis](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|Представляет позиционные или оси фильтра набора ячеек, содержащий выбранные элементы из одного или нескольких измерений.|  
|[Каталог](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|Содержит многомерных сведения (т. е кубы и базового измерения, иерархии, уровни и элементы) о схеме поставщик многомерных данных (MDP).|  
|[Cell](../../../ado/reference/ado-md-api/cell-object-ado-md.md)|Представляет данные на пересечении координатах оси, содержащиеся в наборе ячеек.|  
|[Набор ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|Представляет результаты из многомерного запроса. Это коллекция ячеек, выбираются из кубов или других наборов ячеек.|  
|[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|Представляет куб из многомерной схемой, содержащий набор связанных измерений.|  
|[Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|Представляет одно из измерений многомерного куба, содержащего один или несколько иерархии элементов.|  
|[Hierarchy](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|Представляет один из способов, в котором элементы измерения можно статистическая обработка или «накоплены.» Измерение может быть статистически вычислена вдоль одной или нескольким иерархиям.|  
|[Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)|Содержит набор элементов, каждый из которых имеет один и тот же ранг в иерархии.|  
|[Член](../../../ado/reference/ado-md-api/member-object-ado-md.md)|Представляет элемент уровня в кубе, дочерние элементы элемента уровня или членом положение вдоль оси набора ячеек.|  
|[Положение](../../../ado/reference/ado-md-api/position-object-ado-md.md)|Представляет набор из одного или нескольких членов разных размерностей, определяющую точку вдоль оси.|  
  
 Кроме того **каталога** объект подключен к ADO **подключения** объект, который входит в состав стандартной библиотеке ADO:  
  
|Объект|Описание|  
|------------|-----------------|  
|[Соединение](../../../ado/reference/ado-api/connection-object-ado.md)|Представляет открытое подключение к источнику данных.|  
  
 Связи между этими объектами проиллюстрированы в [объектная модель ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md).  
  
 Многие объекты ADO MD может содержаться в соответствующую коллекцию. Например [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) объекта может содержаться в [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) коллекцию **каталога**. Дополнительные сведения см. в разделе [коллекции многомерных Объектов ADO](../../../ado/reference/ado-md-api/ado-md-collections.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO MD](../../../ado/reference/ado-md-api/ado-md-api-reference.md)   
 [Примеры кода многомерных Объектов ADO](../../../ado/reference/ado-md-api/ado-md-code-examples.md)   
 [Коллекции многомерных Объектов ADO](../../../ado/reference/ado-md-api/ado-md-collections.md)   
 [Перечисляемые константы многомерных Объектов ADO](../../../ado/reference/ado-md-api/ado-md-enumerated-constants.md)   
 [Методы многомерных Объектов ADO](../../../ado/reference/ado-md-api/ado-md-methods.md)   
 [Объектная модель ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Свойства многомерных объектов ADO](../../../ado/reference/ado-md-api/ado-md-properties.md)
