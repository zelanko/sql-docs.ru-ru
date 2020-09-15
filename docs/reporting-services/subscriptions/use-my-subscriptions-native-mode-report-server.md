---
title: Использование страницы "Мои подписки" (сервер отчетов в собственном режиме) | Документы Майкрософт
description: Сведения о том, как использовать страницу "Мои подписки" на веб-портале Reporting Services для просмотра, изменения, включения, отключения или удаления существующих подписок.
ms.date: 07/01/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 964e6752dc44477215180e6e61f6440feb8972af
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87939441"
---
# <a name="use-my-subscriptions-native-mode-report-server"></a>Использование страницы "Мои подписки" (сервер отчетов в основном режиме)
На веб-портале [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] есть страница **Мои подписки** , которая представляет собой единое место для организации подписок. Страницу *Мои подписки* можно использовать для просмотра, изменения, включения, отключения и удаления существующих подписок. Однако ее нельзя использовать для создания подписок.  Страница «Мои подписки» показывает лишь созданные вами подписки. На ней не отображаются ни подписки, принадлежащие другим пользователям (даже если вы на них подписаны), ни управляемые данными подписки.
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (собственный режим)|  
  
При вводе запроса поле поиска динамически фильтрует список подписок. Выполнить поиск подписок по имени, по сведениям о триггерах, состоянию и т. д. нельзя. Дополнительные сведения см. в разделе [Создание подписок для работающих в основном режиме серверов отчетов и управление этими подписками](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md).
  
## <a name="to-open-the-my-subscriptions-page"></a>Открытие страницы «Мои подписки»  
1. Откройте веб-портал [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] .
2. Щелкните параметр ![ssrs_portal_settings_gear](../../reporting-services/subscriptions/media/ssrs-portal-settings-gear.png) на панели инструментов.
3. Нажмите кнопку **Мои подписки**.

Дополнительные сведения см. в статье [Web portal (SSRS Native Mode)](../../reporting-services/web-portal-ssrs-native-mode.md).

## <a name="use-windows-powershell-to-list-mysubscriptions"></a>Использование Windows PowerShell для перечисления MySubscriptions  
 ![Содержимое, связанное с PowerShell](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")  
  
 Следующий скрипт PowerShell возвращает список подписок и свойств подписок для текущего пользователя. Дополнительные сведения см. в разделе [Метод ReportingService2010.ListMySubscriptions](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).  
  
```  
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "https://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions

```  
  
## <a name="see-also"></a>См. также:  
 [Data-Driven Subscriptions](../../reporting-services/subscriptions/data-driven-subscriptions.md)   
 [Подписки и доставка (службы Reporting Services)](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [old_Создание подписок для работающих в собственном режиме серверов отчетов и управление этими подписками](https://docs.microsoft.com/sql/reporting-services/subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers)  
  
  
