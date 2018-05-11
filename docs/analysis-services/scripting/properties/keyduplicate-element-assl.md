---
title: Элемент KeyDuplicate (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b236a148c28d8e4135bcc6b5bff0592934abc6f1
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="keyduplicate-element-assl"></a>Элемент KeyDuplicate (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Определяет, каким образом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ошибок повторения ключей при их обнаружении во время обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyDuplicate>...</KeyDuplicate>  
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
  
## <a name="remarks"></a>Примечания  
 Ошибки с повторяющимися значениями ключа возникают только во время обработки измерения, когда ключ атрибута появляется больше одного раза. Поскольку ключи атрибутов должны быть уникальны, службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] удаляют повторяющиеся записи. Ошибки с повторяющимися значениями ключа обычно свидетельствуют о дефектах модели измерения, в частности в связях между ее атрибутами.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Пропустить ошибку*|При обработке эту ошибку следует пропускать и продолжать выполнение.|  
|*Сообщить и продолжить*|При обработке следует создать отчет об этой ошибке и продолжать выполнение.|  
|*Сообщить и остановиться*|При обработке следует создать отчет об этой ошибке и прервать выполнение.|  
  
 Перечисление, соответствующее разрешенным значениям для **KeyDuplicate** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
