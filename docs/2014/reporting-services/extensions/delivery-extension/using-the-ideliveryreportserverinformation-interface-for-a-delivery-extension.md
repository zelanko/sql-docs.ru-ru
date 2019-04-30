---
title: Использование интерфейса IDeliveryReportServerInformation для модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a94b6da8536ee0269a448b8a446fc0da3f3f576
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63164042"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>Использование интерфейса IDeliveryReportServerInformation в модуле доставки
  В интерфейсе <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> доступно несколько свойств, с помощью которых можно получить сведения о сервере отчетов. Эти сведения моно использовать для доставки уведомлений и отчетов. Во время реализации класса модуля доставки реализуется свойство <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A>, требуемое интерфейсом <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. Свойство <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> возвращает объект, который реализует интерфейс <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>. Из этого объекта можно получить список модулей подготовки отчетов, которые в данный момент поддерживаются сервером отчетов.  
  
 Следующие `for` цикл может использоваться для хранения списка доступных модулей подготовки отчетов на сервере отчетов в **ArrayList** объекта.  
  
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
  
 Дополнительные сведения об использовании интерфейса <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> см. в разделе [Использование интерфейса IDeliveryReportServerInformation для модуля доставки](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Реализация модуля доставки](implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
