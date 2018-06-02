---
title: Элемент SkippedLevels (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3813ea7fd0d4936c458487ade9a3d81ad87ce09d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576306"
---
# <a name="skippedlevels-element-xmla"></a>Элемент SkippedLevels (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит число уровней, пропущенных элементом атрибута, представленного родительским элементом [Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Attribute>  
   ...  
   <SkippedLevels>...</SkippedLevels>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленный|  
|Значение по умолчанию|0|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Элемент **SkippedLevels** определяет количество уровней, пропущенных элементом атрибута, определенного родительским элементом **Attribute** .  
  
## <a name="see-also"></a>См. также
 [Элемент INSERT &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Элемент Update &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
