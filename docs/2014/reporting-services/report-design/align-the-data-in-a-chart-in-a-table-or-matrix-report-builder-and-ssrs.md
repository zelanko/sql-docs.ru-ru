---
title: Выравнивание данных в диаграмме в таблице или матрице (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 7277e8a0b50fb8e67a6601218190241c11efbd74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102414"
---
# <a name="align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs"></a>Выравнивание данных в диаграмме в таблице или матрице (построитель отчетов и службы SSRS)
  Sparkline-графики и гистограммы — это маленькие, простые диаграммы, которые передают большой объем данных без ненужных подробностей. Если выбрать этот параметр, то значения в sparkline-графиках и гистограммах будут выравниваться по различным ячейкам в таблице или матрице даже в случае, если в базовых данных отсутствуют некоторые значения.  
  
 ![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")  
  
 На этом изображении на гистограмме отображаются значения продаж за день для всех сотрудников. Обратите внимание, что для дней, когда у сотрудников нет продаж, на гистограмме остается пустая область и последующие дни выравниваются по горизонтали. Диаграммы выравниваются также по вертикали путем изменения размеров других диаграмм по отношению друг к другу. Дополнительные сведения см. в разделе [спарклайны и гистограммы &#40;построитель отчетов и службы SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="align-the-data-in-a-sparkline-or-data-bar"></a>Выравнивание данных в спарклайн-графиках и гистограммах  
  
1.  Щелкните спарклайн-график или гистограмму и выберите **Свойства горизонтальных осей** или **Свойства вертикальных осей**.  
  
2.  На вкладке **Параметры осей** установите флажок **Выровнять оси в** , затем в раскрывающемся списке выберите группу, для которой необходимо выровнять оси.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Диаграммы (построитель отчетов и службы SSRS)](charts-report-builder-and-ssrs.md)   
 [Добавление спарклайнов и гистограмм &#40;построитель отчетов и службы SSRS&#41;](add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
