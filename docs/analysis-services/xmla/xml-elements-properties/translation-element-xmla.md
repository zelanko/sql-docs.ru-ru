---
title: Элемент Translation (XMLA) | Документация Майкрософт
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8b6c50664cdce599128be9f0ad15a10e33b77ec6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38047188"
---
# <a name="translation-element-xmla"></a>Элемент Translation (XML для аналитики)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Определяет перевод для элемента атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Translations>  
   ...  
   <Translation>  
      <Language>...</Language>  
      <Name>...</Name>  
   </Translation>  
   ...  
</Translations>  
```  
  
## <a name="element-characteristics"></a>Характеристики элементов  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элементов  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Преобразования](../../../analysis-services/xmla/xml-elements-properties/translations-element-xmla.md)|  
|Дочерние элементы|[Language](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md), [Name](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Элемент **Translation** определяет сведения, необходимые для связи элемента атрибута с переводом, определенным для данного атрибута, во время выполнения команды [Insert](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) или [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md) .  
  
## <a name="see-also"></a>См. также
 [Свойства &#40;XML для Аналитики&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
