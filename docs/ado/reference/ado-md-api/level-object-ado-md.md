---
description: Объект Level (многомерные объекты ADO)
title: Объект Level (объекты данных ActiveX (MD)) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 34dc7bc7eb6d80b3ec50cb1838cda0d0e419053b
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986515"
---
# <a name="level-object-ado-md"></a>Объект Level (многомерные объекты ADO)
Содержит набор элементов, каждый из которых имеет одинаковый ранг в иерархии.  
  
## <a name="remarks"></a>Remarks  
 С помощью коллекций и свойств объекта **Level** можно выполнять следующие действия.  
  
-   Определяет **уровень** с помощью свойств [Name](./name-property-ado-md.md) и [UniqueName](./uniquename-property-ado-md.md) .  
  
-   Возвращает строку, используемую при отображении **уровня** со свойством [Caption](./caption-property-ado-md.md) .  
  
-   Возвращает осмысленную строку, описывающую **уровень** со свойством [Description](./description-property-ado-md.md) .  
  
-   Возвращает объекты [элементов](./member-object-ado-md.md) , которые составляют **уровень** , с коллекцией [Members](./members-collection-ado-md.md) .  
  
-   Возвращает количество уровней от корня **уровня** к свойству [Depth](./depth-property-ado-md.md) .  
  
-   Используйте стандартную коллекцию [свойств](../ado-api/properties-collection-ado.md) ADO для получения дополнительных сведений об объекте **Level** .  
  
 Коллекция **Properties** содержит свойства, предоставляемые поставщиком. В следующей таблице перечислены свойства, которые могут быть доступны. Фактический список свойств может отличаться в зависимости от реализации поставщика. Более полный список доступных свойств см. в документации поставщика.  
  
|Имя|Описание|  
|----------|-----------------|  
|CatalogName|Имя каталога, которому принадлежит куб.|  
|CubeName|Имя куба.|  
|Описание|Понятное описание уровня.|  
|дименсионуникуенаме|Однозначное имя [измерения](./dimension-object-ado-md.md).|  
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
  
-   [Свойства, методы и события](./level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример CubeDef (VBScript)](./cubedef-example-vbscript.md)   
 [Объект Hierarchy (объекты данных ActiveX (MD))](./hierarchy-object-ado-md.md)   
 [Коллекция Levels (объекты данных ActiveX (MD))](./levels-collection-ado-md.md)   
 [Коллекция Members (объекты данных ActiveX (MD))](./members-collection-ado-md.md)   
 [Коллекция Properties (ADO)](../ado-api/properties-collection-ado.md)