---
title: Реализация интерфейса IDeliveryExtension для модуля доставки | Документы Майкрософт
description: Узнайте, как реализовать интерфейс IDeliveryExtension в модуле доставки, чтобы клиенты могли проверять данные пользователей и получать параметры доставки.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], attributes
- delivery extensions [Reporting Services], class creation
- IDeliveryExtension interface
ms.assetid: ab0344db-510b-403f-8dbf-b9831553765d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ba66d4f375e30edf37594230ddb44c1bd18d99b8
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529556"
---
# <a name="implementing-the-ideliveryextension-interface-for-a-delivery-extension"></a>Реализация интерфейса IDeliveryExtension для модуля доставки
  Класс модуля доставки используется для доставки пользователям уведомлений об отчетах на основании содержимого уведомлений. Класс модуля доставки также образует инфраструктуру для проверки пользовательских параметров, передаваемых в модуль доставки. Кроме того, класс модуля доставки должен содержать специальные свойства, с помощью которых клиенты могут получать сведения об имени модуля, параметрах, поддерживаемых модулем и форматах подготовки к просмотру, доступных для модуля доставки.  
  
 ![Процесс интерфейса IDeliveryExtension](../../../reporting-services/extensions/delivery-extension/media/bk-ext-02.gif "Процесс интерфейса IDeliveryExtension")  
Интерфейс IDeliveryExtension позволяет проверять пользовательские данные, а также сообщать клиентам о необходимых параметрах доставки.  
  
 Чтобы создать класс модуля доставки, реализуйте интерфейсы <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> и <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Интерфейс **IDeliveryExtension** позволяет модулю доставки доставлять уведомления об отчетах с помощью метода <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> и проверять входящие параметры модуля с помощью метода <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A>. Интерфейс **IExtension** дает возможность реализовать в модуле доставки локализованное имя модуля и обрабатывать сведения конфигурации для модуля, хранящиеся в файле конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. В результате реализации интерфейса **IExtension** в модуль доставки включается свойство <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A>. В модулях доставки служб [!INCLUDE[ssRS](../../../includes/ssrs.md)] настоятельно рекомендуется реализовать поддержку свойства **LocalizedName**, чтобы пользователи работали с привычным именем модуля в пользовательском интерфейсе, например в диспетчере отчетов.  
  
 В модуле доставки также необходимо реализовать свойство **ExtensionSettings** интерфейса **IDeliveryExtension**. Сервер отчетов использует значение, возвращаемое свойством <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A>, для определения параметров, необходимых модулю доставки. Клиенты, взаимодействующие с модулями доставки, используют метод <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> веб-службы сервера отчетов, чтобы вернуть список параметров для модуля доставки.  
  
 Также можно использовать класс модуля доставки для получения пользовательских данных, хранящихся в файле RSReportServer.config, и обработки этих данных. Дополнительные сведения об обработке данных пользовательской конфигурации см. в описании метода <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A>.  
  
 Образец реализации класса **IDeliveryExtension** отчета см. на странице [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
