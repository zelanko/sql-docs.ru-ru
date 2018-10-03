---
title: Элемент HoldoutSeed | Документация Майкрософт
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
- HoldoutSeed
helpviewer_keywords:
- HoldoutSeed element
ms.assetid: 6b608bb3-c075-4744-9722-f5fb9fa1cc7e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b97d88ee83d92d22f72db13d20ce37bb6ea9da08
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097606"
---
# <a name="holdoutseed-element"></a>Элемент HoldoutSeed
  Задает начальное значение для повторяющейся контрольной секции, содержащей проверочный набор элемента [MiningStructure](../objects/miningstructure-element-assl.md) элемент. Это начальное значение обеспечивает сохранение содержимого модели на протяжении повторной обработки. Если не задано или имеет значение 0, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создают начальное значение посредством применения хэш-алгоритма имя структуры интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutSeed>...</ddl100_100:HoldoutSeed>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Long|  
|Значение по умолчанию|0|  
|Количество элементов|0—1: необязательный элемент, который может выполняться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 При первом создании структуры интеллектуального анализа данных ее идентификатор совпадает с именем. Однако имя структуры интеллектуального анализа данных можно изменить. Поэтому, если необходимо обеспечить повторяемость секции, в качестве начального значения не следует использовать основанное на имени значение, а должны задавать его явным образом.  
  
 Кроме того, при создании копии структуры интеллектуального анализа данных с помощью `EXPORT` инструкции [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] сохраняют имя новой структуры интеллектуального анализа данных, но автоматически формируют новый идентификатор. В результате одновременно могут существовать две структуры интеллектуального анализа данных с одинаковым именем, но разными идентификаторами. Для всех структур интеллектуального анализа данных с одинаковыми именами будут созданы одинаковые начальные значения. Тем не менее, поскольку секционирование данных также выполняется в зависимости от исходных данных, фактическое содержимое секций может быть различным.  
  
 Новые свойства `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, или `HoldoutActualSize` доступны только в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и более поздних версий. Таким образом, к этим свойствам необходимо добавить новое пространство имен, как показано в описании синтаксиса, или служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
 **Примечание** в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не поддерживает использование контрольных секций в структуре интеллектуального анализа данных. Таким образом [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] инструкции языка сценариев (ASSL), содержащие указанных контрольных параметров `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, или `HoldoutActualSize` не может использоваться в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Если использовать один из этих контрольных параметров в инструкции ASSL в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], то служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
 Элемент, соответствующий родителю параметра `HoldoutSeed` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)   
 [Элемент HoldoutActualSize](holdoutactualsize-element.md)   
 [Элемент HoldoutMaxPercent](holdoutmaxpercent-element.md)   
 [Элемент HoldoutMaxCases](holdoutmaxcases-element.md)  
  
  
