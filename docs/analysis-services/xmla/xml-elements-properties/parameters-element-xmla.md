---
title: "Элемент Parameters (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Parameters Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameters
- urn:schemas-microsoft-com:xml-analysis#Parameters
- microsoft.xml.analysis.parameters
helpviewer_keywords:
- Parameters element
ms.assetid: d46454a1-a1d1-4aa8-95ea-54be22a53e83
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 27bf966c1a1fb44c547a74f38cc3cddd6399793c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="parameters-element-xmla"></a>Элемент Parameters (XML для аналитики)
  Содержит коллекцию элементов [Parameter](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md) , используемых методом [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) .  
  
 **Пространство имен:**`urn:schemas-microsoft-com:xml-analysis`  
  
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
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Выполнение](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|Дочерние элементы|[Параметр](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 Для некоторых команд (XML для аналитики), таких как [Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) , могут потребоваться дополнительные данные. Элемент **Parameters** обеспечивает механизм предоставления дополнительных данных, включая сведения о фрагментах, для команд XMLA.  
  
 Если в команде XML для аналитики элемент **Parameters** не используется, то при вызове метода **Execute** его можно опустить.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

