---
title: Обновление данных PowerPivot | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4ab42604fabaa188a74858038e35a8b90a105df8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66071221"
---
# <a name="powerpivot-data-refresh"></a>Обновление данных PowerPivot
  После создания книги, содержащей данные PowerPivot, их придется периодически обновлять путем повторного выполнения запроса или команды, чтобы получать новые данные из источников, которые использовались при создании книги. Этот процесс называется `data refresh`. Обновление данных может производиться по запросу [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] или как запланированная операция путем запуска процесса служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на сервере приложений фермы SharePoint. Дополнительные сведения см. в разделе:  
  
-   [Обновление данных PowerPivot с SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)  
  
-   [Настройка PowerPivot учетной записи автоматического обновления &#40;PowerPivot для SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
-   [Настройка сохраненных учетных данных для обновления данных PowerPivot &#40;PowerPivot для SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
-   [Планирование обновления данных &#40;PowerPivot для SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
-   [Просмотр журнала обновления данных &#40;PowerPivot для SharePoint&#41;](view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и SharePoint Server 2013 Excel Services используется другая архитектура для обновления данных в моделях данных PowerPivot. Архитектура SharePoint 2013 в качестве основного компонента для загрузки моделей данных PowerPivot использует службы Excel. В прежней архитектуре обновления данных для загрузки моделей данных использовался сервер с PowerPivot System Service и [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме SharePoint. Дополнительные сведения см. в следующих разделах:  
> 
>  -   [Обновление данных PowerPivot с SharePoint 2013](power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Обновление книг и запланированное обновление данных (SharePoint 2013 )](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
