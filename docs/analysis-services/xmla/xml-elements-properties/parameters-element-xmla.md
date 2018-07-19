---
title: Элемент Parameters (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 68366f03168b7c7c434f05e88f512401248c1124
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050451"
---
# <a name="parameters-element-xmla"></a>Элемент Parameters (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Содержит коллекцию элементов [Parameter](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md) , используемых методом [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) .  
  
 **Пространство имен:** `urn:schemas-microsoft-com:xml-analysis`  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Execute>  
...  
   <Parameters>  
      <Parameter>...</Parameter>  
   </Parameters>  
...  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Выполнение](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|Дочерние элементы|[Параметр](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Для некоторых команд (XML для аналитики), таких как [Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) , могут потребоваться дополнительные данные. Элемент **Parameters** обеспечивает механизм предоставления дополнительных данных, включая сведения о фрагментах, для команд XMLA.  
  
 Если в команде XML для аналитики элемент **Parameters** не используется, то при вызове метода **Execute** его можно опустить.  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
