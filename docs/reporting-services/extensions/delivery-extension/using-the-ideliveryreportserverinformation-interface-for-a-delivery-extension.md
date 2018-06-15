---
title: Использование интерфейса IDeliveryReportServerInformation для модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 01ae302af52fbf6e0b72124dba64830623f47cba
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33014631"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>Использование интерфейса IDeliveryReportServerInformation в модуле доставки
  В интерфейсе <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> доступно несколько свойств, с помощью которых можно получить сведения о сервере отчетов. Эти сведения моно использовать для доставки уведомлений и отчетов. Во время реализации класса модуля доставки реализуется свойство <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A>, требуемое интерфейсом <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. Свойство <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> возвращает объект, который реализует интерфейс <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>. Из этого объекта можно получить список модулей подготовки отчетов, которые в данный момент поддерживаются сервером отчетов.  
  
 В следующем цикле **for** можно сохранить список модулей подготовки отчетов, доступных в данный момент на сервере отчетов, в объекте **ArrayList**.  
  
```vb  
Dim renderFormats As New ArrayList()  
Dim e As Microsoft.ReportingServices.Interfaces.Extension  
For Each e In  ReportServerInformation.RenderingExtension  
   If e.Visible Then  
      renderFormats.Add(e.Name)  
   End If  
Next e  
```  
  
```csharp  
ArrayList renderFormats = new ArrayList();  
foreach (Microsoft.ReportingServices.Interfaces.Extension e in ReportServerInformation.RenderingExtension)  
{   
   if (e.Visible)  
   {  
      renderFormats.Add(e.Name);  
   }  
}  
```  
  
 Дополнительные сведения об использовании интерфейса <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> см. в разделе [Использование интерфейса IDeliveryReportServerInformation для модуля доставки](../../../reporting-services/extensions/delivery-extension/using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
