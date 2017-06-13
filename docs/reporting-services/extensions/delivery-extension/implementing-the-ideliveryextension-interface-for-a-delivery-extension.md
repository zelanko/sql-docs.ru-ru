---
title: "Реализация интерфейса IDeliveryExtension для модуля доставки | Документы Microsoft"
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
- delivery extensions [Reporting Services], attributes
- delivery extensions [Reporting Services], class creation
- IDeliveryExtension interface
ms.assetid: ab0344db-510b-403f-8dbf-b9831553765d
caps.latest.revision: 37
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 82bf0172d2ad744d5a34945596814cd584888d95
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="implementing-the-ideliveryextension-interface-for-a-delivery-extension"></a>Реализация интерфейса IDeliveryExtension для модуля доставки
  Класс модуля доставки используется для доставки пользователям уведомлений об отчетах на основании содержимого уведомлений. Класс модуля доставки также образует инфраструктуру для проверки пользовательских параметров, передаваемых в модуль доставки. Кроме того, класс модуля доставки должен содержать специальные свойства, с помощью которых клиенты могут получать сведения об имени модуля, параметрах, поддерживаемых модулем и форматах подготовки к просмотру, доступных для модуля доставки.  
  
 ![Процесс интерфейса IDeliveryExtension](../../../reporting-services/extensions/delivery-extension/media/bk-ext-02.gif "IDeliveryExtension interface process")  
Интерфейс IDeliveryExtension позволяет проверять пользовательские данные, а также сообщать клиентам о необходимых параметрах доставки.  
  
 Чтобы создать класс модуля доставки, реализуйте интерфейсы <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> и <xref:Microsoft.ReportingServices.Interfaces.IExtension>. **IDeliveryExtension** интерфейс позволяет модулю доставки для доставки уведомлений об отчетах с помощью <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> метод и проверять входящие параметры модуля с помощью <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> метод. **IExtension** интерфейс позволяет модулю доставки для реализации локализованное имя модуля и обрабатывать сведения конфигурации для модуля, хранящиеся в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] файла конфигурации. Путем реализации **IExtension**, содержащий модуль доставки <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> свойство. Настоятельно рекомендуется, [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] поддержки модули доставки **LocalizedName** свойства, чтобы пользователи работали с привычным именем модуля в пользовательском интерфейсе, таком как диспетчер отчетов.  
  
 Модуль доставки, также должен реализовывать **ExtensionSettings** свойство **IDeliveryExtension** интерфейса. Сервер отчетов использует значение, возвращаемое свойством <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A>, для определения параметров, необходимых модулю доставки. Клиенты, взаимодействующие с модулями доставки, используют метод <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> веб-службы сервера отчетов, чтобы вернуть список параметров для модуля доставки.  
  
 Также можно использовать класс модуля доставки для получения пользовательских данных, хранящихся в файле RSReportServer.config, и обработки этих данных. Дополнительные сведения об обработке данных пользовательской конфигурации см. в описании метода <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A>.  
  
 Образец **IDeliveryExtension** реализации класса см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
