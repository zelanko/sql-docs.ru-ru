---
title: объекты данных ActiveX (MD) объекты | Документация Майкрософт
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
ms.openlocfilehash: d568ca20cca6c12a04c0f3d54a2c134d59a0d7fc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67930574"
---
# <a name="ado-md-objects"></a>Многомерные объекты ADO

|||  
|-|-|  
|[Ось](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|Представляет координату или ось фильтрации набора ячеек, содержащего выбранные элементы одного или нескольких измерений.|  
|[Каталог](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|Содержит сведения о многомерной схеме (то есть Кубы и базовые измерения, иерархии, уровни и элементы), относящиеся к поставщику многомерных данных (MDP).|  
|[Cell (Ячейка)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)|Представляет данные на пересечении координат осей, содержащихся в наборе ячеек.|  
|[Набора ячеек](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|Представляет результаты многомерного запроса. Это коллекция ячеек, выбранных из кубов или других наборы ячеек.|  
|[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|Представляет куб из многомерной схемы, содержащий набор связанных измерений.|  
|[Измерение](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|Представляет одно из измерений многомерного куба, содержащего одну или несколько иерархий элементов.|  
|[Иерархия](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|Представляет один из способов, с помощью которых элементы измерения могут быть объединены или сведены. Измерение можно объединить по одной или нескольким иерархиям.|  
|[Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)|Содержит набор элементов, каждый из которых имеет одинаковый ранг в иерархии.|  
|[Участник](../../../ado/reference/ado-md-api/member-object-ado-md.md)|Представляет элемент уровня в Кубе, дочерние элементы элемента уровня или элемента в положении вдоль оси набора ячеек.|  
|[Разместить](../../../ado/reference/ado-md-api/position-object-ado-md.md)|Представляет набор из одного или нескольких элементов различных измерений, определяющих точку вдоль оси.|  
  
 Кроме того, объект **каталога** подключается к объекту **соединения** ADO, который входит в стандартную библиотеку ADO:  
  
|Объект|Description|  
|------------|-----------------|  
|[Соединен](../../../ado/reference/ado-api/connection-object-ado.md)|Представляет открытое соединение с источником данных.|  
  
 Связи между этими объектами иллюстрируются в [объектной модели объекты данных ActiveX (MD)](../../../ado/reference/ado-md-api/ado-md-object-model.md).  
  
 Многие объекты объекты данных ActiveX (MD) могут содержаться в соответствующей коллекции. Например, объект [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) может содержаться в коллекции [кубедефс](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) **каталога**. Дополнительные сведения см. в разделе [объекты данных ActiveX (MD) Collections](../../../ado/reference/ado-md-api/ado-md-collections.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по объекты данных ActiveX (MD) API](../../../ado/reference/ado-md-api/ado-md-api-reference.md)   
 [Примеры кода объекты данных ActiveX (MD)](../../../ado/reference/ado-md-api/ado-md-code-examples.md)   
 [объекты данных ActiveX (MD) коллекции](../../../ado/reference/ado-md-api/ado-md-collections.md)   
 [объекты данных ActiveX (MD) перечислимые константы](../../../ado/reference/ado-md-api/ado-md-enumerated-constants.md)   
 [Методы объекты данных ActiveX (MD)](../../../ado/reference/ado-md-api/ado-md-methods.md)   
 [Объектная модель объекты данных ActiveX (MD)](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Свойства многомерных объектов ADO](../../../ado/reference/ado-md-api/ado-md-properties.md)
