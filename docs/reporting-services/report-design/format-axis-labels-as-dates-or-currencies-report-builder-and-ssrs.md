---
title: "Форматировать метки оси как значения даты или валюты (построитель отчетов и службы SSRS) | Документы Microsoft"
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
ms.assetid: e9a01a74-2f51-4b35-be3a-a6138568f6cf
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7b8f82c7824a44d46a282eca8d617fb12ac9ade5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs"></a>Форматирование меток оси в виде значений даты или валюты (построитель отчетов и службы SSRS)
Если на оси в отчете [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с разбиением на страницы отображаются правильно отформатированные значения типа DateTime, диаграмма автоматически отобразит эти значения как дни. Чтобы указать интервал даты-времени для оси X, такой как интервал в месяцах или интервал в часах, необходимо отформатировать метки оси и задать в качестве типа интервала оси допустимый интервал значений даты или времени.  
  
> [!NOTE]  
>  В гистограммах и точечных диаграммах осью категорий является горизонтальная ось (или ось X). Однако для линейчатых диаграмм осью категорий является вертикальная (ось Y).  
  
 Чтобы правильно отформатировать интервалы времени, необходимо обеспечить приведение значений, отображаемых на оси X, к типу данных <xref:System.DateTime> . Если поле содержит данные типа <xref:System.String>, то на диаграмме не вычисляются интервалы как значения даты или времени. Дополнительные сведения см. в разделе [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md).  
  
 Если к оси Y добавляется числовое значение, то, по умолчанию, на диаграмме это число не форматируется перед его отображением. Если числовое поле содержит данные о продаже, можно отформатировать эти числа как значения валюты, чтобы повысить удобство чтения диаграммы.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-format-x-axis-labels-as-monthly-intervals"></a>Форматирование меток оси X как месячных интервалов  
  
1.  Щелкните правой кнопкой мыши горизонтальную ось (ось X) диаграммы и выберите **Свойства горизонтальной оси**.  
  
2.  В диалоговом окне **Свойства горизонтальной оси** выберите **Число**.  
  
3.  В списке **Категория** выберите **Дата**. В списке **Тип** выберите формат даты, применяемый к меткам оси X.  
  
4.  Выберите **Параметры оси**.  
  
5.  В поле **Интервал**введите **1**. Для свойства **Тип интервала** выберите значение **Месяцы**.  
  
    > [!NOTE]  
    >  Если тип интервала не указан, диаграмма вычисляет интервалы в днях.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="to-format-y-axis-labels-using-a-currency-format"></a>Форматирование меток оси Y с помощью формата валюты  
  
1.  Щелкните правой кнопкой мыши вертикальную ось (ось Y) диаграммы и выберите **Свойства вертикальной оси**.  
  
2.  В диалоговом окне **Свойства вертикальной оси** выберите **Число**.  
  
3.  В списке **Категория** выберите **Валюта**. В списке **Символ** выберите формат валюты, применяемый к меткам оси Y.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Форматирование меток оси на диаграмме &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Форматирование диаграммы &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Задать логарифмическую шкалу &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/specify-a-logarithmic-scale-report-builder-and-ssrs.md)   
 [Укажите интервал оси &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
