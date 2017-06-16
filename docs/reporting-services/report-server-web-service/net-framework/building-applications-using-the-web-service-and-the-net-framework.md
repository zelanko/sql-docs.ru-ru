---
title: "Построение приложений с помощью веб-службы и .NET Framework | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 58588838e0e74b545290df5ff0e77dc68ad5e918
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a>Building Applications Using the Web Service and the .NET Framework
  С [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], можно использовать знакомые программные конструкции, например методы, простые типы и определяемые пользователем сложные типы для работы с веб-службами. В платформе [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] содержится инфраструктура и средства, которые можно использовать для создания клиентов веб-службы, которые могут вызвать любую веб-службу, совместимую со стандартами консорциума World Wide Web (W3C).  
  
 Клиент веб-службы сервера отчетов — это любой компонент или приложение, которое обменивается данными с сервером отчетов посредством сообщений SOAP.  
  
 **Чтобы создать отчет клиент веб-сервера службы с помощью .NET Framework, выполните следующие основные шаги:**  
  
1.  Создание класса-посредника для веб-службы.  
  
     Чтобы сделать это, необходимо добавить класс-посредник или веб-ссылку на разрабатываемый проект, сослаться на класс-посредник в коде клиента и создать экземпляр данного класса-посредника. Дополнительные сведения см. в разделе [создание прокси веб-службы](../../../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md).  
  
2.  Выполнение проверки подлинности клиента веб-службы на сервере отчетов.  
  
     Для этого необходимо задать для свойства <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> объекта службы значение, равное значению учетных данных авторизованного пользователя на сервере отчетов. Дополнительные сведения см. в разделе [веб-службы проверки подлинности](../../../reporting-services/report-server-web-service/net-framework/web-service-authentication.md).  
  
3.  Вызов метода класса-посредника, соответствующего операции веб-службы, которую необходимо вызвать.  
  
     Чтобы сделать это, вызовите метод веб-службы и предоставьте необходимые аргументы. Дополнительные сведения о методы веб-службы см. в разделе [методы веб-службы отчетов сервера](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md). Дополнительные сведения о вызове см. в разделе [вызова методов веб-службы](../../../reporting-services/report-server-web-service/net-framework/calling-web-service-methods.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Создание прокси веб-службы](../../../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md)|Описание способов добавления класса-посредника в проект, использующий [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].|  
|[Веб-служба проверки подлинности](../../../reporting-services/report-server-web-service/net-framework/web-service-authentication.md)|Описывает процесс проверки подлинности вызовов к веб-службе сервера отчетов.|  
|[Вызов методов веб-службы](../../../reporting-services/report-server-web-service/net-framework/calling-web-service-methods.md)|Описывает, как использовать API-Интерфейс SOAP для вызова методов веб-службы в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].|  
|[Задание свойства URL-адрес веб-службы](../../../reporting-services/report-server-web-service/net-framework/setting-the-url-property-of-the-web-service.md)|Описывает процесс программного перенаправления учетной записи-посредника веб-службы на URL-адрес нового сервера после создания веб-ссылки.|  
|[Аргументов метода Web Service](../../../reporting-services/report-server-web-service/net-framework/supplying-web-service-method-arguments.md)|Описывает процесс вызова метода веб-службы и предоставления аргументов метода.|  
|[Пропуск значений для объектов необязательно веб-службы](../../../reporting-services/report-server-web-service/net-framework/omitting-values-for-optional-web-service-objects.md)|Описывает процесс пропуска значений для необязательных объектов веб-службы.|  
|[С помощью методов безопасных веб-службы](../../../reporting-services/report-server-web-service/net-framework/using-secure-web-service-methods.md)|Описывает **SecureConnectionLevel** и то, как он влияет использование API SOAP служб Reporting Services.|  
|[Передача настроек сведений об устройстве для модулей подготовки отчетов](../../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)|Описываются настройки сведений об устройстве, используемые для подготовки отчетов в различных форматах.|  
|[Настройки модуля доставки Reporting Services](../../../reporting-services/report-server-web-service/net-framework/reporting-services-delivery-extension-settings.md)|Описываются параметры, используемые для доставки отчетов с использованием электронной почты сервера отчетов.|  
|[Использование службы Reporting Services заголовки SOAP](../../../reporting-services/report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|Описывает использование заголовков SOAP в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Введение в обработку исключений в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|Предоставляет сведения о процессе обработки ошибок в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также:  
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Технический справочник по &#40; Службы SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
