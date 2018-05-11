---
title: Элемент KeyNotFound (ASSL) | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e90452cb0b40dac2ce285cf0058ed820bff9c0dd
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="keynotfound-element-assl"></a>Элемент KeyNotFound (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает, каким образом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] при обнаружении ошибки ссылочной целостности.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyNotFound>...</KeyNotFound>  
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
 Ошибки, связанные с нарушением ссылочной целостности, возникают, если значению внешнего ключа в зависимой таблице не соответствует ни одно значение первичного ключа в родительской таблице. Эта ошибка возникает при обработке службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] измерения, в котором таблица фактов ссылается на значение внешнего ключа, не существующее в таблице измерения для этого измерения, или если в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] обрабатывается секция, притом, что главная таблица измерения для измерения, которое входит в состав этой секции, ссылается на значение ключа, отсутствующее в другой связанной с ней таблице измерения. (В случае измерений с иерархиями типа «родители-потомоки» и родительскими атрибутами это может также происходить, если таблица главного измерения для измерения, которое включено в секцию, ссылается на значение ключа, не существующее в той же таблице измерения.)  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Пропустить ошибку*|При обработке эту ошибку следует пропускать и продолжать выполнение.|  
|*Сообщить и продолжить*|При обработке следует создать отчет об этой ошибке и продолжать выполнение.|  
|*Сообщить и остановиться*|При обработке следует создать отчет об этой ошибке и прервать выполнение.|  
  
 Перечисление, соответствующее разрешенным значениям для **KeyNotFound** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
