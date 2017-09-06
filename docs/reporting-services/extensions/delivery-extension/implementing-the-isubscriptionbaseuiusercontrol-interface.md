---
title: "Реализация интерфейса ISubscriptionBaseUIUserControl | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- user controls [Reporting Services]
- ISubscriptionBaseUIUserControl interface
- delivery extensions [Reporting Services], user controls
ms.assetid: a1e9122c-aa0b-45de-b536-4f1202875ab1
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 4e76edaa727df1694a5903e1cc9870c20581c9a0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-the-isubscriptionbaseuiusercontrol-interface"></a>Реализация интерфейса ISubscriptionBaseUIUserControl
  Модули доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] могут содержать реализацию пользовательского интерфейса подписки для сбора сведений, относящихся к модулю, в диспетчере отчетов. Пользовательский интерфейс вызывается, когда пользователь создает новую подписку или изменяет существующую подписку. Когда создается новая подписка, в пользовательском интерфейсе выводятся походящие значения по умолчанию, а пользователи получают возможность взаимодействовать с поставщиком доставки. Когда подписка изменяется, пользовательский интерфейс заранее заполняется сведениями, содержащимися в текущей подписке.  
  
 Модули доставки предоставляют пользовательский интерфейс подписки в виде пользовательского элемента управления ASP.NET. Сервер отчетов содержит пользовательский элемент управления, определенный модулем доставки, когда отображается пользовательский интерфейс подписки. Интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> является базовым и содержит абстрактные методы, выполняющие эти функции. Этот интерфейс обеспечивает правильное выполнение общих операций, таких как проверка входных значений. Кроме того, базовый пользовательский элемент управления передает набор свойств по умолчанию, которые используются сервером отчетов для обеспечения согласованности между подписками. Эти свойства необходимы для модулей доставки, которые интегрированы с диспетчером отчетов.  
  
 Можно реализовать интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> в поставщике доставки, чтобы построить пользовательский интерфейс подписки для диспетчера отчетов. Интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> образует инфраструктуру, которая позволяет пользователям вводить значения для параметров подписки, обрабатывает параметры, необходимые для модуля доставки, а также проверяет параметры.  
  
> [!NOTE]  
>  Интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> необязательно должен быть реализован в составе модуля доставки. Вместо этого подписки, использующие модуль доставки, всегда можно создать с помощью методов <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> и <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A> из API-интерфейса SOAP. Дополнительные сведения о функциях API-Интерфейс SOAP для управления подпиской и доставкой см. в разделе [методы подписки и доставки](../../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md).  
  
 Интерфейс <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> служит расширением интерфейса <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Пользовательский элемент управления, реализующий <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> также должен наследоваться от **System.Web.UI.WebControls.WebControl**. Дополнительные сведения о **WebControl** см. в описании вашей [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] в руководстве разработчика.  
  
 Пример использования <xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> интерфейса см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
