---
title: Элемент NullKeyConvertedToUnknown (ASSL) | Документы Microsoft
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
- NullKeyConvertedToUnknown Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullKeyConvertedToUnknown
helpviewer_keywords:
- NullKeyConvertedToUnknown element
ms.assetid: 1a6cde33-01ba-4095-b464-16d1ad3c6905
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8e11f7de1b3fa7b11774a960351a1b3c974ce4f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195252"
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Ошибки преобразования NULL возникают, если в ключевом столбце обнаруживается значение NULL и интерпретируется как элемент `Unknown`. Тем не менее, эта ошибка возникает только в том случае, если [NullProcessing](nullprocessing-element-assl.md) элемент для [DataItem](../data-type/dataitem-data-type-assl.md) предком `ErrorConfiguration` родительского элемента имеет значение *UnknownMember*.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Пропустить ошибку*|При обработке ошибка не учитывается и обработка продолжается.|  
|*Сообщить и продолжить*|При обработке создается отчет об ошибке и обработка продолжается.|  
|*Сообщить и остановить выполнение*|При обработке создается отчет об ошибке и обработка прерывается.|  
  
 Перечисление, соответствующее допустимым значениям элемента `NullKeyConvertedToUnknown` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>См. также  
 [Элемент ErrorConfiguration &#40;ASSL&#41;](../objects/errorconfiguration-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  