---
title: "Добавление прямоугольника или контейнера (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
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
f1_keywords:
- "10061"
- sql13.rtp.rptdesigner.rectangleproperties.general.f1
ms.assetid: f905c35f-754d-4d02-80f3-85e29ddda826
caps.latest.revision: "9"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 706d719a813508541f3eda5df4045937a3af4643
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="add-a-rectangle-or-container-report-builder-and-ssrs"></a>Добавление прямоугольника или контейнера (построитель отчетов и службы SSRS)
  Прямоугольник добавляется к отчету [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы, если нужно разделить различные области отчета с помощью графического элемента, выделить области отчета или установить фон для одного или нескольких элементов отчета. Прямоугольники используются также в качестве контейнеров, помогающих управлять подготовкой к просмотру областей данных в отчете. Внешний вид прямоугольника можно настроить, изменяя его свойства, например цвета фона и границ. Дополнительные сведения об использовании прямоугольника как контейнера см. в разделах [Прямоугольники и линии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/rectangles-and-lines-report-builder-and-ssrs.md) и [Отображение одних и тех же данных в матрице и на диаграмме (построитель отчетов)](../../reporting-services/report-design/display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).    
   
## <a name="to-add-a-rectangle"></a>Добавление прямоугольника    
    
1.  На вкладке **Вставка** в группе **Элементы отчета** щелкните **Прямоугольник**.    
    
2.  В области конструктора щелкните место расположения верхнего левого угла прямоугольника и перетащите указатель мыши в место расположения нижнего правого угла.    
    
     Обратите внимание при движении курсора: в момент, когда курсор располагается на одной линии с другими объектами в области конструктора, появляются линии привязки. Это облегчает выравнивание объектов.    
    
## <a name="to-create-a-container"></a>Создание контейнера    
    
1.  Добавьте прямоугольный элемент отчета в отчет.    
    
2.  Перетащите в прямоугольник другие элементы отчета.    
    
    > [!NOTE]    
    >  Прямоугольник является всего лишь контейнером для элементов, которые создаются в прямоугольнике или перетаскиваются в него. Если нарисовать прямоугольник вокруг элемента, уже существующего в области конструктора, прямоугольник не будет функционировать как его контейнер.    
    
## <a name="to-change-rectangle-properties-such-as-color-style-or-weight"></a>Изменение свойств прямоугольника, таких как цвет, стиль или вес    
    
1.  Выберите прямоугольник, а затем выберите параметры цвета, стиля или веса в разделе **Граница** вкладки «Корневая папка».    
    
2.  Для задания того, какие стороны прямоугольника изменять, нажмите стрелку рядом с кнопкой **Граница** .    
    
    > [!NOTE]    
    >  Если установить для линии стиль **Двойная** , а толщина линии не будет превышать 1,5 пт, то при выполнении отчета в построителе отчетов, в конструкторе отчетов или на веб-портале [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] эта линия может не отображаться двойной. После экспорта отчета в другие форматы, такие как Microsoft Word и Acrobat PDF, линия будет отображаться двойной.    
    
## <a name="see-also"></a>См. также    
 [Прямоугольники и линии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/rectangles-and-lines-report-builder-and-ssrs.md)     
 [Поведение при подготовке к просмотру (построитель отчетов и службы SSRS)](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)    
    
  
