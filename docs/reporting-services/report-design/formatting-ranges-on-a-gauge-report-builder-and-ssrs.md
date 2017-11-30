---
title: "Форматирование диапазонов на датчике (построитель отчетов и службы SSRS) | Документы Майкрософт"
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
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
caps.latest.revision: "7"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 851b829cf66a2d89ba2753381dc1598e5bc439b6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a>Форматирование диапазонов на датчике (построитель отчетов и службы SSRS)
 В отчете [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы диапазон датчика — это зона или область на шкале датчика, которая указывает важный подраздел значений в датчике. Используя диапазон датчика, можно визуально отобразить момент, когда значение указателя датчика перемещается в определенную область значений. Диапазоны определяются начальным значением и конечным значением.  
  
 Диапазоны также используются для определения различных разделов датчика. Например, в датчике со значениями от 0 до 10 можно определить красный диапазон со значениями от 0 до 3, желтый диапазон со значениями от 4 до 7 и зеленый диапазон со значениями от 8 до 10. Если заданное начальное значение больше конечного, эти значения меняются местами, и начальное значение становится конечным, а конечное — начальным.  
  
 Диапазон можно размещать точно так же, как размещается указатель на шкале. Свойства **Положение** и **Расстояние от шкалы** определяют положение диапазона. Дополнительные сведения см. в разделе [Датчики (построитель отчетов и службы SSRS)](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Форматирование шкал на датчике (построитель отчетов и службы SSRS)](../../reporting-services/report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Форматирование указателей на датчике &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Установка минимума и максимума на датчике (построитель отчетов и службы SSRS)](../../reporting-services/report-design/set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)   
 [Учебник. Добавление в отчет ключевого показателя эффективности (построитель отчетов)](../../reporting-services/tutorial-adding-a-kpi-to-your-report-report-builder.md)   
 [Датчики (построитель отчетов и службы SSRS)](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)  
  
  
