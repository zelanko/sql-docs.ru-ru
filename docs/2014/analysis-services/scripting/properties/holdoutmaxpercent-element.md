---
title: Элемент HoldoutMaxPercent | Документация Майкрософт
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
- HoldoutMaxPercent
helpviewer_keywords:
- HoldoutMaxPercent element
ms.assetid: e375cc51-5f9d-4252-98a1-326ca0dbbf83
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8ef3a056404f350ea8b9bfe5d369b9091bad0de9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140274"
---
# <a name="holdoutmaxpercent-element"></a>Элемент HoldoutMaxPercent
  Указывает максимальную процентную долю вариантов в источнике данных, который будет использоваться для контрольной секции, содержащей проверочный набор элемента [MiningStructure](../objects/miningstructure-element-assl.md) элемент. Оставшиеся варианты используются для обучения. Значение 0 указывает на то, что количество вариантов, которые можно контролировать как проверочные наборы, не ограничено.  
  
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
  
 Новые свойства `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, или `HoldoutActualSize` доступны только в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] и более поздних версий. Таким образом, к этим свойствам необходимо добавить новое пространство имен, как показано в описании синтаксиса, или службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] вернут ошибку.  
  
> [!NOTE]  
>  В [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] не поддерживалось использование контрольных секций в структуре интеллектуального анализа данных. Таким образом, инструкции языка сценариев [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (ASSL), содержащие один из указанных контрольных параметров, а именно `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` или `HoldoutActualSize`, не могут быть использованы в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Если использовать один из этих контрольных параметров в инструкции ASSL в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], то служба [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] возвратит ошибку.  
  
 Элемент, соответствующий родителю параметра `HoldoutMaxPercent` в объекты управления Analysis AMO объектной модели это <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>См. также  
 [Свойства &#40;ASSL&#41;](properties-assl.md)   
 [Элемент HoldoutMaxCases](holdoutmaxcases-element.md)   
 [Элемент HoldoutSeed](holdoutseed-element.md)   
 [Элемент HoldoutActualSize](holdoutactualsize-element.md)  
  
  
