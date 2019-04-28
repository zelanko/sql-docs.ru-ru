---
title: Свойства ячеек FORE_COLOR и Back_color (многомерные Выражения) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bb721d04e32e584a312c779db3aadab2ab83ba19
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806141"
---
# <a name="mdx-cell-properties---forecolor-and-backcolor-contents"></a>Свойства ячеек многомерных выражений — содержимое FORE_COLOR и BACK_COLOR
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Свойства ячеек **FORE_COLOR** и **BACK_COLOR** хранят сведения о цвете соответственно текста и фона ячеек в формате операционной системы Microsoft Windows RGB (красный-зеленый-синий).  
  
 Допустимый диапазон обычных RGB-цветов: от нуля (0) до 16777215 (&H00FFFFFF). Старший байт числа в этом диапазоне всегда равен 0, следующие 3 байта (в порядке старшинства) определяют интенсивность красного, зеленого и синего компонентов соответственно. Интенсивность красного, зеленого и синего компонентов выражается числом от 0 до 255 (&HFF).  
  
## <a name="see-also"></a>См. также  
 [Использование свойств ячеек (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)  
  
  
