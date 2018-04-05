---
title: Элемент annotation (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Annotation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Annotation
helpviewer_keywords:
- Annotation element
ms.assetid: 7d75291a-47b4-498a-8ba4-3d093b8513b2
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 09cafc5c5dcbafd48047995b03082a4d15e84288
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="annotation-element-assl"></a>Элемент Annotation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Содержит элементы, используемые для расширения схемы языка сценариев служб Analysis Services (ASSL).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Annotations>  
   <Annotation>  
      <Name>...</Name>  
      <Visibility>...</Visibility>  
      <Value>...</Value>  
   </Annotation>  
</Annotations >  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Description|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|Дочерние элементы|[Имя](../../../analysis-services/scripting/properties/name-element-assl.md), [значение](../../../analysis-services/scripting/properties/value-element-assl.md), [видимость](../../../analysis-services/scripting/properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 **Заметки** элемент предоставляет возможность расширения схемы ASSL для всех объектов, отличных от тех, которые используются исключительно для определения сложного типа данных. **Значение** элемент **заметки** элемент может содержать допустимый XML-код из любого пространства имен XML отличного от ASSL применяются следующие правила:  
  
-   В XML-коде могут содержаться только элементы.  
  
-   Каждый элемент должен иметь уникальное имя. Рекомендуется значение **имя** элемент **заметки** элемент ссылается на целевое пространство имен.  
  
 Эти правила применяются к позволяют содержимое **заметки** пары элемент должен быть предоставлен как набор имен и значений через другие интерфейсы, такие как объекты поддержки принятия решений (DSO).  
  
 Комментарии и пробелы в **заметки** невозможно сохранить элемент не были заключены в дочерний элемент. Кроме того, все элементы должны быть доступными для чтения и записи; элементы, доступные только для чтения, будут пропускаться.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>См. также:  
 [Объекты &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
