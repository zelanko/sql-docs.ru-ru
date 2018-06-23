---
title: Элемент HoldoutActualSize | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- HoldoutActualSize
helpviewer_keywords:
- HoldoutActualSize element
ms.assetid: 606a6674-cedb-4cee-82d0-26589f084dd9
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fe781b9e3381a97d9ad75440dac40e281881419f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109579"
---
# <a name="holdoutactualsize-element"></a>Элемент HoldoutActualSize
  Отображает фактический размер, после обработки контрольной секции, содержащей проверочный набор элемента [MiningStructure](../objects/miningstructure-element-assl.md) элемента. Остающиеся варианты в наборе данных используются для обучения. Это свойство доступно только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutActualSize>...</ddl100_100:HoldoutActualSize>  
   ...  
</MiningStructure  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целочисленное значение только для чтения.|  
|Значение по умолчанию|Неприменимо|  
|Количество элементов|0—1: необязательный элемент, который может встречаться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Значение для `HoldoutActualSize` зависит от источника данных и значения для [HoldoutMaxCases](holdoutmaxcases-element.md), [HoldoutMaxPercent](holdoutmaxpercent-element.md), и [HoldoutSeed](holdoutseed-element.md). Таким образом, значение `HoldoutActualSize` недоступно, пока службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не завершат обработку структуры интеллектуального анализа данных.  
  
 Элемент, соответствующий родителю параметра `HoldoutActualSize` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не поддерживалось использование контрольных секций в структуре интеллектуального анализа данных. Таким образом, инструкции языка сценариев [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (ASSL), содержащие один из указанных контрольных параметров, а именно `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` или `HoldoutActualSize`, не могут быть использованы в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Если использовать один из этих контрольных параметров в инструкции ASSL в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], то служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)   
 [Элемент HoldoutMaxCases](holdoutmaxcases-element.md)   
 [Элемент HoldoutMaxPercent](holdoutmaxpercent-element.md)   
 [Элемент HoldoutSeed](holdoutseed-element.md)  
  
  