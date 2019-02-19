---
title: Выравнивание данных в диаграмме в таблице или матрице (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 763091e27701524a40c686fc773a6e4e845992fb
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56290423"
---
# <a name="align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs"></a>Выравнивание данных в диаграмме в таблице или матрице (построитель отчетов и службы SSRS)
  Sparkline-графики и гистограммы — это маленькие, простые диаграммы, которые передают большой объем данных без ненужных подробностей. Если выбрать этот параметр в отчете [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы, то значения в спарклайнах и гистограммах будут выравниваться по различным ячейкам в таблице или матрице даже в случае, если в базовых данных отсутствуют некоторые значения.  
  
 ![rs_SparklineAlignData](../../reporting-services/report-design/media/rs-sparklinealigndata.gif "rs_SparklineAlignData")  
  
 На этом изображении на гистограмме отображаются значения продаж за день для всех сотрудников. Обратите внимание, что для дней, когда у сотрудников нет продаж, на гистограмме остается пустая область и последующие дни выравниваются по горизонтали. Диаграммы выравниваются также по вертикали путем изменения размеров других диаграмм по отношению друг к другу. Дополнительные сведения см. в разделе [Спарклайны и гистограммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
## <a name="align-the-data-in-a-sparkline-or-data-bar"></a>Выравнивание данных в спарклайн-графиках и гистограммах  
  
1.  [Добавьте спарклайн или гистограмму](../../reporting-services/report-design/add-sparklines-and-data-bars-report-builder-and-ssrs.md) к таблице или матрице.  
  
2. Щелкните спарклайн-график или гистограмму и выберите **Свойства горизонтальных осей** или **Свойства вертикальных осей**.  
  
2.  На вкладке **Параметры осей** установите флажок **Выровнять оси в** , затем в раскрывающемся списке выберите группу, для которой необходимо выровнять оси.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Добавление спарклайнов и гистограмм (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
