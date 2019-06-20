---
title: Проверка подлинности в службах Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], authentication
- forms-based authentication [Reporting Services]
- authentication [Reporting Services]
- custom authentication [Reporting Services]
ms.assetid: 103ce1f9-31d8-44bb-b540-2752e4dcf60b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c4fc4d98eb32fb07def2fd317ebb7f5a6f6332cb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63282154"
---
# <a name="authentication-in-reporting-services"></a>Проверка подлинности в службах Reporting Services
  Проверка подлинности — это процесс определения прав пользователя на удостоверение. Чтобы проверить подлинность, можно использовать много методов. Самым распространенным является использование паролей. Например, если разрабатывается проверка подлинности с помощью форм, необходима реализация, которая запрашивает у пользователей учетные данные (обычно с помощью интерфейса, который запрашивает имя и пароль), а затем проверяет пользователей по хранилищу данных, которым может быть таблица, база данных или файл конфигурации. Если не удается проверить учетные данные, то процесс проверки подлинности завершается неуспешно и для пользователя принимается анонимное удостоверение.  
  
## <a name="custom-authentication-in-reporting-services"></a>Нестандартная проверка подлинности в службах Reporting Services  
 Операционная система Windows в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] выполняет проверку подлинности пользователей с помощью встроенной безопасности Windows или путем явного получения и проверки учетных данных пользователя. В службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] можно разработать нестандартную проверку подлинности, чтобы обеспечить поддержку дополнительных схем проверки подлинности. Это возможно с помощью интерфейса модуля безопасности <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>. Все модули, развертываемые и используемые на сервере отчетов, наследуют базовый интерфейс <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Интерфейсы <xref:Microsoft.ReportingServices.Interfaces.IExtension> и <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension> входят в пространство имен <xref:Microsoft.ReportingServices.Interfaces>.  
  
 Основным способом проверки подлинности на сервере отчетов в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] служит метод <xref:ReportService2010.ReportingService2010.LogonUser%2A>. Этот элемент веб-службы Reporting Services можно использовать для передачи учетных данных пользователя на сервер отчетов для проверки. Пользовательский базовый модуль безопасности реализует **IAuthenticationExtension.LogonUser** которого содержит код нестандартной проверки подлинности. В образце проверки подлинности с помощью форм метод **LogonUser** выполняет проверку подлинности по переданным учетным данным и хранилищу пользователей в базе данных. Пример реализации метода **LogonUser** имеет следующий вид:  
  
```  
public bool LogonUser(string userName, string password, string authority)  
{  
   return AuthenticationUtilities.VerifyPassword(userName, password);  
}  
  
```  
  
 Следующий образец функции используется для проверки переданных учетных данных:  
  
```  
  
internal static bool VerifyPassword(string suppliedUserName,  
   string suppliedPassword)  
{   
   bool passwordMatch = false;  
   // Get the salt and pwd from the database based on the user name.  
   // See "How To: Use DPAPI (Machine Store) from ASP.NET," "How To:  
   // Use DPAPI (User Store) from Enterprise Services," and "How To:  
   // Create a DPAPI Library" for more information about how to use  
   // DPAPI to securely store connection strings.  
   SqlConnection conn = new SqlConnection(  
      "Server=localhost;" +   
      "Integrated Security=SSPI;" +  
      "database=UserAccounts");  
   SqlCommand cmd = new SqlCommand("LookupUser", conn);  
   cmd.CommandType = CommandType.StoredProcedure;  
  
   SqlParameter sqlParam = cmd.Parameters.Add("@userName",  
       SqlDbType.VarChar,  
       255);  
   sqlParam.Value = suppliedUserName;  
   try  
   {  
      conn.Open();  
      SqlDataReader reader = cmd.ExecuteReader();  
      reader.Read(); // Advance to the one and only row  
      // Return output parameters from returned data stream  
      string dbPasswordHash = reader.GetString(0);  
      string salt = reader.GetString(1);  
      reader.Close();  
      // Now take the salt and the password entered by the user  
      // and concatenate them together.  
      string passwordAndSalt = String.Concat(suppliedPassword, salt);  
      // Now hash them  
      string hashedPasswordAndSalt =  
         FormsAuthentication.HashPasswordForStoringInConfigFile(  
         passwordAndSalt,  
         "SHA1");  
      // Now verify them. Returns true if they are equal.  
      passwordMatch = hashedPasswordAndSalt.Equals(dbPasswordHash);  
   }  
   catch (Exception ex)  
   {  
       throw new Exception("Exception verifying password. " +  
          ex.Message);  
   }  
   finally  
   {  
       conn.Close();  
   }  
   return passwordMatch;  
}  
```  
  
## <a name="authentication-flow"></a>Поток проверки подлинности  
 Веб-служба Reporting Services предоставляет нестандартные модули проверки подлинности, позволяющие реализовать проверку подлинности с помощью форм в диспетчере отчетов и на сервере отчетов.  
  
 Метод <xref:ReportService2010.ReportingService2010.LogonUser%2A> веб-службы Reporting Services позволяет отправлять учетные данные на сервер отчетов для проверки подлинности. Веб-служба использует заголовки HTTP для передачи билета проверки подлинности (называемого куки-файлом) с сервера на клиент для проверяемых запросов входа в систему.  
  
 На следующем рисунке представлен метод проверки подлинности пользователей в веб-службе, где приложение развернуто на сервере отчетов, настроенном для использования нестандартного модуля проверки подлинности.  
  
 ![Поток проверки подлинности служб Reporting Services](../../media/rosettasecurityextensionauthenticationflow.gif "Поток проверки подлинности служб Reporting Services")  
  
 На рис. 1 процесс проверки подлинности представлен следующим образом.  
  
