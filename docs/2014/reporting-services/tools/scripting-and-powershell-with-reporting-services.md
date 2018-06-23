---
title: Работа с отчетами и PowerShell в Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 0d76693f37506cd78a7d198520344cb55f9d142f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101662"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Сценарии и PowerShell со службами Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] поддерживает широкий спектр сценариев разработки и управления посредством скриптов, включая программу командной строки rs.exe, командлеты PowerShell для серверов отчетов в режиме интеграции с SharePoint и использование [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] объектной модели из PowerShell для как в собственном и Режиме интеграции с SharePoint.  
  
-   Администратор может написать на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] скрипт, который позволит автоматизировать развертывание установки сервера отчетов и управление ей. Администраторы также могут создавать и запускать скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] для создания, настройки и обновления базы данных сервера отчетов. Администраторы также могут использовать возможности записи и воспроизведения компонентов скрипта в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , чтобы автоматизировать стандартные задачи обслуживания.  
  
-   Разработчики могут создавать пользовательские приложения, включающие скрипты. Можно запустить скрипт, который выполнит вызовы к веб-службе сервера отчетов. Практически любая операция доступная в управляемом коде, может быть написана и в скрипте.  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] поддерживает [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] сценария .NET как язык скриптов, который может быть обработан программой RS.exe, сервером скриптов, который выполняется на сервере отчетов.  
  
## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>Образцы и командлеты PowerShell в режиме SharePoint для служб Reporting Services  
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Режим SharePoint включает [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] командлеты для администрирования сервера отчетов.  
  
-   [PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) содержит следующие примеры.  
  
    -   Создайте приложение службы и прокси-сервер  
  
    -   Проверьте и обновите модуль доставки  
  
    -   Получение и задание свойств базы данных приложения служб Reporting Services, например времени ожидания базы данных  
  
    -   Расширения данных списка  
  
## <a name="reporting-services-object-model-and-powershell-samples"></a>Объектная модель служб Reporting Services и примеры отчетов Powershell  
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")  
  
 Вызов PowerShell основной объектной модели, в большинстве случаев допустимый для режима SharePoint и собственного режима, например при работе с миграцией и подписками, а также дополнительные сопутствующие примеры по работе с подписками в SQL15.  
  
-   [Использование PowerShell для смены и перечисления владельцев подписок служб Reporting Services и запуска подписки](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
-   [Использование PowerShell для создания виртуальной машины Windows Azure с помощью сервера отчетов, работающего в собственном режиме](http://msdn.microsoft.com/library/azure/dn449661.aspx).  
  
-   См. раздел "Доступ к классам WMI с помощью PowerShell" в статье [Access the Reporting Services WMI Provider](access-the-reporting-services-wmi-provider.md).  
  
-   [Администрирование служб SSRS с помощью PowerShell](http://curah.microsoft.com/13107/how-to-administer-ssrs-using-powershell).scriptin  
  
## <a name="rsexe-scripting-samples"></a>Образцы скриптов RS.exe  
  
-   [Скрипт rs.exe для переноса содержимого между серверами отчетов служб отчетов образца](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
-   Дополнительные примеры скриптов, приложений и расширений см. в разделе [Примеры продуктов SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также  
 [Служебная программа RS.exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md)   
 [Написание скриптов для задач развертывания и администрирования](script-deployment-and-administrative-tasks.md)   
 [Создание скриптов с помощью программы rs.exe и веб-службы](script-with-the-rs-exe-utility-and-the-web-service.md)  
  
  