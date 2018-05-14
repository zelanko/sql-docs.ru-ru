---
title: Элемент Member (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3ef62ab60f54f8bb9f4590ca6bbe2d1a7893399e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="member-element-xmla"></a>Элемент Member (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Представляет собой отдельный элемент родительского элемента [Members](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md) или [Tuple](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Members>  
   ...  
   <Member>  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Members>  
<!-- or -->  
<Tuple>  
   ...  
   <Member Hierarchy="string">  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Tuple>  
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
|Родительские элементы|[Members](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md), [Tuple](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)|  
|Дочерние элементы|[Caption](../../../analysis-services/xmla/xml-elements-properties/caption-element-xmla.md), [DisplayInfo](../../../analysis-services/xmla/xml-elements-properties/displayinfo-element-xmla.md), [LName](../../../analysis-services/xmla/xml-elements-properties/lname-element-xmla.md), [LNum](../../../analysis-services/xmla/xml-elements-properties/lnum-element-xmla.md), [UName](../../../analysis-services/xmla/xml-elements-properties/uname-element-xmla.md)|  
  
## <a name="attributes"></a>Атрибуты  
  
|Attribute|Описание|  
|---------------|-----------------|  
|Иерархия|Обязательный атрибут типа **String** (только для родительских элементов **Tuple** ). Имя иерархии, которой принадлежат члены, представленные элементом **Member** .|  
  
## <a name="remarks"></a>Примечания  
 Элемент **Member** содержит сведения, необходимые для определения и отображения элементов в рамках заданной иерархии. Для родительских элементов **Members** иерархия уже задана атрибутом **Hierarchy** родительского элемента. Для родительских элементов **Tuple** иерархия задается при помощи атрибута **Hierarchy** элемента **Member** .  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
