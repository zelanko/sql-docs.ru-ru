---
title: Элемент HoldoutSeed | Документы Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3e9b38b6fbc552ac46453df8d95d8332f44eb422
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="holdoutseed-element"></a>Элемент HoldoutSeed
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Указывает начальное значение для повторяющейся контрольной секции, содержащей проверочный набор элемента [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) элемента. Это начальное значение обеспечивает сохранение содержимого модели на протяжении повторной обработки. Если не задано или имеет значение 0, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создают начальное значение посредством применения хэш-алгоритма имя структуры интеллектуального анализа данных.  
  
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
|Родительский элемент|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 При первом создании структуры интеллектуального анализа данных ее идентификатор совпадает с именем. Однако имя структуры интеллектуального анализа данных можно изменить. Поэтому, если необходимо обеспечить повторяемость секции, в качестве начального значения не следует использовать основанное на имени значение, а должны задавать его явным образом.  
  
 Кроме того, при создании копии структуры интеллектуального анализа данных с помощью **Экспорт** инструкции [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] сохраняют имя новой структуры интеллектуального анализа данных, но автоматически формируют новый идентификатор. В результате одновременно могут существовать две структуры интеллектуального анализа данных с одинаковым именем, но разными идентификаторами. Для всех структур интеллектуального анализа данных с одинаковыми именами будут созданы одинаковые начальные значения. Тем не менее, поскольку секционирование данных также выполняется в зависимости от исходных данных, фактическое содержимое секций может быть различным.  
  
 Новые свойства **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, или **HoldoutActualSize** доступны только в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и более поздних версиях. Таким образом, к этим свойствам необходимо добавить новое пространство имен, как показано в описании синтаксиса, или служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
 **Примечание** в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не поддерживает использование контрольных секций в структуре интеллектуального анализа данных. Таким образом [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] инструкций языка сценариев (ASSL), которые содержат контрольные параметры **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, или **HoldoutActualSize** не может использоваться в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Если использовать один из этих контрольных параметров в инструкции ASSL в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], то служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
 Элемент, соответствующий родителю параметра **HoldoutSeed** в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Элемент HoldoutActualSize](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)   
 [Элемент HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)   
 [Элемент HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)  
  
  
