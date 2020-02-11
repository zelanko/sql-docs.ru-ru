---
title: Настройка PowerPivot с помощью Windows PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4d83e53e-04f1-417d-9039-d9e81ae0483d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9282fce8e0004495ae8c10b0b3f75fec205d6b34
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "72782808"
---
# <a name="powerpivot-configuration-using-windows-powershell"></a>Настройка PowerPivot с помощью Windows PowerShell
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]включает командлеты Windows PowerShell, которые можно использовать для настройки установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Для полной настройки установки требуются командлеты и SharePoint, и PowerPivot для SharePoint. Большую часть настройки можно выполнить с помощью одного из средств [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Дополнительные сведения об этих средствах см. в разделе [PowerPivot Configuration Tools](power-pivot-configuration-tools.md).  
  
> [!IMPORTANT]  
>  При работе с фермой SharePoint 2010 необходимо установить SharePoint 2010 с пакетом обновления 1 (SP1), чтобы иметь возможность настроить PowerPivot для SharePoint или ферму SharePoint 2010, в которой используется сервер базы данных [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] . Если пакет обновления еще не установлен, установите его, прежде чем начать настройку сервера.  
  
## <a name="benefits-of-configuring-powerpivot-for-sharepoint-using-powershell"></a>Преимущества настройки PowerPivot для SharePoint с помощью PowerShell  
 Для автоматизации задач настройки можно построить файлы скриптов Windows PowerShell (PS1). Этот подход рекомендуется, если необходимо обеспечить установку и настройку с помощью скриптов, которые можно выполнить на любом сервере. В случае отказа аппаратной части подобный скрипт может потребоваться как часть плана аварийного восстановления сервера.  
  
## <a name="view-a-list-of-the-powerpivot-cmdlets-on-a-server"></a>Просмотр списка командлетов PowerPivot на сервере  
 Чтобы просмотреть содержимое и примеры [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] командлетов, см. [Справочник по PowerShell для PowerPivot для SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).  
  
 Использование PowerShell для просмотра списка командлетов PowerPivot  
  
1.  Откройте консоль управления SharePoint с параметром **Запуск от имени администратора** .  
  
2.  Введите следующую команду:  
  
    ```powershell
    Get-Help *powerpivot*  
    ```  
  
     Появится список командлетов, содержащих в имени «PowerPivot». Пример: `Get-PowerPivotServiceApplication`. Число доступных командлетов зависит от используемой версии служб Analysis Services.  
  
    -   10 командлетов на сервере служб SQL Server 2012 Analysis Services с пакетом обновления 1 (SP1), работающим в режиме интеграции с SharePoint и SharePoint 2013. Версия 2012 с пакетом обновления 1 (SP1) использует новую архитектуру, которая позволяет серверу анализа данных работать за пределами фермы SharePoint и требует меньше командлетов управления Windows PowerShell.  
  
    -   17 командлетов на сервере служб Analysis Services SQL Server 2012, работающем в режиме интеграции с SharePoint и SharePoint 2010.  
  
     Если в списке не возвращено ни одной команды или появляется сообщение об ошибке, похожее на "`get-help could not find *powerpivot* in a help file in this session.`", см. сведения о том, как включить командлеты PowerPivot на сервере в следующем разделе этого раздела.  
  
     Для всех командлетов имеется справка в Интернете. В следующем примере показано, как посмотреть справку в Интернете для командлета `New-PowerPivotServiceApplication`.  
  
    ```powershell
    Get-Help new-powerpivotserviceapplication -Full  
    ```  
  
     Кроме того, чтобы просмотреть только примеры, используйте следующий синтаксис.  
  
    ```powershell
    Get-Help new-powerpivotserviceapplication -Example  
    ```  
  
## <a name="enable-powerpivot-cmdlets-on-a-server"></a>Включение командлетов PowerPivot на сервере  
 Командлеты PowerPivot доступны после установки PowerPivot для SharePoint и развертывания решения фермы. Решения развертываются при запуске средства настройки PowerPivot. Выполните следующие действия, чтобы включить использование командлетов.  
  
1.  Откройте консоль управления SharePoint с параметром **Запуск от имени администратора** .  
  
2.  Запустите первый командлет.  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     Командлет возвратит имя решения, его идентификатор, а также атрибут Deployed=False. На следующем шаге будет выполнено развертывание решения.  
  
3.  Выполните второй командлет, чтобы развернуть решение.  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
4.  Закройте окно. Откройте его снова с помощью варианта **Запуск от имени администратора** .  
  
## <a name="related-content"></a>См. также  
 [Настройка и администрирование сервера PowerPivot в центре администрирования](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [PowerPivot Configuration Tools](power-pivot-configuration-tools.md)  
  
 [Справочник по PowerShell для PowerPivot для SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
