---
title: Объект Dimension (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Dimension
helpviewer_keywords:
- Dimension object [ADO MD]
ms.assetid: 66adbbd2-23a3-4c19-a91b-84c31309aa1b
author: rothja
ms.author: jroth
ms.openlocfilehash: 2d5b475600ef211d8203a64a1a2c6d917bb99914
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764305"
---
# <a name="dimension-object-ado-md"></a>Объект Dimension (многомерные объекты ADO)
Представляет одно из измерений многомерного куба, содержащего одну или несколько иерархий элементов.  
  
## <a name="remarks"></a>Примечания  
 С помощью коллекций и свойств объекта **Dimension** можно выполнять следующие действия.  
  
-   Определяет **измерение** с помощью свойств [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) .  
  
-   Возвращает осмысленную строку, описывающую **измерение** со свойством [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) .  
  
-   Возвращает объекты [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) , составляющие **измерение** , с помощью коллекции [иерархий](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md) .  
  
-   Используйте коллекцию стандартных [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) ADO для получения дополнительных сведений об объекте **измерения** .  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|name|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, которому принадлежит куб.|  
|CubeName|Имя куба.|  
|DefaultHierarchy|Уникальное имя иерархии по умолчанию.|  
|Описание|Понятное описание Куба.|  
|дименсионкаптион|Метка или заголовок, связанный с измерением.|  
|дименсионкардиналити|Число элементов в измерении.|  
|дименсионгуид|Идентификатор GUID измерения.|  
|DimensionName|Имя измерения.|  
|дименсионординал|Порядковый номер измерения в группе измерений, образующих куб.|  
|DimensionType|Тип измерения.|  
|дименсионуникуенаме|Однозначное имя измерения.|  
|SchemaName|Имя схемы, к которой принадлежит куб.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/dimension-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект CubeDef (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)   
 [Коллекция Dimensions (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Коллекция иерархий (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
