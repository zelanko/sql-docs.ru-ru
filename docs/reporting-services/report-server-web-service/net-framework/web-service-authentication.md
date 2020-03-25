---
title: Проверка подлинности веб-службы | Документы Майкрософт
description: Если клиент выполняет запросы SOAP к серверу отчетов, реализуйте клиентскую часть проверки подлинности. Узнайте, как реализовать проверку подлинности для веб-службы.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 34873835231c122f3d086c3490be2bab7a684925
ms.sourcegitcommit: d1f6da6f0f5e9630261cf733c64958938a3eb859
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2020
ms.locfileid: "79198537"
---
# <a name="web-service-authentication"></a>Проверка подлинности веб-службы
  Для проверки подлинности запросов, поступающих веб-службе сервера отчетов, можно использовать как проверку подлинности Windows, так и обычную проверку подлинности. Любой клиент, отправляющий SOAP-запросы на сервер отчетов должен реализовать клиентскую часть одного из поддерживаемых протоколов проверки подлинности. Если используется платформа [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], то для реализации проверки подлинности можно использовать классы HTTP управляемого кода. Использование данных API-интерфейсов облегчает пересылку данных проверки подлинности вместе с SOAP-запросами.  
  
 Если пользователь не обладает необходимыми учетными данными для вызова веб-службы сервера отчетов, то вызов завершится с ошибкой. Во время выполнения учетные данные можно передать веб-службе путем настройки свойства **Credentials** объекта на стороне клиента, представляющего веб-службу. Это следует выполнить перед вызовом методов веб-службы.  
  
 В следующих разделах содержится пример кода, отправляющий учетные данные с помощью платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="windows-authentication"></a>Проверка подлинности Windows  
 Следующий код отправляет учетные данные проверки подлинности Windows веб-службе.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a>Обычная проверка подлинности  
 Следующий код отправляет учетные данные обычной проверки подлинности веб-службе.  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 Учетные данные следует задать до вызова любых методов веб-службы сервера отчетов. Если учетные данные не были заданы, то будет выведена ошибка с кодом состояния HTTP 401: Доступ запрещен. Перед использованием службы необходимо выполнить проверку подлинности, однако после того как учетные данные были заданы, нет необходимости задавать их повторно, пока используется та же переменная службы (например, *rs*).  
  
## <a name="custom-authentication"></a>Нестандартная проверка подлинности  
 В службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] включен API-интерфейс программирования, обеспечивающий разработчикам возможность проектирования и разработки нестандартных модулей проверки подлинности, также известных как модули безопасности. Дополнительные сведения см. в разделе [Implementing a Security Extension](../../../reporting-services/extensions/security-extension/implementing-a-security-extension.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
