---
title: "Добавление на карту пользовательских местоположений (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MICROSOFT.REPORTDESIGNER.MAPPOINT.POINTTEMPLATE
ms.assetid: 7d36faae-5bcc-446a-9eba-f42349cafacb
caps.latest.revision: "10"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 0f874233485441f7f3ac2575b022c69cd298c056
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="add-custom-locations-to-a-map-report-builder-and-ssrs"></a>Добавление на карту пользовательских местоположений (построитель отчетов и службы SSRS)
  После добавления карты в отчет [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы в нее можно добавлять собственные точечные местоположения.  
  
 Параметры отображения всех точек слоя управляются путем задания свойств точек слоя. Для выбранной внедренной точки можно переопределить свойства отображения.  
  
> [!NOTE]  
>  При переопределении свойств отображения слоя для внедренной точки произведенные изменения необратимы.  
  
 Дополнительные сведения см. в разделе [Изменение параметров отображения многоугольников, линий и точек с помощью правил и аналитических данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-point-layer"></a>Добавление слоя точек  
  
1.  Чтобы выбрать карту и отобразить панель «Карта», щелкните карту в области конструктора отчетов.  
  
2.  На панели инструментов нажмите кнопку **Добавить слой**.  
  
3.  Из раскрывающегося списка выберите **Добавить слой точек**. На карту добавляется слой точек без точек. По умолчанию слой точек готов к добавлению внедренных точек.  
  
## <a name="to-add-a-custom-point"></a>Добавление пользовательской точки  
  
1.  Чтобы выбрать карту и отобразить панель «Карта», щелкните карту в области конструктора отчетов.  
  
2.  На панели "Карта" щелкните правой кнопкой мыши слой точек типа **Внедренный**, а затем выберите пункт **Добавить точку**. Курсор превращается в перекрестье.  
  
3.  Чтобы добавить точку, щелкните определенное положение на карте. Внедренная точка добавляется в выбранный слой в местоположении щелчка.  
  
## <a name="to-customize-the-display-for-an-embedded-point"></a>Настройка отображения внедренной точки  
  
1.  Щелкните правой кнопкой мыши точку и выберите пункт **Свойства точки**. Открывается диалоговое окно **Свойства внедренных точек карты** .  
  
2.  Установите флажок **Переопределить параметры точек для данного слоя**. На левой панели появится несколько страниц свойств.  
  
3.  Переходите по страницам и задавайте свойства отображения, которые необходимо применить к данной точке.  
  
## <a name="see-also"></a>См. также  
 [Карты (построитель отчетов и службы SSRS)](../../reporting-services/report-design/maps-report-builder-and-ssrs.md)   
 [Изменение параметров отображения многоугольников, линий и точек с помощью правил и аналитических данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
