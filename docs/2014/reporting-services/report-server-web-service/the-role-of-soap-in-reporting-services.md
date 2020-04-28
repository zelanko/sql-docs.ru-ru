---
title: Роль протокола SOAP в службах Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- SOAP [Reporting Services], role in Reporting Services
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: f229c3ef-f2ca-448f-98f1-b8df350b9992
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4e0b418e44436912b5ed1368ad7a316951872266
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62519208"
---
# <a name="the-role-of-soap-in-reporting-services"></a>The Role of SOAP in Reporting Services
  Веб-служба сервера отчетов использует обмен сообщениями по протоколу SOAP для отправки текстовых команд по сети. Эти команды имеют вид XML-текста, передаваемого через Интернет по протоколу HTTP. Использование протокола связи SOAP в веб-службе сервера отчетов позволяет приложениям и компонентам обмениваться данными с сервером отчетов, используя широко признанную открытую инфраструктуру. Стандарт SOAP определен на веб-сайте www.w3.org/TR/SOAP.  
  
 В качестве клиента SOAP может выступать любое приложение, которое поддерживает протокол SOAP и может отправлять SOAP-запросы. Примером такого клиента SOAP является диспетчер отчетов. Он предоставляет интерфейс к базе данных сервера отчетов, в которой хранятся все отчеты и относящееся к ним содержимое. Пользователи этого приложения могут просматривать папки и отчеты в пространстве имен сервера отчетов и работать с отчетами. Диспетчер отчетов построен на инфраструктуре веб-службы сервера отчетов.  
  
 Сервер отчетов выступает в роли сервера SOAP — службы, которая поддерживает протокол SOAP, может принимать запросы от клиентов SOAP и формировать необходимые ответные сообщения. Сервер обрабатывает запросы и посылает клиенту закодированные ответные сообщения.  
  
 Сообщения SOAP в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] могут принимать множество различных форм в зависимости от типа запроса, выполненного клиентом. В следующем примере показан простой запрос клиента SOAP для удаления элемента из базы данных сервера отчетов.  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItem xmlns="https://www.microsoft.com/sql/ReportingServer">  
            <item>/Samples/Report1</item>  
        </DeleteItem>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 Протокол SOAP требует, чтобы сообщения помещались в элемент `Envelope`, а большая часть сообщения располагалась в элементе `Body`. В этом примере элемент Body содержит вызов метода <xref:ReportService2010.ReportingService2010.DeleteItem%2A>, который принимает строковый параметр, представляющий путь к удаляемому элементу. Вы можете создать [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] клиентский прокси-класс, который инкапсулирует все операции SOAP в методы. Следующий [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] метод представляет пример SOAP, заданный ранее.  
  
```  
public void DeleteItem(string item);  
```  
  
 Ответ от сервера имеет приблизительно следующий вид:  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItemResponse xmlns="https://www.microsoft.com/sql/ReportingServer" />  
    </soap:Body>  
</soap:Envelope>  
```  
  
 Метод <xref:ReportService2010.ReportingService2010.DeleteItem%2A> не имеет возвращаемого значения, поэтому возвращается пустой ответ.  
  
## <a name="see-also"></a>См. также  
 [Доступ к API SOAP](accessing-the-soap-api.md)   
 [Диспетчер отчетов (службы Reporting Services в основном режиме)](../report-manager-ssrs-native-mode.md)   
 [Сервер отчетов Reporting Services](../reporting-services-report-server.md)   
 [Веб-службы сервера отчетов](report-server-web-service.md)  
  
  
