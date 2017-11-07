---
title: "Свойства ячеек FORE_COLOR и Back_color (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FORE_COLOR contents
- backgrounds [MDX]
- cells [MDX]
- colors [MDX]
- storing cell color information
- cell backgrounds
- BACK_COLOR contents
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e3372c17e261017ea48d834dfc38c509d8fd98fb
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-cell-properties---forecolor-and-backcolor-contents"></a>Свойства ячеек MDX - FORE_COLOR и Back_color
  Свойства ячеек **FORE_COLOR** и **BACK_COLOR** хранят сведения о цвете соответственно текста и фона ячеек в формате операционной системы Microsoft Windows RGB (красный-зеленый-синий).  
  
 Допустимый диапазон обычных RGB-цветов: от нуля (0) до 16777215 (&H00FFFFFF). Старший байт числа в этом диапазоне всегда равен 0, следующие 3 байта (в порядке старшинства) определяют интенсивность красного, зеленого и синего компонентов соответственно. Интенсивность красного, зеленого и синего компонентов выражается числом от 0 до 255 (&HFF).  
  
## <a name="see-also"></a>См. также  
 [Использование свойств ячеек &#40;многомерные выражения&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)  
  
  

