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
ms.openlocfilehash: 6f7d5ed5c2f8882cbc0c47a1c711748d26e0193c
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84535076"
---
# <a name="powerpivot-data-refresh"></a>Обновление данных PowerPivot
  После создания книги, содержащей данные PowerPivot, их придется периодически обновлять путем повторного выполнения запроса или команды, чтобы получать новые данные из источников, которые использовались при создании книги. Этот процесс называется `data refresh`. Обновление данных может производиться по запросу [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] или как запланированная операция путем запуска процесса служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на сервере приложений фермы SharePoint. Дополнительные сведения можно найти в разделе  
  
-   [Обновление данных PowerPivot с SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)  
  
-   [Настройте учетную запись автоматического обновления данных PowerPivot &#40;PowerPivot для SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)  
  
-   [Настройка сохраненных учетных данных для &#40;обновления данных PowerPivot PowerPivot для SharePoint&#41;](../configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
-   [Планирование &#40;обновления данных PowerPivot для SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
-   [Просмотр журнала обновления данных &#40;PowerPivot для SharePoint&#41;](view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и SharePoint Server 2013 Excel Services используется другая архитектура для обновления данных в моделях данных PowerPivot. Архитектура SharePoint 2013 в качестве основного компонента для загрузки моделей данных PowerPivot использует службы Excel. В прежней архитектуре обновления данных для загрузки моделей данных использовался сервер с PowerPivot System Service и [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме SharePoint. Дополнительные сведения см. в следующих разделах:  
> 
>  -   [Обновление данных PowerPivot с SharePoint 2013](power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Обновление книг и обновление данных по расписанию &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
