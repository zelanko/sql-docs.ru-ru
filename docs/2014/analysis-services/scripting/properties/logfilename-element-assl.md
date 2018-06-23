---
title: Элемент LogFileName (ASSL) | Документы Microsoft
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
- LogFileName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LogFileName
helpviewer_keywords:
- LogFileName element
ms.assetid: 80c7530d-ef73-44c3-88b5-c11c0f290946
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e3038ae45e740b52662f6e580808096541b7b386
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191069"
---
# <a name="logfilename-element-assl"></a>Элемент LogFileName (ASSL)
  Содержит имя файла для файла журнала [трассировки](../objects/trace-element-assl.md) элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Trace>  
   ...  
   <LogFileName>...</LogFileName>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|String|  
|Значение по умолчанию|None|  
|Количество элементов|0-1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[Trace](../objects/trace-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Файл журнала сохраняется в папке журнала экземпляра [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Элемент, соответствующий родителю параметра `LogFileName` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>См. также  
 [Отслеживает элемент &#40;ASSL&#41;](../collections/traces-element-assl.md)   
 [Свойства &#40;ASSL&#41;](properties-assl.md)  
  
  