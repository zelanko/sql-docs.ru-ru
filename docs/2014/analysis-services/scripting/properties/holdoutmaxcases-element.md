---
title: Элемент HoldoutMaxCases | Документы Microsoft
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
- HoldoutMaxCases
helpviewer_keywords:
- HoldoutMaxCases element
ms.assetid: 58d94d10-e11e-4368-b3b8-dff23e1947cd
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 083ff97f8d739f4f970a6fec8a5c7353b43b5763
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192982"
---
# <a name="holdoutmaxcases-element"></a>Элемент HoldoutMaxCases
  Указывает максимальное число вариантов в источнике данных для контрольной секции, содержащей проверочный набор элемента [MiningStructure](../objects/miningstructure-element-assl.md) элемента. Остающиеся варианты в наборе данных используются для обучения. Значение 0 указывает на то, что количество вариантов, которые можно контролировать как проверочные наборы, не ограничено.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxCases>...</ddl100_100:HoldoutMaxCases>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целое число больше 0.|  
|Значение по умолчанию|0|  
|Количество элементов|0—1: необязательный элемент, который может выполняться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если указать значения для `HoldoutMaxPercent` и `HoldoutMaxCases`, алгоритм ограничивает проверочный набор до меньшего из двух значений.  
  
 Если элементу `HoldoutMaxCases` присвоено значение по умолчанию 0, а элементу `HoldoutMaxPercent` значение не присвоено, алгоритм использует для обучения весь набор данных.  
  
 Новые свойства `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, или `HoldoutActualSize` доступны только в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и более поздних версиях. Таким образом, к этим свойствам необходимо добавить новое пространство имен, как показано в описании синтаксиса, или служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не поддерживалось использование контрольных секций в структуре интеллектуального анализа данных. Таким образом, инструкции языка сценариев [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (ASSL), содержащие один из указанных контрольных параметров, а именно `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` или `HoldoutActualSize`, не могут быть использованы в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Если использовать один из этих контрольных параметров в инструкции ASSL в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], то служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
 Элемент, соответствующий родителю параметра `HoldoutMaxCases` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)   
 [Элемент HoldoutMaxPercent](holdoutmaxpercent-element.md)   
 [Элемент HoldoutSeed](holdoutseed-element.md)   
 [Элемент HoldoutActualSize](holdoutactualsize-element.md)  
  
  