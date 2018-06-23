---
title: Элемент annotation (ASSL) | Документы Microsoft
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
- Annotation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Annotation
helpviewer_keywords:
- Annotation element
ms.assetid: 7d75291a-47b4-498a-8ba4-3d093b8513b2
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5dfe8ea881948de8ed53cea0ddcff1e1325a96d3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102105"
---
# <a name="annotation-element-assl"></a>Элемент Annotation (ASSL)
  Содержит элементы, используемые для расширения схемы языка ASSL.  
  
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
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Заметки](../collections/annotations-element-assl.md)|  
|Дочерние элементы|[Имя](../properties/name-element-assl.md), [значение](../properties/value-element-assl.md), [видимость](../properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент `Annotation` предоставляет возможность расширения схемы ASSL для всех объектов, кроме тех, которые используются исключительно для определения сложного типа данных. Элемент `Value` элемента `Annotation` может содержать допустимый XML-код из любого пространства имен XML, отличного от ASSL. На эти значения распространяются следующие правила.  
  
-   В XML-коде могут содержаться только элементы.  
  
-   Каждый элемент должен иметь уникальное имя. Рекомендуется, чтобы значение элемента `Name` элемента `Annotation` ссылалось на целевое пространство имен.  
  
 Эти правила применяются для того, чтобы содержимое элемента `Annotation` могло быть представлено как набор пар имен и значений через другие интерфейсы, например объекты DSO.  
  
 Комментарии и пробелы в элементе `Annotation` не сохраняются, если они не были заключены в дочерний элемент. Кроме того, все элементы должны быть доступными для чтения и записи; элементы, доступные только для чтения, будут пропускаться.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>См. также  
 [Объекты &#40;ASSL&#41;](objects-assl.md)  
  
  