---
title: "Свойства ячеек FORE_COLOR и Back_color (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
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
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1c39713f66b15fcf959f6ba3887b7002cd7a2863
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="mdx-cell-properties---forecolor-and-backcolor-contents"></a>Свойства ячеек MDX - FORE_COLOR и Back_color
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]**FORE_COLOR** и **BACK_COLOR** свойства ячейки хранения цвет шрифта для текста и фона ячеек, соответственно, в формате (RGB) красный зеленый синий операционной системы Microsoft Windows .  
  
 Допустимый диапазон обычных RGB-цветов: от нуля (0) до 16777215 (&H00FFFFFF). Старший байт числа в этом диапазоне всегда равен 0, следующие 3 байта (в порядке старшинства) определяют интенсивность красного, зеленого и синего компонентов соответственно. Интенсивность красного, зеленого и синего компонентов выражается числом от 0 до 255 (&HFF).  
  
## <a name="see-also"></a>См. также  
 [Использование свойств ячеек (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)  
  
  
