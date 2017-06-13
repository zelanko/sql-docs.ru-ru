---
title: "Добавление стилей рельефа, приподнятости и текстуры в диаграмму (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2081d22c9e0aefd82cda5dff97b8ece503fdd9b0
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="chart-effects---add-bevel-emboss-or-texture-report-builder"></a>Эффекты для диаграммы - добавить Рельеф, рельефный, или текстуры (построитель отчетов)
  При использовании диаграмм определенных типов можно ввести в действие эффекты рисования для повышения внешней привлекательности диаграммы. Эти эффекты рисования применяются только к ряду, представленному на диаграмме. Они не оказывают никакого влияния на другие элементы диаграммы.  
  
 Если используется какой-либо вариант круговой или кольцевой диаграммы, можно определить стиль рисования с применением размытых краев или вогнутых участков, аналогичный стилю с эффектами скоса или выпуклости, которые могут быть применены к изображению.  
  
 Если используется какой-либо вариант линейчатой диаграммы или гистограммы, то можно применить стили текстуры, такие как оформление в виде цилиндра, клина и переход от светлого к темному, к отдельным линейкам или столбцам.  
  
 Кроме этих стилей рисования можно добавлять границы и тени ко многим элементам диаграммы для создания иллюзии глубины. Дополнительные сведения о других способах форматирования диаграммы см. в разделе [Форматирование диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-bevel-or-emboss-styles-to-a-pie-or-doughnut-chart"></a>Добавление стилей скоса или выпуклости к круговой или кольцевой диаграмме  
  
1.  На вкладке **Представление** выберите **Свойства** , чтобы открыть панель «Свойства».  
  
2.  Выберите круговую или кольцевую диаграмму, которую необходимо сделать более привлекательной. Выберите поле данных на диаграмме, а не всю диаграмму.  
  
3.  На панели «Свойства» разверните узел **CustomAttributes** .  
  
4.  Для PieDrawingStyle выберите стиль из раскрывающегося списка.  
  
> [!NOTE]  
>  На одной диаграмме не могут применяться объемный и рельефный или приподнятый стили. Если для диаграммы включен объемный стиль, свойство PieDrawingStyle не будет выводиться.  
  
 ![Круговая диаграмма с вогнутым стилем](../../reporting-services/report-design/media/rs-piedrawingeffects-concave.gif "круговая диаграмма с вогнутым стилем")  
  
### <a name="to-add-texture-styles-to-a-bar-or-column-chart"></a>Чтобы добавить стили текстуры к линейчатой диаграмме или гистограмме  
  
1.  Выберите линейчатую диаграмму или гистограмму, которую необходимо сделать более привлекательной. Выберите поле данных на диаграмме, а не всю диаграмму.  
  
2.  Откройте панель «Свойства».  
  
3.  Разверните узел **CustomAttributes** .  
  
4.  Для DrawingStyle выберите стиль из раскрывающегося списка.  
  
> [!NOTE]  
>  На одной диаграмме не могут применяться объемный и рельефный или приподнятый стили. Если для диаграммы включен объемный стиль, свойство PieDrawingStyle не будет выводиться.  
  
 ![Линейчатая диаграмма с эффектом рисования LightToDark](../../reporting-services/report-design/media/rs-bardrawingeffects-lighttodark.gif "линейчатая диаграмма с эффектом рисования LightToDark")  
  
## <a name="see-also"></a>См. также:  
 [Линейчатые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [Гистограммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md)   
 [Круговые диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [Форматирование диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)  
  
  
