---
title: "Элемент invocation (ASSL) | Документы Microsoft"
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
apiname: Invocation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Invocation
helpviewer_keywords: Invocation element
ms.assetid: f6bf64ad-ae57-4d46-bf92-1d07a65378bb
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8e83bb6a69802c2a4aa39108712661d6e7f1c692
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="invocation-element-assl"></a>Элемент Invocation (ASSL)
  Указывает, каким образом [действия](../../../analysis-services/scripting/objects/action-element-assl.md) должны вызываться.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Action>  
   ...  
   <Invocation>...</Invocation>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String (перечисление)|  
|Значение по умолчанию|*Интерактивный*|  
|Количество элементов|0—1: необязательный элемент, который может появляться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Действие](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Замечания  
 Вызов действия зависит от клиентского приложения. **Вызов** элемент предлагает клиентскому приложению, как должно обрабатываться действие и не указывает на экземпляр [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] способ вызова действия.  
  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*Интерактивный*|Вызывается интерактивно пользователем.|  
|*OnOpen*|Вызывается при открытии объекта клиентским приложением.|  
|*Пакет*|Вызывается командой пакетной обработки.|  
  
 Перечисление, соответствующее разрешенным значениям для **вызов** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>См. также:  
 [Свойства &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
