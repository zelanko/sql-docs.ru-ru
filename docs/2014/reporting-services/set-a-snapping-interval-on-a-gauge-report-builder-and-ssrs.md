---
title: Установка интервала привязки в датчике (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0ece7297-6e2f-47fb-835d-b9e9cce53fe2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e2a35e4d6fefb6830774ffd7b2c3bc13a5e097c
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66101365"
---
# <a name="set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs"></a>Установка интервала привязки в датчике (построитель отчетов и службы SSRS)
  Интервал привязки определяет кратную величину, до которой округляются значения. По умолчанию датчик указывает на точное значение поля, заданное на панели данных. Однако может потребоваться округлить точное значение в ту или иную сторону, чтобы указатель был привязан к заранее заданному интервалу. Например, если значение на датчике равно 34,2 и указан интервал привязки 5, указатель датчика будет указывать значение 35. Если значение на датчике равно 31,2 и указан интервал привязки 5, указатель датчика будет указывать значение 30.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-snapping-interval-on-a-gauge"></a>Установка интервала привязки в датчике  
  
1.  Щелкните любое число датчика, чтобы выделить шкалу.  
  
2.  Откройте панель «Свойства».  
  
    > [!NOTE]  
    >  Если панель свойств не видна, щелкните **представление** , а затем — **свойства** флажок.  
  
3.  В **указатели** свойство, нажмите кнопку (...). Откроется окно редактора коллекции указателей.  
  
4.  Задайте **SnappingEnabled** свойства `True`.  
  
5.  Задайте **SnappingInterval** которого является значение, представляющее интервал привязки. Указатель будет привязан к ближайшей кратной величине указанного значения.  
  
## <a name="see-also"></a>См. также  
 [Форматирование шкал на датчике (построитель отчетов и службы SSRS)](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Форматирование указателей на датчике &#40;построитель отчетов и службы SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Датчики (построитель отчетов и службы SSRS)](report-design/gauges-report-builder-and-ssrs.md)  
  
  
