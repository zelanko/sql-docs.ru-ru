---
title: Использовать «Мои подписки» | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddd8eba477d0426fc0bf8eaeac9dcd2c1ec60b78
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66100619"
---
# <a name="use-my-subscriptions"></a>Использовать «Мои подписки»
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Диспетчер отчетов предлагает **Мои подписки** страницу, которая организует всех подписок в одном месте. Можно использовать страницу «Мои подписки» для просмотра, изменения и удаления существующих подписок. Однако ее нельзя использовать для создания подписок.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в собственном режиме|  
  
 На странице «Мои подписки» можно сортировать подписки по папкам, отчетам, описаниям, триггерам, дате последнего запуска и состоянию. Все значения сортируются по алфавиту, за исключением даты последнего запуска; по ней выполняется сортировка в хронологическом порядке.  
  
 Страница «Мои подписки» показывает лишь созданные вами подписки. На ней не отображаются ни подписки, принадлежащие другим пользователям (даже если вы на них подписаны), ни управляемые данными подписки.  
  
 В ней нельзя выполнить поиск подписки по имени, по сведениям о триггерах, состоянию и др. Дополнительные сведения см. в разделе [создание, изменение и удаление стандартных подписок &#40;служб Reporting Services в собственном режиме&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).  
  
## <a name="how-to-use-my-subscriptions"></a>Как использовать страницу «Мои подписки»  
 Страница «Мои подписки» доступна в диспетчере отчетов. Чтобы получить доступ к странице «Мои подписки», нажмите кнопку **Мои подписки** на общей панели инструментов диспетчера отчетов.  
  
## <a name="use-windows-powershell-to-list-mysubscriptions"></a>Использование Windows PowerShell для перечисления MySubscriptions  
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")  
  
 Следующий скрипт PowerShell возвращает список подписок и свойств подписок для текущего пользователя. Дополнительные сведения см. в разделе [Метод ReportingService2010.ListMySubscriptions](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).  
  
```  
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions  
  
```  
  
## <a name="see-also"></a>См. также  
 [Подписки, управляемые данными](data-driven-subscriptions.md)   
 [Подписки и доставка (службы Reporting Services)](subscriptions-and-delivery-reporting-services.md)   
 [Создание и администрирование подписок для серверов отчетов в собственном режиме](../create-manage-subscriptions-native-mode-report-servers.md)  
  
  
