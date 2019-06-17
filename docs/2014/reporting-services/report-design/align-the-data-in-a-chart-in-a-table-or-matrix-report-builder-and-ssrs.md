---
title: Выравнивание данных в диаграмме в таблице или матрице (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 74b6e86e6c9e7fd9d293e4c1bdab952468adb4b6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106511"
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
 [Добавление спарклайнов и гистограмм (построитель отчетов и службы SSRS)](add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
