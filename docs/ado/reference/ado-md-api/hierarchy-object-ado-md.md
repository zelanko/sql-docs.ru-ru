---
title: Объект Hierarchy (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 35e02e4823d0a3abf245e1885b95176d6350d712
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949697"
---
# <a name="hierarchy-object-ado-md"></a>Объект Hierarchy (многомерные объекты ADO)
Представляет один из способов, с помощью которых элементы [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md) могут быть объединены или сведены. Измерение можно объединить по одной или нескольким иерархиям.  
  
## <a name="remarks"></a>Remarks  
 С помощью коллекций и свойств объекта **Hierarchy** можно выполнять следующие действия.  
  
-   Определяет **иерархию** с помощью свойств [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) .  
  
-   Возвращает осмысленную строку, описывающую **иерархию** со свойством [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) .  
  
-   Возвращает объекты [уровня](../../../ado/reference/ado-md-api/level-object-ado-md.md) , составляющие **иерархию** , с коллекцией [Levels](../../../ado/reference/ado-md-api/levels-collection-ado-md.md) .  
  
-   Используйте стандартную коллекцию [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) ADO для получения дополнительных сведений об объекте **иерархии** .  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|Имя|Описание|  
|----------|-----------------|  
|AllMember|Элемент на высшем уровне свертки в иерархии.|  
|CatalogName|Имя каталога, которому принадлежит куб.|  
|CubeName|Имя куба.|  
|DefaultMember|Уникальное имя элемента по умолчанию для этой иерархии.|  
|Описание|Понятное описание иерархии.|  
|DimensionType|Тип измерения, которому принадлежит эта иерархия.|  
|дименсионуникуенаме|Однозначное имя измерения.|  
|хиерарчикаптион|Метка или заголовок, связанный с иерархией.|  
|хиерарчикардиналити|Количество элементов в иерархии.|  
|хиерарчигуид|Идентификатор GUID иерархии.|  
|HierarchyName|Имя иерархии.|  
|хиерарчюникуенаме|Однозначное имя иерархии.|  
|SchemaName|Имя схемы, к которой принадлежит куб.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/hierarchy-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект Dimension (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Коллекция иерархий (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Коллекция Levels (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
