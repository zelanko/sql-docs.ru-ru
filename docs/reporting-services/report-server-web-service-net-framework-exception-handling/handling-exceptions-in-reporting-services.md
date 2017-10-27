---
title: "Обработка исключений в службах Reporting Services | Документы Microsoft"
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
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
caps.latest.revision: 31
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 7e1472c11575ba8bed99992ec9630e408c347291
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="handling-exceptions-in-reporting-services"></a>Обработка исключений в службах Reporting Services
  Если клиентский запрос API-интерфейса протокола SOAP не может быть выполнен, сервер отчетов возвращает ошибку вместо ожидаемых результатов вызова. Когда не удается выполнить вызов, возвращается ошибка для сервера веб-службы отчетов как SOAP **ошибки** XML-элемента. Ключевым описательным элементом ошибки является **сведений** элемент, который включает в себя все сведения об ошибке, предоставляемые сервером отчетов, а также все дополнительные сведения об ошибках службы Web. Сведения о ключе в **сведений** элемент является код ошибки сервера отчетов. На основании сообщения и кода ошибки можно определить, какое следующее правильное действие следует предпринять в приложении. Дополнительные сведения об ошибках SOAP см. на веб-сайте консорциума W3C: http://www.w3.org/TR/SOAP.  
  
## <a name="soap-faults-and-the-net-framework"></a>Ошибки протокола SOAP и платформы .NET Framework  
 В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], при возникновении ошибки в клиентском запросе в веб-службу, сервер отчетов передает ошибку в клиентский код, который вызывает веб-службы путем создания исключения **SoapException** объекта. **SoapException** упаковывает данные, содержащиеся в ошибке SOAP. **Сведений** свойство **SoapException** сопоставляется **сведений** элемент в ошибки SOAP. Приложения должны перехватывать **SoapException** с помощью блока try/catch и используйте **сведений** свойство **SoapException** предпринять соответствующее действие. Дополнительные сведения о **SoapException** класса и **сведений** свойство в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], в разделе [Reporting класс SoapException служб](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md). Дополнительные сведения о **SoapException** см. в описании [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] документации по пакету SDK.  
  
## <a name="see-also"></a>См. также:  
 [Свойство Detail](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Введение в обработку исключений в службах Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException служб Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  

