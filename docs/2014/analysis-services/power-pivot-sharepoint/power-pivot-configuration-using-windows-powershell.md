---
title: Настройка PowerPivot с помощью Windows PowerShell | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d83e53e-04f1-417d-9039-d9e81ae0483d
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4f4feb016768a71ca3f90a8efaf69769cd2ae59c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191308"
---
# <a name="powerpivot-configuration-using-windows-powershell"></a>Настройка PowerPivot с помощью Windows PowerShell
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] включает в себя командлеты Windows PowerShell, которые можно использовать для настройки установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Для полной настройки установки требуются командлеты и SharePoint, и PowerPivot для SharePoint. Большую часть настройки можно выполнить с помощью одного из средств [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Дополнительные сведения об этих средствах см. в разделе [средства настройки PowerPivot](power-pivot-configuration-tools.md).  
  
> [!IMPORTANT]  
>  При работе с фермой SharePoint 2010 необходимо установить SharePoint 2010 с пакетом обновления 1 (SP1), чтобы иметь возможность настроить PowerPivot для SharePoint или ферму SharePoint 2010, в которой используется сервер базы данных [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Если пакет обновления еще не установлен, установите его, прежде чем начать настройку сервера.  
  
## <a name="benefits-of-configuring-powerpivot-for-sharepoint-using-powershell"></a>Преимущества настройки PowerPivot для SharePoint с помощью PowerShell  
 Для автоматизации задач настройки можно построить файлы скриптов Windows PowerShell (PS1). Этот подход рекомендуется, если необходимо обеспечить установку и настройку с помощью скриптов, которые можно выполнить на любом сервере. В случае отказа аппаратной части подобный скрипт может потребоваться как часть плана аварийного восстановления сервера.  
  
## <a name="view-a-list-of-the-powerpivot-cmdlets-on-a-server"></a>Просмотр списка командлетов PowerPivot на сервере  
 Чтобы просмотреть содержимое и примеры [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] командлетов [Справочник по PowerShell для PowerPivot для SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).  
  
 Использование PowerShell для просмотра списка командлетов PowerPivot  
  
1.  Откройте консоль управления SharePoint с параметром **Запуск от имени администратора** .  
  
2.  Введите следующую команду:  
  
    ```  
    Get-help *powerpivot*  
    ```  
  
     Появится список командлетов, содержащих в имени «PowerPivot». Например, `Get-PowerPivotServiceApplication`. Число доступных командлетов зависит от используемой версии служб Analysis Services.  
  
    -   10 командлетов на сервере служб SQL Server 2012 Analysis Services с пакетом обновления 1 (SP1), работающим в режиме интеграции с SharePoint и SharePoint 2013. Версия 2012 с пакетом обновления 1 (SP1) использует новую архитектуру, которая позволяет серверу анализа данных работать за пределами фермы SharePoint и требует меньше командлетов управления Windows PowerShell.  
  
    -   17 командлетов на сервере служб Analysis Services SQL Server 2012, работающем в режиме интеграции с SharePoint и SharePoint 2010.  
  
     Если в списке не показано команд или выдается сообщение об ошибке, например «`get-help could not find *powerpivot* in a help file in this session.`», то см. инструкции по включению командлетов PowerPivot на сервере в следующем подразделе данного раздела.  
  
     Для всех командлетов имеется справка в Интернете. В следующем примере показано, как посмотреть справку в Интернете для командлета `New-PowerPivotServiceApplication`.  
  
    ```  
    Get-help new-powerpivotserviceapplication -full  
    ```  
  
     Кроме того, чтобы просмотреть только примеры, используйте следующий синтаксис.  
  
    ```  
    Get-help new-powerpivotserviceapplication -example  
    ```  
  
## <a name="enable-powerpivot-cmdlets-on-a-server"></a>Включение командлетов PowerPivot на сервере  
 Командлеты PowerPivot доступны после установки PowerPivot для SharePoint и развертывания решения фермы. Решения развертываются при запуске средства настройки PowerPivot. Выполните следующие действия, чтобы включить использование командлетов.  
  
1.  Откройте консоль управления SharePoint с параметром **Запуск от имени администратора** .  
  
2.  Запустите первый командлет.  
  
    ```  
    Add-SPSolution –LiteralPath “C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp”  
    ```  
  
     Командлет возвратит имя решения, его идентификатор, а также атрибут Deployed=False. На следующем шаге будет выполнено развертывание решения.  
  
3.  Выполните второй командлет, чтобы развернуть решение.  
  
    ```  
    Install-SPSolution –Identity PowerPivotFarm.wsp –GACDeployment -Force  
    ```  
  
4.  Закройте окно. Откройте его снова с помощью варианта **Запуск от имени администратора** .  
  
## <a name="related-content"></a>См. также  
 [Настройка и администрирование сервера PowerPivot в центре администрирования](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [Средства настройки PowerPivot](power-pivot-configuration-tools.md)  
  
 [Справочник по PowerShell для PowerPivot для SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
  
