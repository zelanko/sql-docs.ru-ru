---
title: Использование класса Notification для модуля доставки | Документы Майкрософт
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], notifications
- notifications [Reporting Services]
- retry queues
- Nofication class
ms.assetid: 549c40c4-d33d-46c2-9d6a-7bbb671ac67a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1ac8e57ab8248a06a10488e6b8ca1743ed57f5eb
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50028209"
---
# <a name="using-a-notification-class-for-a-delivery-extension"></a>Использование класса Notification для модуля доставки
  Класс <xref:Microsoft.ReportingServices.Interfaces.Notification> находится в пространстве имен <xref:Microsoft.ReportingServices.Interfaces> и представляет сведения о подписках, используемые модулями доставки при доставке отчетов. Класс <xref:Microsoft.ReportingServices.Interfaces.Notification> предоставляет ряд свойств, которые могут быть использованы при подготовке отчетов для доставки, при определении состояния уведомления и при указании пользовательских данных.  
  
 ![Процесс уведомления об отчетах](../../../reporting-services/extensions/delivery-extension/media/bk-ext-03.gif "Процесс уведомления об отчетах")  
Уведомление является центральным объектом любой доставки  
  
 При возникновении события, связанного с подпиской, в которой применяется пользовательский модуль доставки, создается уведомление, содержащее объект <xref:Microsoft.ReportingServices.Interfaces.Report>. Объект <xref:Microsoft.ReportingServices.Interfaces.Report> инкапсулирует функции, необходимые для подготовки данного отчета к отображению в поддерживаемом формате, и содержит такие конкретные свойства отчета, как URL-адрес отчета на сервере, а также имя отчета. Дополнительные сведения о классе <xref:Microsoft.ReportingServices.Interfaces.Report> см. в разделе [Использование класса Report в модуле доставки](../../../reporting-services/extensions/delivery-extension/using-the-report-class-for-a-delivery-extension.md).  
  
 Объект <xref:Microsoft.ReportingServices.Interfaces.Notification> передается методу <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> модуля доставки. Метод <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> должен содержать конкретный код, обеспечивающий обработку уведомления и доставку отчета.  
  
 Пример использования класса <xref:Microsoft.ReportingServices.Interfaces.Notification> см. в разделе [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="retry-functionality"></a>Функция повторной передачи  
 Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] предоставляют возможность создавать очереди повтора для уведомлений, которые не могут быть переданы немедленно. После вызова сервером отчетов метода <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> модуля доставки этот модуль доставки может обратиться к серверу отчетов с запросом о повторной доставке в более поздний момент времени. В таком случае сервер отчетов помещает уведомление во внутреннюю очередь и по истечении определенного периода времени предпринимает новую попытку доставки. Администраторы могут настраивать максимальное число попыток повторной передачи, предпринимаемых сервером отчетов, а также период времени между повторными попытками, в разделе модуля доставки файла RSReportServer.config с помощью элемента XML **MaxNumberOfRetries** и элемента XML **PeriodBetweenRetries**. Уведомления удаляются из очереди повтора, если в дальнейшем доставка завершится успешно или будет достигнуто максимальное число попыток повторной передачи. Если после достижения максимального числа попыток повторной передачи доставка оканчивается неудачей, уведомление отменяется.  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
