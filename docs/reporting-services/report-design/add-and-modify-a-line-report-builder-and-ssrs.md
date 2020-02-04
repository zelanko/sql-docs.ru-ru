---
title: Добавление и изменение линии (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 8dc4998b-a214-49b6-96e7-fbc179015209
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b58cb9cd7b4fcb13454b1a8d7cebcf380987fcbd
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65582096"
---
# <a name="add-and-modify-a-line-report-builder-and-ssrs"></a>Добавление и изменение линии (построитель отчетов и службы SSRS)
  Если нужно отделить разделы отчета [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы каким-либо графическим элементом, можно добавить в отчет линию. Настроить внешний вид линии можно, изменяя ее свойства, такие как цвет или стиль. Например, можно встроить в отчет корпоративные цвета компании.    
    
> [!NOTE]    
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]    
    
## <a name="to-add-a-line"></a>Добавление линии    
    
1.  На вкладке **Вставка** щелкните **Линия**.    
    
2.  В области конструктора щелкните место, где должен находиться один конец линии, затем щелкните место, где должен находиться другой ее конец.    
    
     Обратите внимание, что при перемещении конца линии появляются «линии привязки», если ее конец выравнивается с другим объектом в области конструктора. Это облегчает выравнивание объектов.    
    
3.  Для изменения свойств линии выберите ее в области конструктора и измените свойства в разделе **Граница** вкладки **Корневая папка** .    
    
    > [!NOTE]    
    >  Если установить для линии стиль **Двойная** , а толщина линии не будет превышать 1,5 пт, то при выполнении отчета в построителе отчетов, в конструкторе отчетов или на веб-портале [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] эта линия может не отображаться двойной. После экспорта отчета в другие форматы, такие как Microsoft Word и Acrobat PDF, линия будет отображаться двойной.    
    
## <a name="see-also"></a>См. также:    
 [Прямоугольники и линии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/rectangles-and-lines-report-builder-and-ssrs.md)    
    
  
