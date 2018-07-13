---
title: Свойства ячеек FORE_COLOR и Back_color (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8a4909413bb7847d4254020ed2b4135049baaea4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278258"
---
# <a name="forecolor-and-backcolor-contents-mdx"></a>Свойства ячеек FORE_COLOR и BACK_COLOR (многомерные выражения)
  Свойства ячеек `FORE_COLOR` и `BACK_COLOR` хранят сведения о цвете соответственно текста и фона ячеек в формате операционной системы Microsoft Windows RGB (красный-зеленый-синий).  
  
 Допустимый диапазон обычных RGB-цветов: от нуля (0) до 16777215 (&H00FFFFFF). Старший байт числа в этом диапазоне всегда равен 0, следующие 3 байта (в порядке старшинства) определяют интенсивность красного, зеленого и синего компонентов соответственно. Интенсивность красного, зеленого и синего компонентов выражается числом от 0 до 255 (&HFF).  
  
## <a name="see-also"></a>См. также  
 [Свойства ячеек &#40;многомерных Выражений&#41;](mdx-cell-properties-using-cell-properties.md)  
  
  
