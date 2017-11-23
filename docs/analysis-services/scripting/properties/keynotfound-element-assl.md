---
title: "Элемент KeyNotFound (ASSL) | Документы Microsoft"
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
apiname: KeyNotFound Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: KeyNotFound
helpviewer_keywords: KeyNotFound element
ms.assetid: 2a93bbfa-2409-4e94-8b68-926532895a4c
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 72ebb26afc343b771e32087e9d68f4978cdaedc8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="keynotfound-element-assl"></a>Элемент KeyNotFound (ASSL)
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
  
## <a name="remarks"></a>Замечания  
 Ошибки, связанные с нарушением ссылочной целостности, возникают, если значению внешнего ключа в зависимой таблице не соответствует ни одно значение первичного ключа в родительской таблице. Эта ошибка возникает при обработке службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] измерения, в котором таблица фактов ссылается на значение внешнего ключа, не существующее в таблице измерения для этого измерения, или если в [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] обрабатывается секция, притом, что главная таблица измерения для измерения, которое входит в состав этой секции, ссылается на значение ключа, отсутствующее в другой связанной с ней таблице измерения. (В случае измерений с иерархиями типа «родители-потомоки» и родительскими атрибутами это может также происходить, если таблица главного измерения для измерения, которое включено в секцию, ссылается на значение ключа, не существующее в той же таблице измерения.)  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Пропустить ошибку*|При обработке эту ошибку следует пропускать и продолжать выполнение.|  
|*Сообщить и продолжить*|При обработке следует создать отчет об этой ошибке и продолжать выполнение.|  
|*Сообщить и остановить выполнение*|При обработке следует создать отчет об этой ошибке и прервать выполнение.|  
  
 Перечисление, соответствующее разрешенным значениям для **KeyNotFound** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