1.  Клиентское приложение вызывает метод <xref:ReportService2010.ReportingService2010.LogonUser%2A> веб-службы для проверки подлинности пользователя.  
  
2.  Веб-служба выполняет вызов <xref:ReportService2010.ReportingService2010.LogonUser%2A> метод расширения безопасности, в частности, класс, реализующий **IAuthenticationExtension**.  
  
3.  Реализация метода <xref:ReportService2010.ReportingService2010.LogonUser%2A> проверяет имя пользователя и пароль в хранилище пользователей или в центре безопасности.  
  
4.  После успешной проверки подлинности веб-служба создает куки-файл и управляет им в ходе сеанса.  
  
5.  Веб-служба возвращает билет проверки подлинности в вызывающее приложение с помощью заголовка HTTP.  
  
 При успешной проверке подлинности пользователя с помощью модуля безопасности веб-служба создает куки-файл, который используется для последующих запросов. Куки-файл не может сохраняться в пользовательском центре безопасности, поскольку сервер отчетов не владеет центром безопасности. Куки-файл возвращается из метода веб-службы <xref:ReportService2010.ReportingService2010.LogonUser%2A> и используется в последующих вызовах метода веб-службы и при доступе по URL-адресу.  
  
> [!NOTE]  
>  Чтобы предотвратить несанкционированный доступ к куки-файлу во время передачи, файлы cookie, используемые для проверки подлинности, возвращаемые методом <xref:ReportService2010.ReportingService2010.LogonUser%2A>, должны передаваться безопасным способом с помощью шифрования по протоколу SSL.  
  
 Во время доступа к серверу отчетов по URL-адресу, если установлен настраиваемый модуль безопасности, службы IIS и [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] автоматически управляют передачей билета проверки подлинности. Если доступ к серверу отчетов выполняется через API SOAP, в реализацию класса-посредника необходимо включить дополнительную поддержку управления билетом проверки подлинности. Дополнительные сведения об использовании API SOAP и управлении билетом проверки подлинности см. в разделе «Использование веб-служб с пользовательской безопасностью».  
  
## <a name="forms-authentication"></a>Проверка подлинности с помощью форм  
 Проверка подлинности с помощью форм — это тип проверки подлинности [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], в котором пользователь, не прошедший проверку, направляется в HTML-форму. Когда пользователь предоставляет учетные данные, система создает куки-файл, содержащий билет проверки подлинности. При последующих запросах система сначала проверяет куки-файл, чтобы определить, прошел ли пользователь проверку подлинности на сервере отчетов.  
  
 Можно расширить службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] для поддержки проверки подлинности с помощью форм, используя интерфейсы расширения системы безопасности, доступные через API служб Reporting Services. При расширении служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] для использования проверки подлинности с помощью форм используйте для всех каналов связи с сервером отчетов протокол SSL, чтобы предотвратить возможность доступа злоумышленника к куки-файлу другого пользователя. Протокол SSL позволяет клиентам и серверу отчетов проверять подлинность друг друга и обеспечивать невозможность считывания содержимого, передаваемого между двумя компьютерами, с других компьютеров. Все данные, отправляемые с клиента через SSL-соединению, шифруются, чтобы исключить возможность перехвата злоумышленником паролей или данных, отправляемых на сервер отчетов.  
  
 Проверка подлинности с помощью форм обычно реализуется для поддержки учетных записей и проверки подлинности на платформах, отличных от Windows. Для пользователя, запрашивающего доступ к серверу отчетов, выводится графический интерфейс, а введенные учетные данные отправляются в центр безопасности для проверки подлинности.  
  
 Для проверки подлинности с помощью форм необходимо присутствие пользователя, вводящего учетные данные. Для приложений, которые работают в автоматическом режиме и связываются непосредственно с веб-службами служб Reporting Services, проверку подлинности с помощью форм необходимо сочетать со схемой нестандартной проверки подлинности.  
  
 Использование проверки подлинности с помощью форм в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] оправдано в следующих случаях.  
  
-   Необходимо сохранять и проверять подлинность пользователей, не обладающих учетными записями [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows.  
  
-   Необходимо предоставлять собственную форму пользовательского интерфейса в виде страницы входа между различными страницами на веб-сайте.  
  
 При создании настраиваемого модуля безопасности, поддерживающего проверку подлинности с помощью форм, учитывайте следующие факторы.  
  
-   Если используется проверка подлинности с помощью форм, необходимо включить анонимный доступ для виртуального каталога сервера отчетов в службах IIS.  
  
-   Для [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] необходимо установить проверку подлинности с помощью форм. Проверка подлинности [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] для сервера отчетов настраивается в файле Web.config.  
  
-   Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] могут проверять подлинность и авторизовывать пользователей с помощью проверки подлинности Windows или нестандартной проверки подлинности, но оба метода не могут использоваться одновременно. Службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] не поддерживают одновременное использование нескольких модулей безопасности.  
  
## <a name="see-also"></a>См. также  
 [Реализация модуля безопасности](../security-extension/implementing-a-security-extension.md)  
  
  
