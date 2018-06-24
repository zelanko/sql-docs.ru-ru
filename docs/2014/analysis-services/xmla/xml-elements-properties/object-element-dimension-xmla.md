---
title: Объект элемента (измерение) (XMLA) | Документы Microsoft
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
- Object Element (Dimension)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Object
- urn:schemas-microsoft-com:xml-analysis#Object
- microsoft.xml.analysis.object
helpviewer_keywords:
- Object element
ms.assetid: db7feb39-7cc1-4b54-8979-77ce402ef71f
caps.latest.revision: 10
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 2f0a80bcd26e5a54a0c45adff7667b4cfebdc467
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096229"
---
# <a name="object-element-dimension-xmla"></a>Элемент Object (Dimension) (XMLA)
  Содержит ссылку на объект для измерения, на котором родительского [вставить](../xml-elements-commands/insert-element-xmla.md), [обновление](../xml-elements-commands/update-element-xmla.md), или [Drop](../xml-elements-commands/drop-element-xmla.md) выполняется команда.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Insert> <!-- or any of the parent elements in the Element Relationships table -->  
...  
   <Object>  
      <Database>...</Database>  
      <Cube>...</Cube>  
      <Dimension>...</Dimension>  
   </Object>  
...  
</Insert>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|1-1: обязательный элемент, который встречается ровно один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Удалить](../xml-elements-commands/drop-element-xmla.md), [вставить](../xml-elements-commands/insert-element-xmla.md), [обновления](../xml-elements-commands/update-element-xmla.md)|  
|Дочерние элементы|[Куб](cube-element-xmla.md), [базы данных](database-element-xmla.md), [измерения](dimension-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  