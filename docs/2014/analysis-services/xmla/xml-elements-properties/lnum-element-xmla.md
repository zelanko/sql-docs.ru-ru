---
title: Элемент LNum (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- LNum Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.lnum
- urn:schemas-microsoft-com:xml-analysis#LNum
- http://schemas.microsoft.com/analysisservices/2003/engine#LNum
helpviewer_keywords:
- LNum element
ms.assetid: 7b9cc143-0c5e-4a8c-a288-8921bfcfd103
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e19f8f362fad80ce7940eccb59d8170b393abc28
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306106"
---
# <a name="lnum-element-xmla"></a>Элемент LNum (XML для аналитики)
  Содержит сведения о порядковом положении уровня для родительского [HierarchyInfo](hierarchyinfo-element-xmla.md) или [член](member-element-xmla.md) элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <LNum>...</LNum>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|ssNoversion|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[HierarchyInfo](hierarchyinfo-element-xmla.md), [Member](member-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Для элементов `HierarchyInfo` в элементе `LNum` содержится имя свойства, которое предоставляет порядковые позиции уровней иерархии. Это значение эквивалентно значению свойства LEVEL_NUMBER, определенного для набора строк оси в спецификации OLE DB для OLAP.  
  
 Для `Member` элементов, `LNum` элемент содержит отсчитываемый от нуля порядковый номер, от корневого уровня в иерархии элемента, представленного родительским [член](member-element-xmla.md) элемент. Нулевое значение представляет корневой уровень иерархии.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
