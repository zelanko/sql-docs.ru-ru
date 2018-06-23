---
title: Установка интервала привязки в датчике (построитель отчетов и службы SSRS) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ece7297-6e2f-47fb-835d-b9e9cce53fe2
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 4ce2f81ddb04c088c909e07f6d842f53c35b3974
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101949"
---
# <a name="set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs"></a>Установка интервала привязки в датчике (построитель отчетов и службы SSRS)
  Интервал привязки определяет кратную величину, до которой округляются значения. По умолчанию датчик указывает на точное значение поля, заданное на панели данных. Однако может потребоваться округлить точное значение в ту или иную сторону, чтобы указатель был привязан к заранее заданному интервалу. Например, если значение на датчике равно 34,2 и указан интервал привязки 5, указатель датчика будет указывать значение 35. Если значение на датчике равно 31,2 и указан интервал привязки 5, указатель датчика будет указывать значение 30.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-snapping-interval-on-a-gauge"></a>Установка интервала привязки в датчике  
  
1.  Щелкните любое число датчика, чтобы выделить шкалу.  
  
2.  Откройте панель «Свойства».  
  
    > [!NOTE]  
    >  Если вы не видите панели «свойства», нажмите кнопку **представление** и затем выберите **свойства** флажок.  
  
3.  В **указатели** свойства, нажмите кнопку (...). Откроется окно редактора коллекции указателей.  
  
4.  Задать **SnappingEnabled** свойства `True`.  
  
5.  Задать **SnappingInterval** значение, представляющее интервал привязки. Указатель будет привязан к ближайшей кратной величине указанного значения.  
  
## <a name="see-also"></a>См. также  
 [Форматирование шкал на датчике (построитель отчетов и службы SSRS)](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Форматирование указателей на датчике &#40;построитель отчетов и службы SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Датчики (построитель отчетов и службы SSRS)](report-design/gauges-report-builder-and-ssrs.md)  
  
  