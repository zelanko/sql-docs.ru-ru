---
title: Справочник по PowerShell для Power Pivot для SharePoint | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8a133d55644545e9af6331653a8ec153b53abea9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="powershell-reference-for-power-pivot-for-sharepoint"></a>Справочник по PowerShell для Power Pivot для SharePoint
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В этом разделе перечисляются командлеты PowerShell, которые используются для настройки и администрирования установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] . Дополнительные сведения о разрешении командлетов и просмотре встроенной справки см. в разделе [Настройка PowerPivot с помощью Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md).  

>[!NOTE] 
>В этой статье может содержать устаревшие сведения и примеры. С помощью командлета Get-Help для последней версии.
  
## <a name="cmdlet-list"></a>Список командлетов  
 Чтобы просмотреть список командлетов из командной строки PowerShell:  
  
1.  Откройте консоль управления SharePoint с параметром **Запуск от имени администратора** .  
  
2.  Введите следующую команду: `Get-help *powerpivot*`  
  
|Командлет|Поддерживаемые версии|  
|------------|------------------------|  
|[Командлет Get-PowerPivotServiceApplication](../../analysis-services/powershell/get-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Get-PowerPivotSystemService»](../../analysis-services/powershell/get-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Get-PowerPivotSystemServiceInstance»](../../analysis-services/powershell/get-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «New-PowerPivotServiceApplication»](../../analysis-services/powershell/new-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет New-PowerPivotSystemServiceInstance](../../analysis-services/powershell/new-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Remove-PowerPivotServiceApplication»](../../analysis-services/powershell/remove-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Remove-PowerPivotSystemServiceInstance»](../../analysis-services/powershell/remove-powerpivotsystemserviceinstance-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет Set-PowerPivotServiceApplication](../../analysis-services/powershell/set-powerpivotserviceapplication-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет Set-PowerPivotSystemService](../../analysis-services/powershell/set-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
|[Командлет «Update-PowerPivotSystemService»](../../analysis-services/powershell/update-powerpivotsystemservice-cmdlet.md)|SharePoint 2013 | SharePoint 2016|  
  
 Примечание. Указанные далее командлеты работали только в SharePoint 2010, не поддерживаемом [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] .  
  
-   Get-PowerPivotEngineService  
  
-   Get-PowerPivotEngineServiceInstance  
  
-   New-PowerPivotEngineServiceInstance  
  
-   Remove-PowerPivotEngineServiceInstance  
  
-   Set-PowerPivotEngineService  
  
-   Set-PowerPivotEngineServiceInstance  
  
-   Update-PowerPivotEngineService  
  
  
