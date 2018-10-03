---
title: Создание приложений с помощью веб-службы и .NET Framework | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
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
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 062d7c811f0d2201fd1a0954005860a95511fb3a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105854"
---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a>Building Applications Using the Web Service and the .NET Framework
  В [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] можно использовать знакомые программные конструкции, например методы, типы-примитивы и определяемые пользователем сложные типы для работы с веб-службами. В платформе [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] содержится инфраструктура и средства, которые можно использовать для создания клиентов веб-службы, которые могут вызвать любую веб-службу, совместимую со стандартами консорциума World Wide Web (W3C).  
  
 Клиент веб-службы сервера отчетов — это любой компонент или приложение, которое обменивается данными с сервером отчетов посредством сообщений SOAP.  
  
 **Создать клиент веб-службы сервера отчетов с помощью платформы .NET Framework можно, выполнив следующие основные шаги.**  
  
1.  Создание класса-посредника для веб-службы.  
  
     Чтобы сделать это, необходимо добавить класс-посредник или веб-ссылку на разрабатываемый проект, сослаться на класс-посредник в коде клиента и создать экземпляр данного класса-посредника. Дополнительные сведения см. в разделе [Создание прокси веб-службы](creating-the-web-service-proxy.md).  
  
2.  Выполнение проверки подлинности клиента веб-службы на сервере отчетов.  
  
     Для этого необходимо задать для свойства <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> объекта службы значение, равное значению учетных данных авторизованного пользователя на сервере отчетов. Дополнительные сведения см. в разделе [Проверка подлинности веб-службы](web-service-authentication.md).  
  
3.  Вызов метода класса-посредника, соответствующего операции веб-службы, которую необходимо вызвать.  
  
     Чтобы сделать это, вызовите метод веб-службы и предоставьте необходимые аргументы. Дополнительные сведения о методах веб-службы см. в разделе [Методы веб-службы сервера отчетов](../methods/report-server-web-service-methods.md). Дополнительные сведения о вызовах см. в разделе [Вызов методов веб-службы](calling-web-service-methods.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Создание прокси веб-службы](creating-the-web-service-proxy.md)|Описывает методы добавления класса-посредника в проект с использованием [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].|  
|[Аутентификация веб-службы](web-service-authentication.md)|Описывает процесс проверки подлинности вызовов к веб-службе сервера отчетов.|  
|[Вызов методов веб-службы](calling-web-service-methods.md)|Описывает процесс использования API-интерфейса SOAP для вызова методов веб-службы в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].|  
|[Определение свойства URL-адреса веб-службы](setting-the-url-property-of-the-web-service.md)|Описывает процесс программного перенаправления учетной записи-посредника веб-службы на URL-адрес нового сервера после создания веб-ссылки.|  
|[Передача аргументов метода веб-службы](supplying-web-service-method-arguments.md)|Описывает процесс вызова метода веб-службы и предоставления аргументов метода.|  
|[Пропуск значений для необязательных объектов веб-службы](omitting-values-for-optional-web-service-objects.md)|Описывает процесс пропуска значений для необязательных объектов веб-службы.|  
|[Использование защищенных методов веб-службы](using-secure-web-service-methods.md)|Описывает параметр **SecureConnectionLevel** и то, как он влияет на использование API-интерфейса SOAP служб Reporting Services.|  
|[Передача параметров сведений об устройстве для модулей подготовки отчетов](passing-device-information-settings-to-rendering-extensions.md)|Описываются настройки сведений об устройстве, используемые для подготовки отчетов в различных форматах.|  
|[Параметры модуля доставки Reporting Services](reporting-services-delivery-extension-settings.md)|Описываются параметры, используемые для доставки отчетов с использованием электронной почты сервера отчетов.|  
|[Использование заголовков SOAP в службах Reporting Services](../../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|Описывает использование заголовков SOAP в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Общие сведения об обработке исключений в службах Reporting Services](../../report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|Предоставляет сведения о процессе обработки ошибок в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также  
 [Веб-служба сервера отчетов](../report-server-web-service.md)   
 [Технический справочник (службы SSRS)](../../technical-reference-ssrs.md)  
  
  
