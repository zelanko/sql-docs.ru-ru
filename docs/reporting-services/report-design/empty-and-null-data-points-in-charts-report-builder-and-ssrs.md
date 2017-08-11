---
title: "NULL и пустые точки данных в диаграммах (построитель отчетов и службы SSRS) | Документы Microsoft"
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
ms.assetid: faddd29d-4cc1-4c2c-8e29-d3d9918fe22a
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: cce213fa628dfed0d57304de308377520f60c3d0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---

# <a name="empty-and-null-data-points-in-charts-report-builder-and-ssrs"></a>Точки данных со значением NULL и пустые точки в диаграммах (построитель отчетов и службы SSRS)

  При отображении полей с пустыми значениями или значением NULL на диаграмме в отчете [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с разбиением на страницы диаграмма может выглядеть неправильно. В зависимости от типа диаграммы пустые значения могут обрабатываться по-разному.  
  
-   Если диаграмма имеет линейный тип (линейчатая диаграмма, гистограмма, точечная, линейная, диаграмма с областями, диаграмма диапазонов), то пустые значения изображаются как пустые пространства или пробелы. Чтобы обозначить пустые точки, необходимо добавить заполнители. Дополнительные сведения см. в разделе [Добавление пустых точек на диаграмму &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/add-empty-points-to-a-chart-report-builder-and-ssrs.md).  
  
-   Если диаграмма имеет непрерывный линейный тип (с областями, линейчатая, гистограмма, линия, точечная), то для поддержания непрерывности ряда в диаграмму добавляются пустые точки данных.  
  
-   Если диаграмма имеет нелинейный тип (полярная диаграмма, круговая диаграмма, воронкообразная диаграмма или пирамидальная диаграмма), то пустые значения опускаются из отображения.  
  
-   В фигурных диаграммах значения NULL опускаются.  
  
 Пример диаграммы с пустыми точками данных доступен в виде образца отчета. Дополнительные сведения о скачивании этого и других примеров отчетов см. в статье [Report Builder and Report Designer sample reports](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="removing-empty-or-null-values"></a>Удаление пустых значений и значений NULL  
 Чтобы не скрыть важные данные, подумайте об удалении пустых значений из набора данных. Чтобы отфильтровать значения NULL, используйте в запросе предложение NOT IS NULL. Или же добавьте критерий фильтра, который задает отображение значений, не равных нулю. Дополнительные сведения см. в разделе [Добавление фильтров набора данных, фильтров области данных и групповых фильтров (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md).  
  
## <a name="fields-with-no-values-in-a-chart"></a>Поля без значений в диаграмме  
 Если в возвращаемом наборе данных поле не содержит значений, диаграмма будет пустой, без точек данных, но имя ряда (обычно имя поля) добавляется в качестве условных обозначений.  
  
 Такое поведение отличается от поведения в случае, когда возвращаемый набор данных содержит нулевые строки; такое происходит, если отчет имеет параметры, а выбранное значение возвращает пустой результирующий набор. Если запрос набора данных возвращает нулевые строки данных, то во время выполнения отображается сообщение, оповещающее об отсутствии данных для отображения. Это сообщение можно настроить, изменив заголовок NoDataMessage для отчета на панели **Свойства** . Дополнительные сведения см. в разделе [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  

## <a name="next-steps"></a>Следующие шаги

[Диаграммы](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[Форматирование диаграммы](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
[Добавление диаграммы в отчет](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md)   
[Устранение неполадок с диаграммами](../../reporting-services/report-design/troubleshoot-charts-report-builder-and-ssrs.md)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
