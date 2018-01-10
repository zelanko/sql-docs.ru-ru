---
title: "Реализация интерфейса ISubscriptionBaseUIUserControl | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- user controls [Reporting Services]
- ISubscriptionBaseUIUserControl interface
- delivery extensions [Reporting Services], user controls
ms.assetid: a1e9122c-aa0b-45de-b536-4f1202875ab1
caps.latest.revision: "35"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: de645a67fc9997fdc4d527035ec83108798d8941
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="implementing-the-isubscriptionbaseuiusercontrol-interface"></a>Реализация интерфейса ISubscriptionBaseUIUserControl
  Модули доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] могут содержать реализацию пользовательского интерфейса подписки для сбора сведений, относящихся к модулю, в диспетчере отчетов. Пользовательский интерфейс вызывается, когда пользователь создает новую подписку или изменяет существующую подписку. Когда создается новая подписка, в пользовательском интерфейсе выводятся походящие значения по умолчанию, а пользователи получают возможность взаимодействовать с поставщиком доставки. Когда подписка изменяется, пользовательский интерфейс заранее заполняется сведениями, содержащимися в текущей подписке.  
  
 Модули доставки предоставляют пользовательский интерфейс подписки в виде пользовательского элемента управления ASP.NET. Сервер отчетов содержит пользовательский элемент управления, определенный модулем доставки, когда отображается пользовательский интерфейс подписки. Интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> является базовым и содержит абстрактные методы, выполняющие эти функции. Этот интерфейс обеспечивает правильное выполнение общих операций, таких как проверка входных значений. Кроме того, базовый пользовательский элемент управления передает набор свойств по умолчанию, которые используются сервером отчетов для обеспечения согласованности между подписками. Эти свойства необходимы для модулей доставки, которые интегрированы с диспетчером отчетов.  
  
 Можно реализовать интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> в поставщике доставки, чтобы построить пользовательский интерфейс подписки для диспетчера отчетов. Интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> образует инфраструктуру, которая позволяет пользователям вводить значения для параметров подписки, обрабатывает параметры, необходимые для модуля доставки, а также проверяет параметры.  
  
> [!NOTE]  
>  Интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> необязательно должен быть реализован в составе модуля доставки. Вместо этого подписки, использующие модуль доставки, всегда можно создать с помощью методов <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> и <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A> из API-интерфейса SOAP. Дополнительные сведения о функциях API-интерфейса SOAP для управления подпиской и доставкой см. в разделе [Методы подписки и доставки](../../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md).  
  
 Интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> служит расширением интерфейса <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Пользовательский элемент управления, реализующий интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl>, также должен наследовать от класса **System.Web.UI.WebControls.WebControl**. Дополнительные сведения о классе **WebControl** см. в руководстве разработчика [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Пример использования интерфейса <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> см. на странице [Образцы продуктов служб SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
