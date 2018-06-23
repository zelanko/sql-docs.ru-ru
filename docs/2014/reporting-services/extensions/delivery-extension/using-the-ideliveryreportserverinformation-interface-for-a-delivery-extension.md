---
title: Использование интерфейса IDeliveryReportServerInformation для модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
caps.latest.revision: 34
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ccffffd38ed25bea72bfcafdfaf2161e7b88c666
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102352"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>Использование интерфейса IDeliveryReportServerInformation в модуле доставки
  В интерфейсе <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> доступно несколько свойств, с помощью которых можно получить сведения о сервере отчетов. Эти сведения моно использовать для доставки уведомлений и отчетов. Во время реализации класса модуля доставки реализуется свойство <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A>, требуемое интерфейсом <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. Свойство <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> возвращает объект, который реализует интерфейс <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>. Из этого объекта можно получить список модулей подготовки отчетов, которые в данный момент поддерживаются сервером отчетов.  
  
 Следующие `for` цикла может использоваться для хранения списка доступных модулей подготовки отчетов на сервере отчетов в **ArrayList** объекта.  
  
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
  
  