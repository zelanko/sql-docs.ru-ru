---
title: "Элемент NullKeyNotAllowed (ASSL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
apiname: NullKeyNotAllowed Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: NullKeyNotAllowed
helpviewer_keywords: NullKeyNotAllowed element
ms.assetid: 4ece99eb-954b-4da1-add4-dd9efd5fff0a
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 45ad433dc247749c466f05896a89bc25bee0680d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="nullkeynotallowed-element-assl"></a>Элемент NullKeyNotAllowed (ASSL)
  Определяет, как [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] подсистема обработки обрабатывает ошибку ключа null во время обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ErrorConfiguration>  
   ...  
   <NullKeyNotAllowed>...</NullKeyNotAllowed>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Сообщить и продолжить*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Ошибки ключа NULL возникают при обнаружении значения NULL в ключевом столбце, в котором не допускаются значения NULL, и приводят к пропуску соответствующей записи в процессе обработки. Тем не менее, эта ошибка возникает только в том случае, если [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md) элемент для **DataItem** предком **ErrorConfiguration** родительского элемента имеет значение  *Ошибка*.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Пропустить ошибку*|При обработке ошибка не учитывается и обработка продолжается.|  
|*Сообщить и продолжить*|При обработке создается отчет об ошибке и обработка продолжается.|  
|*Сообщить и остановить выполнение*|При обработке создается отчет об ошибке и обработка прерывается.|  
  
 Перечисление, соответствующее разрешенным значениям для **NullKeyNotAllowed** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>См. также:  
 [Элемент ErrorConfiguration &#40; ASSL &#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)  
  
  
