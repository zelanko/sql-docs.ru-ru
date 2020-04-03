---
title: Доступ к интерфейсу API SOAP | Документы Майкрософт
description: Веб-служба сервера отчетов применяет протокол SOAP через протокол HTTP и действует как интерфейс связи между клиентскими программами и сервером отчетов. Используйте WSDL для вызова службы.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], WSDL
- Web service [Reporting Services], SOAP
- calling Web service
- SOAP [Reporting Services], accessing
- Report Server Web service, SOAP
- Web service [Reporting Services], WSDL
- WSDL [Reporting Services]
- XML Web service [Reporting Services], SOAP
- Report Server Web service, WSDL
- referencing WSDL
ms.assetid: 63bb870a-4dbf-46bd-8921-78f8ebe5fd75
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 165302d4bb324dfb79f43e37b8a47e5e11973ce5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "79509915"
---
# <a name="accessing-the-soap-api"></a>Доступ к API-интерфейсу SOAP
  Веб-служба сервера отчетов использует протокол SOAP по протоколу HTTP и выступает в роли интерфейса связи между клиентскими программами и сервером отчетов. Веб-служба предоставляет две конечные точки — одну для выполнения отчетов и другую для управления отчетами. Веб-служба состоит из методов и набора объектов сложного типа, которые можно использовать для доступа ко всем функциональным возможностям служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Для вызова службы следует создать ссылку на язык описания веб-служб (WSDL) служб Reporting Services.  
  
## <a name="referencing-the-reporting-services-wsdl"></a>Создание ссылок на язык WSDL для служб Reporting Services  
 Для успешного вызова веб-службы следует знать способ доступа к данной службе, поддерживаемые ей операции, параметры, ожидаемые этой службой, а также данные, которые она возвращает С помощью языка WSDL эти данные предоставляются в XML-документе, который может быть считан или обработан компьютером.  
  
 Веб-службы сервера отчетов доступны в трех различных конечных точках. Имя WSDL-файла у каждой конечной точки свое. Конечная точка <xref:ReportService2010> содержит методы для управления объектами в сервере отчетов как в собственном режиме, так и в режиме интеграции с SharePoint. Обратиться к WSDL-файлу данной конечной точки можно по адресу `ReportService2010.asmx?wsdl.`.  
  
> [!NOTE]  
>  Конечные точки <xref:ReportService2005> и <xref:ReportService2006> являются устаревшими в [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Конечная точка <xref:ReportService2010> содержит функциональные возможности обеих конечных точек, а также содержит дополнительные функции управления.  
  
-   Конечная точка <xref:ReportExecution2005> позволяет разработчикам программным образом обрабатывать и подготавливать к просмотру отчеты на сервере отчетов. Обратиться к WSDL-файлу данной конечной точки можно по адресу `ReportExecution2005.asmx?wsdl`  
  
 WSDL-файл может использоваться пакетами разработки, поддерживающими SOAP и веб-службы, например пакетом SDK для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
 В следующем примере показывается формат URL-адреса управляющего WSDL-файла служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:  
  
```  
https://server/reportserver/ReportService2010.asmx?wsdl  
```  
  
 В следующей таблице описывается каждый элемент URL-адреса.  
  
|Элемент URL-адреса|Описание|  
|-----------------|-----------------|  
|*server*|Имя сервера, на котором развернут сервер отчетов.|  
|*reportserver*|Имя папки, в которой содержится веб-служба XML. Данный элемент настраивается во время установки.|  
|*\<имя конечной точки>.asmx*|Имя конечной точки веб-службы.|  
  
 Дополнительные сведения о формате WSDL см. в спецификации языка WSDL см. на веб-сайте консорциума W3C: http://www.w3.org/TR/wsdl.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
