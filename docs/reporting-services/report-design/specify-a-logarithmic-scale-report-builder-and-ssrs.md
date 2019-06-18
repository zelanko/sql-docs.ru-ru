---
title: Задание логарифмической шкалы (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d3a3e94111a11380b86ec3127d7a1c9641f20b44
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65570816"
---
# <a name="specify-a-logarithmic-scale-report-builder-and-ssrs"></a>Задание логарифмической шкалы (построитель отчетов и службы SSRS)
  Если данные пропорциональны логарифму, в диаграмме в отчете с разбиением на страницы [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] можно использовать логарифмическую шкалу. Это может улучшить внешний вид диаграммы и повысить удобство работы с данными. Большинство логарифмических шкал использует логарифм с основанием 10.  
  
 Эта функция доступна только для оси значений. Ось значений обычно является вертикальной осью (осью Y). Однако в линейчатых диаграммах это горизонтальная ось (ось X).  
  
 Если ось логарифмическая, все остальные ее свойства будут логарифмически масштабированы. Например, если задать на оси логарифмическую шкалу с основанием 10, установка интервала шкалы, равного 2, на самом деле создаст интервалы, равные 10 в степени 2, то есть 100. Это означает, что будут отображены значения осей 1, 100, 10000, а не значения по умолчанию 1, 10, 100, 1000, 10000.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-a-logarithmic-scale"></a>Задание логарифмической шкалы  
  
1.  Щелкните правой кнопкой мыши ось Y диаграммы и выберите пункт **Свойства вертикальной оси**. Откроется диалоговое окно **Свойства вертикальной оси** .  
  
2.  В поле **Свойства оси**выберите **Использовать логарифмическую шкалу**.  
  
3.  В текстовом поле **Основание логарифма** введите положительное значение для основания логарифма. Если значение не задано, по умолчанию берется логарифм с основанием 10.  
  
## <a name="see-also"></a>См. также:  
 [Форматирование меток оси на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Форматирование диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Форматирование меток оси в виде значений даты или валюты &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
