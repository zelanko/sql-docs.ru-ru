---
title: Элемент NullKeyNotAllowed (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NullKeyNotAllowed Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NullKeyNotAllowed
helpviewer_keywords:
- NullKeyNotAllowed element
ms.assetid: 4ece99eb-954b-4da1-add4-dd9efd5fff0a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0d17edc031d66282b433571b18ef1c32cf6e09bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054574"
---
# <a name="nullkeynotallowed-element-assl"></a>Элемент NullKeyNotAllowed (ASSL)
  Определяет, каким образом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] подсистема обработки обрабатывает ошибку ключа null во время обработки.  
  
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
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Ошибки ключа NULL возникают при обнаружении значения NULL в ключевом столбце, в котором не допускаются значения NULL, и приводят к пропуску соответствующей записи в процессе обработки. Тем не менее, эта ошибка возникает только в том случае, если [NullProcessing](nullprocessing-element-assl.md) элемент для `DataItem` предком `ErrorConfiguration` родительского элемента имеет значение *ошибка*.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Пропустить ошибку*|При обработке ошибка не учитывается и обработка продолжается.|  
|*Сообщить и продолжить*|При обработке создается отчет об ошибке и обработка продолжается.|  
|*Сообщить и остановить выполнение*|При обработке создается отчет об ошибке и обработка прерывается.|  
  
 Перечисление, соответствующее допустимым значениям элемента `NullKeyNotAllowed` в модели объектов AMO, — это <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>См. также  
 [Элемент ErrorConfiguration &#40;ASSL&#41;](../objects/errorconfiguration-element-assl.md)  
  
  
