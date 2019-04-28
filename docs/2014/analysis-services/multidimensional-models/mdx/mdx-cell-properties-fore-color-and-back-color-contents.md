---
title: Свойства ячеек FORE_COLOR и Back_color (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17b4bf37eef74824c51a81b97f8b2e5b204df3c0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62725428"
---
# <a name="forecolor-and-backcolor-contents-mdx"></a>Свойства ячеек FORE_COLOR и BACK_COLOR (многомерные выражения)
  Свойства ячеек `FORE_COLOR` и `BACK_COLOR` хранят сведения о цвете соответственно текста и фона ячеек в формате операционной системы Microsoft Windows RGB (красный-зеленый-синий).  
  
 Допустимый диапазон обычных RGB-цветов: от нуля (0) до 16777215 (&H00FFFFFF). Старший байт числа в этом диапазоне всегда равен 0, следующие 3 байта (в порядке старшинства) определяют интенсивность красного, зеленого и синего компонентов соответственно. Интенсивность красного, зеленого и синего компонентов выражается числом от 0 до 255 (&HFF).  
  
## <a name="see-also"></a>См. также  
 [Использование свойств ячеек (многомерные выражения)](mdx-cell-properties-using-cell-properties.md)  
  
  
