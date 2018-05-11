---
title: Элемент Parameter (XML для Аналитики) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ca615a3ca71d025d95fc56c2d4ec8253b7ce2ba
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="parameter-element-xmla"></a>Элемент Parameter (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит имя и значение параметра, используемого методом [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Parameters>  
...  
   <Parameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </Parameter>  
...  
</Parameters>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Параметры](../../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md)|  
|Дочерние элементы|[Name](../../../analysis-services/xmla/xml-elements-properties/name-element-parameter-xmla.md), [Value](../../../analysis-services/xmla/xml-elements-properties/value-element-parameter-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Для некоторых команд (XML для аналитики), таких как [Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) , могут потребоваться дополнительные данные. Элемент **Parameter** обеспечивает механизм предоставления дополнительных данных, включая сведения о фрагментах, для команд XMLA.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; XML для Аналитики & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
