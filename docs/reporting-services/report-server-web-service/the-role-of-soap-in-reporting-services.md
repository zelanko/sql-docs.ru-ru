---
title: Роль протокола SOAP в службах Reporting Services | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- SOAP [Reporting Services], role in Reporting Services
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: f229c3ef-f2ca-448f-98f1-b8df350b9992
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6ab251afd774e36f35a2c96e7519d3b799b33a9c
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50032073"
---
# <a name="the-role-of-soap-in-reporting-services"></a>The Role of SOAP in Reporting Services
  Веб-служба сервера отчетов использует обмен сообщениями по протоколу SOAP для отправки текстовых команд по сети. Эти команды имеют вид XML-текста, передаваемого через Интернет по протоколу HTTP. Использование протокола связи SOAP в веб-службе сервера отчетов позволяет приложениям и компонентам обмениваться данными с сервером отчетов, используя широко признанную открытую инфраструктуру. Стандарт SOAP определен на веб-сайте www.w3.org/TR/SOAP.  
  
 В качестве клиента SOAP может выступать любое приложение, которое поддерживает протокол SOAP и может отправлять SOAP-запросы. Примером такого клиента SOAP является диспетчер отчетов. Он предоставляет интерфейс к базе данных сервера отчетов, в которой хранятся все отчеты и относящееся к ним содержимое. Пользователи этого приложения могут просматривать папки и отчеты в пространстве имен сервера отчетов и работать с отчетами. Диспетчер отчетов построен на инфраструктуре веб-службы сервера отчетов.  
  
 Сервер отчетов выступает в роли сервера SOAP — службы, которая поддерживает протокол SOAP, может принимать запросы от клиентов SOAP и формировать необходимые ответные сообщения. Сервер обрабатывает запросы и посылает клиенту закодированные ответные сообщения.  
  
 Сообщения SOAP в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] могут принимать множество различных форм в зависимости от типа запроса, выполненного клиентом. В следующем примере показан простой запрос клиента SOAP для удаления элемента из базы данных сервера отчетов.  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItem xmlns="http://www.microsoft.com/sql/ReportingServer">  
            <item>/Samples/Report1</item>  
        </DeleteItem>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 Протокол SOAP требует, чтобы сообщения помещались в элемент **Envelope**, а большая часть сообщения располагалась в элементе **Body**. В этом примере элемент Body содержит вызов метода <xref:ReportService2010.ReportingService2010.DeleteItem%2A>, который принимает строковый параметр, представляющий путь к удаляемому элементу. Можно создать класс-посредник клиента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], в котором все операции SOAP инкапсулируются в методы. Следующий метод [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] представляет пример SOAP-запроса, приведенный ранее.  
  
```  
public void DeleteItem(string item);  
```  
  
 Ответ от сервера имеет приблизительно следующий вид:  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItemResponse xmlns="http://www.microsoft.com/sql/ReportingServer" />  
    </soap:Body>  
</soap:Envelope>  
```  
  
 Метод <xref:ReportService2010.ReportingService2010.DeleteItem%2A> не имеет возвращаемого значения, поэтому возвращается пустой ответ.  
  
## <a name="see-also"></a>См. также:  
 [Доступ к API SOAP](../../reporting-services/report-server-web-service/accessing-the-soap-api.md)   
 [Диспетчер отчетов (службы Reporting Services в основном режиме)](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [Сервер отчетов служб Reporting Services](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)   
 [Веб-службы сервера отчетов](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
