---
title: Изменение порядка параметров отчета (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 08/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 77eee65231026bd77aec5086e13b3f56782d23da
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43266772"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Изменение порядка параметров отчета (построитель отчетов и службы SSRS)
  Изменять порядок параметров отчета необходимо в случае, если зависимый параметр расположен перед параметром, от которого он зависит. Порядок параметров имеет значение при наличии каскадных параметров или в случае, если необходимо показать пользователям значение по умолчанию одного параметра перед тем, как они выберут значения для других параметров. Зависимый параметр отчета ссылается (в своем запросе значений по умолчанию или в запросе допустимых значений) на параметр запроса, указывающий на параметр отчета, расположенный после него в списке параметров в области **Данные отчета** .  
  
 Порядок, в котором параметры отображаются на панели инструментов средства просмотра отчетов при запуске отчета, определяется порядком параметров в области **Данные отчета** и расположением параметров на панели пользовательских параметров. Дополнительные сведения см. в разделах [Настройка области параметров в отчете (построитель отчетов)](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-the-order-of-report-parameters"></a>Изменение порядка параметров отчета  
  
Изменить порядок параметров отчета можно одним из следующих способов:  
  
-   Щелкните параметр в области **Данные отчета** и переместите его выше или ниже в списке, используя кнопки со стрелками вниз и вверх, как показано на изображении ниже.  При изменении порядка параметров в области **Данные отчета** также меняется расположение параметра на панели.  
  
     ![Изменение порядка параметров в области данных отчета](../../reporting-services/report-design/media/ssrs-changeorderofparameters-reportdata.png "Изменение порядка параметров в области данных отчета")  
  
-   На панели параметров перетащите параметр в новый столбец или строку. При изменении расположения параметра на панели также изменяется порядок параметров в области **Данные отчета** . Дополнительные сведения о перемещении параметров в области см. в разделе [Настройка области параметров в отчете (построитель отчетов)](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
## <a name="see-also"></a>См. также:  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Добавление каскадных параметров в отчет (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Учебник. Добавление параметра к отчету (построитель отчетов)](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Добавление фильтров набора данных, фильтров области данных и групповых фильтров (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Ссылки на коллекцию параметров (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  
