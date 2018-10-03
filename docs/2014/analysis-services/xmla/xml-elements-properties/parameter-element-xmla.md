---
title: Элемент Parameter (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Parameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Parameter
- microsoft.xml.analysis.parameter
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameter
helpviewer_keywords:
- Parameter element
ms.assetid: fe31ac3d-a3e8-4f60-a81a-c43271ddbed4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7638e033cab8f940972b35ea6c7a7a4abb402ee3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079262"
---
# <a name="parameter-element-xmla"></a>Элемент Parameter (XML для аналитики)
  Содержит имя и значение параметра, используемого методом [Execute](../xml-elements-methods-execute.md) .  
  
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Параметры](parameters-element-xmla.md)|  
|Дочерние элементы|[Name](name-element-parameter-xmla.md), [Value](value-element-parameter-xmla.md)|  
  
## <a name="remarks"></a>Примечания  
 Для некоторых команд (XML для аналитики), таких как [Process](../xml-elements-commands/process-element-xmla.md) , могут потребоваться дополнительные данные. Элемент `Parameter` обеспечивает механизм предоставления дополнительных данных, включая сведения о фрагментах, для команд XMLA.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;XML для Аналитики&#41;](xml-elements-properties.md)  
  
  
