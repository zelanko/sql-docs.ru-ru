---
title: "Добавление или удаление полей из диаграммы (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 795435899de548848ca64cec26d212fd8a80f900
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="add-or-remove-margins-from-a-chart-report-builder-and-ssrs"></a>Добавление или удаление полей из диаграммы (построитель отчетов и службы SSRS)
В гистограмме и точечной диаграмме в отчетах с разбиением на страницы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] боковые поля автоматически добавляются по краям оси X. В линейчатой диаграмме боковые поля автоматически добавляются по краям оси X. Для всех остальных диаграмм боковые поля не добавляются. Размер поля изменить нельзя.  
  
 Этот раздел не относится к круговым, кольцевым, воронкообразным и пирамидальным диаграммам.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-enable-or-disable-side-margins"></a>Включение или отключение боковых полей  
  
1.  Щелкните правой кнопкой мыши ось и выберите пункт **Свойства оси**. Отображается диалоговое окно свойств **вертикальных** или **горизонтальных осей** .  
  
2.  На странице **Параметры оси** задайте свойство **Боковые поля** :  
  
    -   **Автоматически** — боковое поле добавляется в зависимости от типа диаграммы.  
  
    -   **Отключено** — в линейчатой диаграмме, гистограмме и точечной диаграмме не будет боковых полей.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Форматирование меток оси на диаграмме &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Диалоговое окно «Свойства оси», параметры оси &#40; Построитель отчетов и службы SSRS &#41;](http://msdn.microsoft.com/library/b276e210-7a12-48ae-971b-7dabae51df11)   
 [Укажите интервал оси &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)   
 [Форматирование меток оси в виде даты или валюты &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Диаграммы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
