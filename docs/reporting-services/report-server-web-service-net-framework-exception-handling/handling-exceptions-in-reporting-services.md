---
title: Обработка исключений в службах Reporting Services | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7fbf4c9d89d35f4fbb437a41c691f7f8c6578b9b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63028571"
---
# <a name="handling-exceptions-in-reporting-services"></a>Обработка исключений в службах Reporting Services
  Если клиентский запрос API-интерфейса протокола SOAP не может быть выполнен, сервер отчетов возвращает ошибку вместо ожидаемых результатов вызова. Если вызов не может быть выполнен, возвращается ошибка для веб-службы сервера отчетов как XML-элемент **Fault** протокола SOAP. Ключевым описательным элементом ошибки является элемент **detail**, который включает в себя все данные ошибки, предоставляемые сервером отчетов, а также дополнительные данные ошибки из веб-службы. Основными данными в элементе **detail** является код ошибки сервера отчетов. На основании сообщения и кода ошибки можно определить, какое следующее правильное действие следует предпринять в приложении. Дополнительные сведения об ошибках SOAP см. на веб-сайте консорциума W3C: http://www.w3.org/TR/SOAP.  
  
## <a name="soap-faults-and-the-net-framework"></a>Ошибки протокола SOAP и платформы .NET Framework  
 На платформе [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], если происходит ошибка в клиентском запросе к веб-службе, сервер отчетов передает ошибку в код клиента, который вызывает веб-службу с помощью объекта **SoapException**. Объект **SoapException** упаковывает данные, содержащиеся в ошибке протокола SOAP. Свойство **Detail** объекта **SoapException** сопоставляется с элементом **detail** в ошибке SOAP. Приложения должны перехватывать объект **SoapException** с помощью блока TRY–CATCH и использовать свойство **Detail** объекта **SoapException** для выполнения соответствующих действий. Дополнительные сведения о классе **SoapException** и свойстве **Detail** в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] см. в разделе [Класс SoapException в службах Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md). Дополнительные сведения о классе **SoapException** см. в документации по пакету SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Свойство Detail](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Введение в обработку исключений в службах Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException в службах Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
