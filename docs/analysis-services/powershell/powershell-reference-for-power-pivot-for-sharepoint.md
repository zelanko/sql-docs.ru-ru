---
title: "Справочник по PowerShell для Power Pivot для SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 11/16/2015
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c01735a8-f919-48ad-8d74-35d75a18f821
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 538992c846ed5dd7bfe9fdd8ab0aaf0ec47009ee
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="powershell-reference-for-power-pivot-for-sharepoint"></a>Справочник по PowerShell для Power Pivot для SharePoint

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  В этом разделе перечисляются командлеты PowerShell, которые используются для настройки и администрирования установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Дополнительные сведения о разрешении командлетов и просмотре встроенной справки см. в разделе [Настройка PowerPivot с помощью Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md).  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
## <a name="cmdlet-list"></a>Список командлетов  
 Чтобы просмотреть список командлетов из командной строки PowerShell:  
  
1.  Откройте консоль управления SharePoint с параметром **Запуск от имени администратора** .  
  
2.  Введите следующую команду: `Get-help *powerpivot*`  
  
|Командлет|Поддерживаемые версии|  
|------------|------------------------|  
|[Командлет «Get-PowerPivotServiceApplication»](../../analysis-services/powershell/get-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Get-PowerPivotSystemService»](../../analysis-services/powershell/get-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Get-PowerPivotSystemServiceInstance»](../../analysis-services/powershell/get-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «New-PowerPivotServiceApplication»](../../analysis-services/powershell/new-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «New-PowerPivotSystemServiceInstance»](../../analysis-services/powershell/new-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Remove-PowerPivotServiceApplication»](../../analysis-services/powershell/remove-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Remove-PowerPivotSystemServiceInstance»](../../analysis-services/powershell/remove-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Set-PowerPivotServiceApplication»](../../analysis-services/powershell/set-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Set-PowerPivotSystemService»](../../analysis-services/powershell/set-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Update-PowerPivotSystemService»](../../analysis-services/powershell/update-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
  
 Примечание. Указанные далее командлеты работали только в SharePoint 2010, не поддерживаемом [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] .  
  
-   Get-PowerPivotEngineService  
  
-   Get-PowerPivotEngineServiceInstance  
  
-   New-PowerPivotEngineServiceInstance  
  
-   Remove-PowerPivotEngineServiceInstance  
  
-   Set-PowerPivotEngineService  
  
-   Set-PowerPivotEngineServiceInstance  
  
-   Update-PowerPivotEngineService  
  
  
