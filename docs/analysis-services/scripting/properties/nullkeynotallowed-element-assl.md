---
title: Элемент NullKeyNotAllowed (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0a7d499729efa4e9079fb01c864faf1f2a21f75d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="nullkeynotallowed-element-assl"></a>Элемент NullKeyNotAllowed (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
## <a name="remarks"></a>Примечания  
 Ошибки ключа NULL возникают при обнаружении значения NULL в ключевом столбце, в котором не допускаются значения NULL, и приводят к пропуску соответствующей записи в процессе обработки. Тем не менее, эта ошибка возникает только в том случае, если [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md) элемент для **DataItem** предком **ErrorConfiguration** родительского элемента имеет значение  *Ошибка*.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Пропустить ошибку*|При обработке ошибка не учитывается и обработка продолжается.|  
|*Сообщить и продолжить*|При обработке создается отчет об ошибке и обработка продолжается.|  
|*Сообщить и остановить выполнение*|При обработке создается отчет об ошибке и обработка прерывается.|  
  
 Перечисление, соответствующее разрешенным значениям для **NullKeyNotAllowed** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>См. также  
 [Элемент ErrorConfiguration &#40;ASSL&#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)  
  
  
