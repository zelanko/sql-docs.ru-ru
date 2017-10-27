---
title: "Добавление и изменение линии (построитель отчетов и службы SSRS) | Документы Microsoft"
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
ms.assetid: 8dc4998b-a214-49b6-96e7-fbc179015209
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ca5f80521b142435210737f2e6c971c8d6853510
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

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
    
## <a name="see-also"></a>См. также    
 [Прямоугольники и линии (построитель отчетов и службы SSRS)](../../reporting-services/report-design/rectangles-and-lines-report-builder-and-ssrs.md)    
    
  

