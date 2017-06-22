---
title: "Использование класса Notification для модуля доставки | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- delivery extensions [Reporting Services], notifications
- notifications [Reporting Services]
- retry queues
- Nofication class
ms.assetid: 549c40c4-d33d-46c2-9d6a-7bbb671ac67a
caps.latest.revision: 33
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 708144d726d97380f32d39ac88901e0f6d57ba0b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="using-a-notification-class-for-a-delivery-extension"></a>Использование класса Notification для модуля доставки
  Класс <xref:Microsoft.ReportingServices.Interfaces.Notification> находится в пространстве имен <xref:Microsoft.ReportingServices.Interfaces> и представляет сведения о подписках, используемые модулями доставки при доставке отчетов. Класс <xref:Microsoft.ReportingServices.Interfaces.Notification> предоставляет ряд свойств, которые могут быть использованы при подготовке отчетов для доставки, при определении состояния уведомления и при указании пользовательских данных.  
  
 ![Процесс уведомления об отчетах](../../../reporting-services/extensions/delivery-extension/media/bk-ext-03.gif "Report notification process")  
Уведомление является центральным объектом любой доставки  
  
 При возникновении события, связанного с подпиской, в которой применяется пользовательский модуль доставки, создается уведомление, содержащее объект <xref:Microsoft.ReportingServices.Interfaces.Report>. Объект <xref:Microsoft.ReportingServices.Interfaces.Report> инкапсулирует функции, необходимые для подготовки данного отчета к отображению в поддерживаемом формате, и содержит такие конкретные свойства отчета, как URL-адрес отчета на сервере, а также имя отчета. Дополнительные сведения о <xref:Microsoft.ReportingServices.Interfaces.Report> см. в описании [использование класса Report в модуле доставки](../../../reporting-services/extensions/delivery-extension/using-the-report-class-for-a-delivery-extension.md).  
  
 Объект <xref:Microsoft.ReportingServices.Interfaces.Notification> передается методу <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> модуля доставки. Метод <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> должен содержать конкретный код, обеспечивающий обработку уведомления и доставку отчета.  
  
 Пример использования <xref:Microsoft.ReportingServices.Interfaces.Notification> см. в описании [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="retry-functionality"></a>Функция повторной передачи  
 Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] предоставляют возможность создавать очереди повтора для уведомлений, которые не могут быть переданы немедленно. После вызова сервером отчетов метода <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> модуля доставки этот модуль доставки может обратиться к серверу отчетов с запросом о повторной доставке в более поздний момент времени. В таком случае сервер отчетов помещает уведомление во внутреннюю очередь и по истечении определенного периода времени предпринимает новую попытку доставки. Администраторы могут настраивать максимальное число повторных попыток, выполняемых на сервере отчетов и за период между повторными попытками, в разделе модуля доставки файла RSReportServer.config с помощью **MaxNumberOfRetries** XML-элемент и **PeriodBetweenRetries** XML-элемента. Уведомления удаляются из очереди повтора, если в дальнейшем доставка завершится успешно или будет достигнуто максимальное число попыток повторной передачи. Если после достижения максимального числа попыток повторной передачи доставка оканчивается неудачей, уведомление отменяется.  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
