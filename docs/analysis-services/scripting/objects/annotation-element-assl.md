---
title: Элемент annotation (ASSL) | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 882e3a5521a8f4359c770c7fba129418ec5620fa
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="annotation-element-assl"></a>Элемент Annotation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Родительские элементы|[Заметки](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
|Дочерние элементы|[Имя](../../../analysis-services/scripting/properties/name-element-assl.md), [значение](../../../analysis-services/scripting/properties/value-element-assl.md), [видимость](../../../analysis-services/scripting/properties/visibility-element-assl.md)|  
  
## <a name="remarks"></a>Замечания  
 **Заметки** элемент предоставляет возможность расширения схемы ASSL для всех объектов, отличных от тех, которые используются исключительно для определения сложного типа данных. **Значение** элемент **заметки** элемент может содержать допустимый XML-код из любого пространства имен XML отличного от ASSL применяются следующие правила:  
  
-   В XML-коде могут содержаться только элементы.  
  
-   Каждый элемент должен иметь уникальное имя. Рекомендуется значение **имя** элемент **заметки** элемент ссылается на целевое пространство имен.  
  
 Эти правила применяются к позволяют содержимое **заметки** пары элемент должен быть предоставлен как набор имен и значений через другие интерфейсы, такие как объекты поддержки принятия решений (DSO).  
  
 Комментарии и пробелы в **заметки** невозможно сохранить элемент не были заключены в дочерний элемент. Кроме того, все элементы должны быть доступными для чтения и записи; элементы, доступные только для чтения, будут пропускаться.  
  
 Соответствующий элемент в объектной модели Analysis Management объекты AMO — это <xref:Microsoft.AnalysisServices.Annotation>.  
  
## <a name="see-also"></a>См. также  
 [Объекты & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
