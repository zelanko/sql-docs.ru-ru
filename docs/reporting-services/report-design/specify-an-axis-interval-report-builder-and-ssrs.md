---
title: Задание интервала оси (построитель отчетов) | Документация Майкрософт
ms.date: 09/02/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: ae46712d-a5bf-44c0-9929-e30ccc1e7e33
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fecaea37ca01f7d005934c8b371d228bc0bb6b93
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "77080941"
---
# <a name="specify-an-axis-interval-report-builder-and-ssrs"></a>Задание интервала оси (построитель отчетов и службы SSRS)
Узнайте, как изменить количество меток и делений на оси категорий (X) диаграммы, задав интервал оси в отчете с разбиением на страницы [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] .
 
Интервалы на оси значений (обычно это ось Y) обеспечивают согласованное измерение точек данных на диаграмме. 

Однако автоматический интервал на оси категорий (обычно это ось X) иногда приводит к отображению категорий без меток на оси. Можно указать необходимое количество интервалов в свойстве оси Interval. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] вычисляют количество интервалов во время выполнения в зависимости от данных результирующего набора. Дополнительные сведения в вычислениях интервалов оси см. в разделе [Форматирование меток оси на диаграмме](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).  

Чтобы попробовать установить интервал оси с помощью образца данных, см. раздел [Учебник. Добавление гистограммы к отчету](Tutorial:%20Add%20a%20Column%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md).
  
> [!NOTE]  
>  Ось категорий обычно является горизонтальной осью (осью X). Однако для линейчатых диаграмм ось категорий является вертикальной (осью Y).  
>
> Данный раздел не применяется к следующим элементам.
>-   Значения даты или времени на оси категорий. Значения **DateTime** по умолчанию отображаются как дни. Вы можете определить другой интервал данных или времени, например интервал месяца или времени. Дополнительные сведения см. в разделе [Форматирование меток оси в виде значений даты или валюты](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md).  
>-  Круговые, кольцевые, воронкообразные или пирамидальные диаграммы, которые не имеют осей. 
  
## <a name="to-show-all-the-category-labels-on-the-x-axis"></a>Отображение всех меток категории на оси X  

На этой гистограмме для горизонтального интервала меток задано значение "Автоматически".

![report-builder-column-chart-preview-x-axis-interval-auto](../../reporting-services/report-design/media/report-builder-column-chart-preview-x-axis-interval-auto.png)
  
1.  Щелкните правой кнопкой мыши ось категорий и выберите пункт **Свойства горизонтальной оси**.   

    ![report-builder-column-chart-x-axis-labels](../../reporting-services/report-design/media/report-builder-column-chart-x-axis-labels.png)
  
2.  В диалоговом окне **Свойства горизонтальной оси** откройте вкладку **Параметры оси** и задайте для параметра **Интервал** значение **1**, чтобы отобразить каждую метку группы категорий. Чтобы отобразить каждую метку группы другой категории на оси X, введите значение **2**. 

     ![report-builder-column-chart-x-axis-interval-one](../../reporting-services/report-design/media/report-builder-column-chart-x-axis-interval-one.png)
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

    Теперь на гистограмме отображаются все метки горизонтальной оси.

    ![report-builder-column-chart-preview-x-axis-interval-one](../../reporting-services/report-design/media/report-builder-column-chart-preview-x-axis-interval-one.png)
  
    > [!NOTE]  
    >  После установки интервала оси автоматическое присваивание меток отключается. При указании значения для интервала оси может возникнуть непредсказуемое поведение при присваивании меток в зависимости от количества категорий на оси категорий.  

## <a name="change-the-label-interval-in-properties-pane"></a>Изменение интервала меток на панели "Свойства"

Вы можете изменить интервал меток на панели "Свойства".

1.  В конструкторе отчетов щелкните диаграмму, а затем выберите метки на горизонтальной оси.

3. На панели "Свойства" назначьте свойству LabelInterval значение **1**.

    ![report-builder-column-chart-set-label-interval](../../reporting-services/media/report-builder-column-chart-set-label-interval.png)

    В режиме конструктора диаграмма выглядит так же. 
    
5.  Нажмите кнопку **Выполнить** для предварительного просмотра отчета.

    ![report-builder-column-chart-label-interval-one-preview](../../reporting-services/media/report-builder-column-chart-label-interval-one-preview.png)
    
    Теперь на диаграмме отображаются все метки.
  
## <a name="to-enable-a-variable-interval-calculation-on-an-axis"></a>Включение вычисления переменного интервала на оси  

По умолчанию [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] задает для интервала оси значение "Автоматически". Эта процедура объясняет, как можно снова присвоить значение по умолчанию. 
  
1.  Щелкните правой кнопкой мыши по оси диаграммы, которую необходимо изменить, и выберите пункт **Свойства оси**. 
  
2.  В диалоговом окне **Свойства горизонтальной оси** откройте вкладку **Параметры оси** и задайте для параметра **Интервал** значение **Авто**. В диаграмме отобразится оптимальное количество меток категории, умещающееся на оси.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Форматирование диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Форматирование точек данных на диаграмме (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Сортировка данных в области данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/sort-data-in-a-data-region-report-builder-and-ssrs.md)   
 [Диалоговое окно "Свойства оси" — "Параметры оси" (построитель отчетов и службы SSRS)](https://msdn.microsoft.com/library/b276e210-7a12-48ae-971b-7dabae51df11)   
 [Задание логарифмической шкалы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specify-a-logarithmic-scale-report-builder-and-ssrs.md)   
 [Построение данных на вспомогательной оси (построитель отчетов и службы SSRS)](../../reporting-services/report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)  
  
  
