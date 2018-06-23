---
title: Элемент DeleteWithDescendants (XML для Аналитики) | Документы Microsoft
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
- DeleteWithDescendants Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DeleteWithDescendants
- microsoft.xml.analysis.deletewithdescendants
- urn:schemas-microsoft-com:xml-analysis#DeleteWithDescendants
helpviewer_keywords:
- DeleteWithDescendants element
ms.assetid: adfc9437-aaa7-4364-bcdb-128fcc9a410d
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 0a51772adb2a571f99a5927fe8150d04ab5ef648
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190511"
---
# <a name="deletewithdescendants-element-xmla"></a>Элемент DeleteWithDescendants (XML для аналитики)
  Указывает, удаляются ли потомки элементов атрибутов командой [Drop](../xml-elements-commands/drop-element-xmla.md) , примененной к родительскому элементу.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Drop>  
   ...  
   <DeleteWithDescendants>...</DeleteWithDescendants>  
   ...  
</Drop>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Логическое значение|  
|Значение по умолчанию|False|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[DROP](../xml-elements-commands/drop-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 `DeleteWithDescendants` Определяет ли `Drop` команду следует удалить элементы атрибутов, определенных в [где](where-element-xmla.md) элемент, но также, потомки этих элементов атрибутов будут также удалены.  
  
> [!NOTE]  
>  Этот элемент применяется только к элементам атрибутов в иерархиях родителей-потомков.  
  
 Дополнительные сведения об удалении и обновлении элементов атрибутов см. в разделе [Вставка, обновление и удаление элементов (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  