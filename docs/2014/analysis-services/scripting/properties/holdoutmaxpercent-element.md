---
title: Элемент HoldoutMaxPercent | Документы Microsoft
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
- HoldoutMaxPercent
helpviewer_keywords:
- HoldoutMaxPercent element
ms.assetid: e375cc51-5f9d-4252-98a1-326ca0dbbf83
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 089ed35d7c900e48da2ba283f8bcf9ee4a29fa7a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096255"
---
# <a name="holdoutmaxpercent-element"></a>Элемент HoldoutMaxPercent
  Указывает максимальный процент вариантов в источнике данных, который будет использоваться для контрольной секции, содержащей проверочный набор элемента [MiningStructure](../objects/miningstructure-element-assl.md) элемента. Оставшиеся варианты используются для обучения. Значение 0 указывает на то, что количество вариантов, которые можно контролировать как проверочные наборы, не ограничено.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxPercent>...</ddl100_100:HoldoutMaxPercent>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|Целое число от 0 до 99.|  
|Значение по умолчанию|30|  
|Количество элементов|0—1: необязательный элемент, который может выполняться только один раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительский элемент|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|Дочерние элементы|None|  
  
## <a name="remarks"></a>Примечания  
 Если указать значения для `HoldoutMaxPercent` и `HoldoutMaxCases`, алгоритм ограничивает проверочный набор до меньшего из двух значений.  
  
 Если элементу `HoldoutMaxCases` присвоено значение по умолчанию 0, а элементу `HoldoutMaxPercent` значение не присвоено, алгоритм использует для обучения весь набор данных.  
  
 Новые свойства `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, или `HoldoutActualSize` доступны только в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и более поздних версиях. Таким образом, к этим свойствам необходимо добавить новое пространство имен, как показано в описании синтаксиса, или службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] вернут ошибку.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не поддерживалось использование контрольных секций в структуре интеллектуального анализа данных. Таким образом, инструкции языка сценариев [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (ASSL), содержащие один из указанных контрольных параметров, а именно `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` или `HoldoutActualSize`, не могут быть использованы в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Если использовать один из этих контрольных параметров в инструкции ASSL в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], то служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
 Элемент, соответствующий родителю параметра `HoldoutMaxPercent` в модели объектов Analysis Management объекты AMO — <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)   
 [Элемент HoldoutMaxCases](holdoutmaxcases-element.md)   
 [Элемент HoldoutSeed](holdoutseed-element.md)   
 [Элемент HoldoutActualSize](holdoutactualsize-element.md)  
  
  