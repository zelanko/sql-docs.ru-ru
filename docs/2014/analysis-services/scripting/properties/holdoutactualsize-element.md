---
title: Элемент HoldoutActualSize | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- HoldoutActualSize
helpviewer_keywords:
- HoldoutActualSize element
ms.assetid: 606a6674-cedb-4cee-82d0-26589f084dd9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8610024c3eb0b3460883fc5eeddb80f057aff86b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096414"
---
# <a name="holdoutactualsize-element"></a>Элемент HoldoutActualSize
  Отображает фактический размер, после обработки, контрольной секции, содержащей проверочный набор элемента [MiningStructure](../objects/miningstructure-element-assl.md) элемент. Остающиеся варианты в наборе данных используются для обучения. Это свойство доступно только для чтения.  
  
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
  
 Элемент, соответствующий родителю параметра `HoldoutActualSize` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не поддерживалось использование контрольных секций в структуре интеллектуального анализа данных. Таким образом, инструкции языка сценариев [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (ASSL), содержащие один из указанных контрольных параметров, а именно `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` или `HoldoutActualSize`, не могут быть использованы в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Если использовать один из этих контрольных параметров в инструкции ASSL в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], то служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)   
 [Элемент HoldoutMaxCases](holdoutmaxcases-element.md)   
 [Элемент HoldoutMaxPercent](holdoutmaxpercent-element.md)   
 [Элемент HoldoutSeed](holdoutseed-element.md)  
  
  
