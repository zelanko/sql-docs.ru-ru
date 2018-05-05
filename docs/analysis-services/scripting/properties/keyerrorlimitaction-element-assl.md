---
title: Элемент KeyErrorLimitAction (ASSL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- KeyErrorLimitAction Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- KeyErrorLimitAction
helpviewer_keywords:
- KeyErrorLimitAction element
ms.assetid: a2a01aae-0571-499f-9025-b61c741f3ddb
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f1279a7d9da7e96256ccd34fc5c4085adddf549d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Замечания  
 Значением этого элемента может быть только одна из строк в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|*StopProcessing*|Остановка обработки объекта.|  
|*StopLogging*|Продолжение обработки объекта, но остановка ведения журнала ошибок, возникающих во время обработки.|  
  
 Перечисление, соответствующее разрешенным значениям для **KeyErrorLimitAction** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.KeyErrorLimitAction>.  
  
## <a name="see-also"></a>См. также  
 [Свойства & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
