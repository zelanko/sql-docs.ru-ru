---
title: "Добавление разрывов шкалы на диаграмму (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84d66436-ed62-4967-bbbd-b457593ee787
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c348bd91264d6e3ea314750da62955378f518e2f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---

# <a name="add-scale-breaks-to-a-chart-report-builder-and-ssrs"></a>Добавление в диаграмму разрывов шкалы (построитель отчетов и службы SSRS)

  Разрыв шкалы представляет собой полосу, нарисованную в области построения диаграммы, обозначающую нарушение непрерывной последовательности изменения значений от малых к большим на оси значений (обычно это вертикальная ось, или ось Y). Разрыв шкалы используется, чтобы отобразить два разных диапазона в одной и той же области диаграммы.  
  
 ![Диаграмма с разрывом шкалы](../../reporting-services/report-design/media/rs-multipledatarangeschart-scalebreak.gif "диаграмма с разрывом шкалы")  
  
> [!NOTE]  
>  Положение разрыва шкалы указать на диаграмме нельзя. Диаграмма на основе значений набора данных самостоятельно вычисляет, где имеется значительный разрыв между диапазонами данных, чтобы поместить разрыв шкалы на оси значений (оси Y) во время выполнения.  
  
 Пример диаграммы с разрывами шкалы доступен в виде образца отчета. Дополнительные сведения о загрузке этого образца и других отчетов см. в разделе [примеры отчетов построителя отчетов и конструктора отчетов](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-scale-breaks-on-the-chart"></a>Включение разрывов шкалы на диаграмме  
  
1.  Щелкните правой кнопкой мыши вертикальную ось и выберите пункт **Свойства оси**. Откроется диалоговое окно **Свойства вертикальной оси** .  
  
2.  Установите флажок **Включить разрывы шкалы** .  
  
### <a name="to-change-the-style-of-the-scale-break"></a>Изменение стиля разрыва шкалы  
  
1.  Откройте панель «Свойства».  
  
2.  В области конструктора щелкните правой кнопкой мыши ось Y диаграммы. На панели «Свойства» будут отображены свойства объекта оси Y (по умолчанию называемой «Ось диаграммы»).  
  
3.  В разделе **Шкала** раскройте свойство ScaleBreakStyle.  
  
4.  Измените значения свойства ScaleBreakStyle, такие как BreakLineType и Spacing. Дополнительные сведения о свойствах разрыва шкалы см. в разделе [Отображение на диаграмме ряда с несколькими диапазонами данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/displaying-a-series-with-multiple-data-ranges-on-a-chart.md).  

## <a name="next-steps"></a>Следующие шаги

[Диаграммы](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[Форматирование диаграммы](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
[Диалоговое окно «Свойства оси», параметры оси](http://msdn.microsoft.com/library/b276e210-7a12-48ae-971b-7dabae51df11)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
