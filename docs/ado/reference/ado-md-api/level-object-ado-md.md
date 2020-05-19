---
title: Объект Level (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level
helpviewer_keywords:
- Level object [ADO MD]
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
author: rothja
ms.author: jroth
ms.openlocfilehash: e1ee7ad05f05d2eb77d7d705200c52ddf3f01146
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82753848"
---
# <a name="level-object-ado-md"></a>Объект Level (многомерные объекты ADO)
Содержит набор элементов, каждый из которых имеет одинаковый ранг в иерархии.  
  
## <a name="remarks"></a>Примечания  
 С помощью коллекций и свойств объекта **Level** можно выполнять следующие действия.  
  
-   Определяет **уровень** с помощью свойств [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md) и [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) .  
  
-   Возвращает строку, используемую при отображении **уровня** со свойством [Caption](../../../ado/reference/ado-md-api/caption-property-ado-md.md) .  
  
-   Возвращает осмысленную строку, описывающую **уровень** со свойством [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md) .  
  
-   Возвращает объекты [элементов](../../../ado/reference/ado-md-api/member-object-ado-md.md) , которые составляют **уровень** , с коллекцией [Members](../../../ado/reference/ado-md-api/members-collection-ado-md.md) .  
  
-   Возвращает количество уровней от корня **уровня** к свойству [Depth](../../../ado/reference/ado-md-api/depth-property-ado-md.md) .  
  
-   Используйте стандартную коллекцию [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) ADO для получения дополнительных сведений об объекте **Level** .  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|name|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, которому принадлежит куб.|  
|CubeName|Имя куба.|  
|Описание|Понятное описание уровня.|  
|дименсионуникуенаме|Однозначное имя [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|хиерарчюникуенаме|Однозначное имя иерархии.|  
|левелкаптион|Метка или заголовок, связанный с уровнем.|  
|левелкардиналити|Число элементов уровня.|  
|левелгуид|Идентификатор GUID уровня.|  
|LevelName|Имя уровня.|  
|LevelNumber|Расстояние между уровнем и корнем иерархии.|  
|LevelType|Тип уровня.|  
|LevelUniqueName|Однозначное имя уровня.|  
|SchemaName|Имя схемы, к которой принадлежит куб.|  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Объект Hierarchy (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [Коллекция Levels (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Коллекция Members (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
