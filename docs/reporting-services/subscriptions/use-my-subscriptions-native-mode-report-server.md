---
title: Использование страницы "Мои подписки" (сервер отчетов в собственном режиме) | Документы Майкрософт
ms.date: 07/01/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 83451b167534f1a94b4cd5324a54b5a8f08cb596
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828964"
---
# <a name="use-my-subscriptions-native-mode-report-server"></a>Использование страницы "Мои подписки" (сервер отчетов в основном режиме)
На веб-портале [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] есть страница **Мои подписки** , которая представляет собой единое место для организации подписок. Страницу *Мои подписки* можно использовать для просмотра, изменения, включения, отключения и удаления существующих подписок. Однако ее нельзя использовать для создания подписок.  Страница «Мои подписки» показывает лишь созданные вами подписки. На ней не отображаются ни подписки, принадлежащие другим пользователям (даже если вы на них подписаны), ни управляемые данными подписки.
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме|  
  
При вводе запроса поле поиска динамически фильтрует список подписок. Выполнить поиск подписок по имени, по сведениям о триггерах, состоянию и т. д. нельзя. Дополнительные сведения см. в разделе [Создание подписок для работающих в основном режиме серверов отчетов и управление этими подписками](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md).
  
## <a name="to-open-the-my-subscriptions-page"></a>Открытие страницы «Мои подписки»  
1. Откройте веб-портал [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] .
2. Щелкните параметр ![ssrs_portal_settings_gear](../../reporting-services/subscriptions/media/ssrs-portal-settings-gear.png) на панели инструментов.
3. Нажмите кнопку **Мои подписки**.

Дополнительные сведения см. в статье [Web portal (SSRS Native Mode)](../../reporting-services/web-portal-ssrs-native-mode.md).

## <a name="use-windows-powershell-to-list-mysubscriptions"></a>Использование Windows PowerShell для перечисления MySubscriptions  
 ![Содержимое, связанное с PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")  
  
 Следующий скрипт PowerShell возвращает список подписок и свойств подписок для текущего пользователя. Дополнительные сведения см. в разделе [Метод ReportingService2010.ListMySubscriptions](http://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).  
  
```  
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions

```  
  
## <a name="see-also"></a>См. также:  
 [Подписки, управляемые данными](../../reporting-services/subscriptions/data-driven-subscriptions.md)   
 [Подписки и доставка (службы Reporting Services)](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [old_Создание подписок для работающих в собственном режиме серверов отчетов и управление этими подписками](http://msdn.microsoft.com/en-us/7f46cbdb-5102-4941-bca2-5e0ff9012c6b)  
  
  
