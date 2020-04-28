---
title: Использование класса Notification для модуля доставки | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], notifications
- notifications [Reporting Services]
- retry queues
- Nofication class
ms.assetid: 549c40c4-d33d-46c2-9d6a-7bbb671ac67a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b274eb50405a02f4995b953611e50a234b11eab
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177004"
---
# <a name="using-a-notification-class-for-a-delivery-extension"></a>Использование класса Notification для модуля доставки
  Класс <xref:Microsoft.ReportingServices.Interfaces.Notification> находится в пространстве имен <xref:Microsoft.ReportingServices.Interfaces> и представляет сведения о подписках, используемые модулями доставки при доставке отчетов. Класс <xref:Microsoft.ReportingServices.Interfaces.Notification> предоставляет ряд свойств, которые могут быть использованы при подготовке отчетов для доставки, при определении состояния уведомления и при указании пользовательских данных.

 ![Процесс уведомления об отчетах](../../media/bk-ext-03.gif "Процесс уведомления об отчетах") Уведомление является центральным объектом любой доставки

 При возникновении события, связанного с подпиской, в которой применяется пользовательский модуль доставки, создается уведомление, содержащее объект <xref:Microsoft.ReportingServices.Interfaces.Report>. Объект <xref:Microsoft.ReportingServices.Interfaces.Report> инкапсулирует функции, необходимые для подготовки данного отчета к отображению в поддерживаемом формате, и содержит такие конкретные свойства отчета, как URL-адрес отчета на сервере, а также имя отчета. Дополнительные сведения о классе <xref:Microsoft.ReportingServices.Interfaces.Report> см. в разделе [Использование класса Report в модуле доставки](../delivery-extension/using-the-report-class-for-a-delivery-extension.md).

 Объект <xref:Microsoft.ReportingServices.Interfaces.Notification> передается методу <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> модуля доставки. Метод <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> должен содержать конкретный код, обеспечивающий обработку уведомления и доставку отчета.

 Пример использования класса <xref:Microsoft.ReportingServices.Interfaces.Notification> см. в разделе [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).

## <a name="retry-functionality"></a>Функция повторной передачи
 Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] предоставляют возможность создавать очереди повтора для уведомлений, которые не могут быть переданы немедленно. После вызова сервером отчетов метода <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> модуля доставки этот модуль доставки может обратиться к серверу отчетов с запросом о повторной доставке в более поздний момент времени. В таком случае сервер отчетов помещает уведомление во внутреннюю очередь и по истечении определенного периода времени предпринимает новую попытку доставки. Администраторы могут настраивать максимальное число попыток повторной передачи, предпринимаемых сервером отчетов, а также период времени между повторными попытками, в разделе модуля доставки файла RSReportServer.config с помощью элемента XML **MaxNumberOfRetries** и элемента XML **PeriodBetweenRetries**. Уведомления удаляются из очереди повтора, если в дальнейшем доставка завершится успешно или будет достигнуто максимальное число попыток повторной передачи. Если после достижения максимального числа попыток повторной передачи доставка оканчивается неудачей, уведомление отменяется.

## <a name="see-also"></a>См. также:
 [Реализация модуля доставки](../delivery-extension/implementing-a-delivery-extension.md) [Reporting Services библиотека расширений](../reporting-services-extension-library.md)


