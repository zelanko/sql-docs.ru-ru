---
title: "Элемент NullKeyConvertedToUnknown (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- NullKeyConvertedToUnknown Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NullKeyConvertedToUnknown
helpviewer_keywords:
- NullKeyConvertedToUnknown element
ms.assetid: 1a6cde33-01ba-4095-b464-16d1ad3c6905
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77c93a56563f621d357943348cf436846f213068
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="nullkeyconvertedtounknown-element-assl"></a>Элемент NullKeyConvertedToUnknown (ASSL)
  Определяет действие, которое следует выполнять при возникновении ошибки преобразования значения NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <NullKeyConvertedToUnknown>...</NullKeyConvertedToUnknown>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Пропустить ошибку*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Ошибки преобразования NULL возникают, если в ключевом столбце обнаруживается значение NULL и интерпретируется как элемент **Unknown** . Тем не менее, эта ошибка возникает только в том случае, если [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md) элемент для [DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md) предком **ErrorConfiguration** родительского элемента имеет значение  *UnknownMember*.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Пропустить ошибку*|При обработке ошибка не учитывается и обработка продолжается.|  
|*Сообщить и продолжить*|При обработке создается отчет об ошибке и обработка продолжается.|  
|*Сообщить и остановить выполнение*|При обработке создается отчет об ошибке и обработка прерывается.|  
  
 Перечисление, соответствующее разрешенным значениям для **NullKeyConvertedToUnknown** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент ErrorConfiguration &#40; ASSL &#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)   
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

