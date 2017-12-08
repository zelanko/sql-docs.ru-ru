---
title: "Power Pivot обновления данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: power-pivot-sharepoint
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
caps.latest.revision: "24"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4c5bc570e1f4f72fe932a8e5b2d0fa08c32f7949
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="power-pivot-data-refresh"></a>Обновление данных Power Pivot
  После создания книги, содержащей данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , их придется периодически обновлять путем повторного выполнения запроса или команды, чтобы получать новые данные из источников, которые использовались при создании книги. Этот процесс называется **обновлением данных**. Обновление данных может производиться по запросу [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]или как запланированная операция путем запуска процесса служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на сервере приложений фермы SharePoint. Дополнительные сведения см. в разделе:  
  
-   [Обновление данных Power Pivot в SharePoint 2010](http://msdn.microsoft.com/en-us/01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [Настройка учетной записи автоматического обновления данных Power Pivot (Power Pivot для SharePoint)](http://msdn.microsoft.com/en-us/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [Настройка сохраненных учетных данных для обновления данных Power Pivot (Power Pivot для SharePoint)](http://msdn.microsoft.com/en-us/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [Планирование обновления данных (Power Pivot для SharePoint)](http://msdn.microsoft.com/en-us/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [Просмотр журнала обновления данных (Power Pivot для SharePoint)](../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]и SharePoint Server 2013 Excel Services используется другая архитектура для обновления данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] моделей данных. Архитектура SharePoint 2013 в качестве основного компонента для загрузки моделей данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] использует службы Excel. В прежней архитектуре обновления данных для загрузки моделей данных использовался сервер с [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System Service и [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме SharePoint. Дополнительные сведения см. в следующих разделах:  
>   
>  -   [Обновление данных PowerPivot в SharePoint 2013](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Обновление книг и запланированное обновление данных (SharePoint 2013 )](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
