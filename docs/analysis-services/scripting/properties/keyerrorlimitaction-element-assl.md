---
title: Элемент KeyErrorLimitAction (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b154c9724ab96cea713437d3fe8ccecb9d0913b5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="keyerrorlimitaction-element-assl"></a>Элемент KeyErrorLimitAction (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает действие [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] предпринимать, когда количество ошибок ключа, который указывается в [KeyErrorLimit](../../../analysis-services/scripting/properties/keyerrorlimit-element-assl.md) достигнут элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyErrorLimitAction>...</KeyErrorLimitAction>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*StopProcessing*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*StopProcessing*|Остановка обработки объекта.|  
|*StopLogging*|Продолжение обработки объекта, но остановка ведения журнала ошибок, возникающих во время обработки.|  
  
 Перечисление, соответствующее разрешенным значениям для **KeyErrorLimitAction** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.KeyErrorLimitAction>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
