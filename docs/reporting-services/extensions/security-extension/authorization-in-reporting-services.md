---
title: "Авторизация в службах Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- authorization [Reporting Services]
ms.assetid: 15fc1c7b-560c-4737-b126-e0d428a1b530
caps.latest.revision: 20
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b97911d8adf797fdf324e0c97863dadd611ca596
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="authorization-in-reporting-services"></a>Авторизация в службах Reporting Services
  Авторизация является процессом определения, должен ли быть предоставлен идентификатору запрошенный тип доступа к конкретному ресурсу в базе данных сервера отчетов. Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] используют архитектуру авторизации на основе ролей, которая предоставляет пользователю доступ к конкретному ресурсу на основании назначенной этому пользователю роли в данном приложении. Модули безопасности для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] содержат реализацию компонента авторизации, который используется для предоставления доступа пользователям после прохождения ими проверки подлинности на сервере отчетов. Авторизация вызывается, когда пользователь пытается выполнить операцию в системе или на элементе сервера через API-интерфейс SOAP, либо посредством доступа по URL-адресу. Это стало возможным благодаря интерфейсу модуля безопасности **IAuthorizationExtension2**. Как указывалось выше, все развертываемые модули наследуют от базового интерфейса **IExtension** . **IExtension** и **IAuthorizationExtension2** являются членами **Microsoft.ReportingServices.Interfaces** пространства имен.  
  
## <a name="checking-access"></a>Проверка доступа  
 При авторизации необходимым условием пользовательской реализации безопасности является проверка доступа, реализованная в методе <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>. Метод <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> вызывается при каждой попытке пользователя выполнить операцию на сервере отчетов. Метод <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> перегружается для всех типов операций. Для операций с папками пример проверки доступа может выглядеть следующим образом:  
  
```  
// Overload for Folder operations  
public bool CheckAccess(  
   string userName,   
   IntPtr userToken,   
   byte[] secDesc,   
   FolderOperation requiredOperation)  
{  
   // If the user is the administrator, allow unrestricted access.  
   if (userName == m_adminUserName)   
      return true;  
  
   AceCollection acl = DeserializeAcl(secDesc);  
   foreach(AceStruct ace in acl)  
   {  
         if (userName == ace.PrincipalName)  
         {  
            foreach(FolderOperation aclOperation in   
               ace.FolderOperations)  
            {  
               if (aclOperation == requiredOperation)  
                     return true;  
            }  
         }  
   }  
   return false;  
}  
```  
  
 Сервер отчетов вызывает метод <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>, передавая имя зарегистрированного пользователя, токен пользователя, дескриптор безопасности для элемента и запрошенную операцию. Здесь проводится проверка дескриптора безопасности для имени пользователя и наличия должного разрешения на выполнение запроса, в результате чего возвращается значение **true** для указания, что доступ предоставлен или **false** для указания, что в доступе отказано.  
  
## <a name="security-descriptors"></a>Дескрипторы безопасности  
 При установке политик авторизации для элементов в базе данных сервера отчетов, клиентское приложение (такое как диспетчер отчетов) передает сведения о пользователе в модуль безопасности вместе с политикой безопасности для данного элемента. Эта политика безопасности и сведения о пользователях вместе называются дескриптором безопасности. Дескриптор безопасности содержит следующие сведения для элемента в базе данных сервера отчетов:  
  
-   Группа или пользователь, имеющие определенный тип разрешений на выполнение операций с этим элементом.  
  
-   Тип данного элемента.  
  
-   Список управления доступом, управляющий доступом к этому элементу.  
  
 Дескрипторы безопасности создаются при помощи методов <xref:ReportService2010.ReportingService2010.SetPolicies%2A> и <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> веб-службы.  
  
### <a name="authorization-flow"></a>Поток авторизации  
 Авторизация служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] управляется модулем безопасности, настроенным в настоящее время для выполнения на сервере. Авторизация основана на ролях и ограничена разрешениями и операциями, предоставляемыми архитектурой безопасности служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. На следующей диаграмме показан процесс авторизации пользователей для работы с элементами в базе данных сервера отчетов.  
  
 ![Поток авторизации служб Reporting](../../../reporting-services/extensions/security-extension/media/rosettasecurityextensionauthorizationflow.gif "поток авторизации служб Reporting Services")  
  
 Как показано на этой диаграмме, авторизация выполняется в следующей последовательности.  
  
1.  После прохождения проверки подлинности клиентские приложения делают запросы серверу отчетов, используя методы веб-служб Reporting Services. Билет проверки подлинности передается серверу отчетов в форме куки-файла в заголовке HTTP каждого веб-запроса.  
  
2.  Перед любой проверкой доступа проводится проверка куки-файла.  
  
3.  После проверки куки-файла сервер отчетов вызывает метод <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> и пользователю дается идентификатор.  
  
4.  Пользователь пытается выполнить операцию с использованием веб-службы Reporting Services.  
  
5.  Сервер отчетов вызывает метод <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>.  
  
6.  Дескриптор безопасности получается и передается настраиваемой реализации модуля безопасности <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>. В этот момент пользователь, группа или компьютер сравниваются с дескриптором безопасности элемента, к которому выполняется доступ, и они авторизуются для выполнения запрошенной операции.  
  
7.  Если пользователь авторизован, веб-служба выполняет запрашиваемую операцию и возвращает ответ вызывающему приложению.  
  
  
