---
title: "Веб-служба проверки подлинности | Документы Microsoft"
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
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 727d9ccd8cd1e40d89cfe74291edae92988b407c
ms.openlocfilehash: be7e76aa26ca4b94afd2e32b40b9fbfbe92b170d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="web-service-authentication"></a>Проверка подлинности веб-службы
  Для проверки подлинности запросов, поступающих веб-службе сервера отчетов, можно использовать как проверку подлинности Windows, так и обычную проверку подлинности. Любой клиент, отправляющий SOAP-запросы на сервер отчетов должен реализовать клиентскую часть одного из поддерживаемых протоколов проверки подлинности. Если вы используете [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], можно использовать классы HTTP управляемого кода для реализации проверки подлинности. Использование данных API-интерфейсов облегчает пересылку данных проверки подлинности вместе с SOAP-запросами.  
  
 Если пользователь не обладает необходимыми учетными данными для вызова веб-службы сервера отчетов, то вызов завершится с ошибкой. Во время выполнения, можно передать учетные данные для веб-службы, задав **учетные данные** свойство клиентский объект, представляющий веб-службы, прежде чем вызывать его методы.  
  
 В следующих разделах содержится пример кода, отправляющий учетные данные с помощью платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="windows-authentication"></a>Проверка подлинности Windows.  
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
  
 Учетные данные следует задать до вызова любых методов веб-службы сервера отчетов. Если учетные данные не задана, появляется код ошибки возникает ошибка HTTP 401: Отказано в доступе. Необходимо проверить подлинность службы перед ее использовать, но после выбора учетных данных, необязательно задавать их повторно при условии, что можно продолжать использовать та же переменная службы (такие как *rs*).  
  
## <a name="custom-authentication"></a>Нестандартная проверка подлинности  
 В службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] включен API-интерфейс программирования, обеспечивающий разработчикам возможность проектирования и разработки нестандартных модулей проверки подлинности, также известных как модули безопасности. Дополнительные сведения см. в разделе [Implementing a Security Extension](../../../reporting-services/extensions/security-extension/implementing-a-security-extension.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
