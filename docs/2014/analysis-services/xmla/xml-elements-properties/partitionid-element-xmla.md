---
title: Элемент PartitionID (XML для Аналитики) | Документы Microsoft
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
- PartitionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PartitionID
- urn:schemas-microsoft-com:xml-analysis#PartitionID
- microsoft.xml.analysis.partitionid
helpviewer_keywords:
- PartitionID element
ms.assetid: 19f06454-9719-488e-aeb6-3fc879313351
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 54631af41d95d7ab149f853c6c94b7af1965f1ca
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096722"
---
# <a name="partitionid-element-xmla"></a>Элемент PartitionID (XML для аналитики)
  Обозначает секцию в родительском элементе, которая содержит ссылку на объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Object> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <PartitionID>...</PartitionID>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|Если предок или родитель =<br />                        [Source](source-element-xmla.md), [Target](../xml-elements-properties/target-element-xmla.md)<br /><br /> Кратность = 1-1: обязательный элемент, который встречается ровно один раз.<br /><br /> Если предок или родитель = Все остальные:<br /><br /> Кратность = 0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Object](object-element-xmla.md), [ParentObject](parentobject-element-xmla.md), [Source](source-element-xmla.md), [Target](../xml-elements-properties/target-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  