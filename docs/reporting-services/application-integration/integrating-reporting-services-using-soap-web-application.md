---
title: Использование API SOAP в веб-приложениях
description: Доступ к функциональным возможностям сервера отчетов можно получить с помощью API SOAP Reporting Services, к которому можно получить доступ для предоставления функций корпоративных отчетов.
ms.date: 06/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.custom: seo-lt-2019
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], Web applications
- impersonation [Reporting Services]
- user impersonation [Reporting Services]
- report servers [Reporting Services], SOAP
- Web applications [Reporting Services]
ms.assetid: e8ca4455-0dc3-4741-8872-3636114938ad
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0a24b256e6d395b6cfd93773a8cb824fe7ba7ece
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "79198204"
---
# <a name="integrating-reporting-services-using-soap---web-application"></a>Интеграция служб Reporting Services с использованием протокола SOAP — веб-приложения
  С помощью API SOAP служб Reporting Services можно получить доступ ко всем функциональным возможностям сервера отчетов. Поскольку API SOAP является веб-службой, к нему легко получить доступ, чтобы предоставить для пользовательских бизнес-приложений функции создания отчетов в масштабе предприятия. Доступ к веб-службе сервера отчетов из веб-приложения осуществляется во многом аналогично доступу к API SOAP из приложения [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. С помощью платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] можно создать класс-посредник, который делает доступными свойства и методы веб-службы сервера отчетов и позволяет использовать привычную инфраструктуру и средства для построения бизнес-приложений на основе технологии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Функции служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] по управлению отчетами доступны из веб-приложения так же легко, как из приложения Windows. Из веб-приложения можно добавлять элементы в базу данных сервера отчетов и удалять из нее элементы, задавать параметры безопасности элемента, изменять элементы базы данных сервера отчетов, управлять планированием и доставкой, а также выполнять другие действия.  
  
## <a name="enabling-impersonation"></a>Активация олицетворения  
 Первым шагом в настройке веб-приложения является включение олицетворения со стороны клиента веб-службы. Олицетворение позволяет приложениям [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] выполняться с удостоверением клиента, от имени которого они работают. [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] с помощью служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS проверяет подлинность пользователя и передает в приложение [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] проверенный токен или (если не удалось проверить подлинность пользователя) непроверенный токен. Если включено олицетворение, приложение [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] в любом случае выполняет олицетворение любого полученного токена. Можно включить олицетворение на клиенте, изменив файл Web.config клиентского приложения следующим образом:  
  
```asp.net  
<!-- Web.config file. -->  
<identity impersonate="true"/>  
```  
  
> [!NOTE]  
>  По умолчанию олицетворение отключено.  
  
 Дополнительные сведения об олицетворении [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] см. в документации по пакету SDK для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="managing-the-report-server-using-soap-api"></a>Управление сервером отчетов с помощью API SOAP  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

 С помощью веб-приложения также можно управлять сервером отчетов и его содержимым. Диспетчер отчетов, входящий в состав служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], служит примером веб-приложения, которое целиком построено с помощью [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] и API SOAP служб Reporting Services. Можно добавить функции управления отчетами, доступные в диспетчере отчетов, в пользовательские веб-приложения. Например, вы захотите вернуть список отчетов, доступных в базе данных сервера отчетов, и отобразить их в элементе управления [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] **Listbox**, чтобы пользователи могли выбрать отчет. В следующем коде устанавливается соединение с базой данных сервера отчетов и возвращается список элементов в базе данных сервера отчетов. Затем доступные отчеты добавляются в элемент управления Listbox, в котором отображается путь к каждому отчету.  

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

 С помощью веб-приложения также можно управлять сервером отчетов и его содержимым. Веб-портал, поставляемый в комплекте с [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], служим примером веб-приложения, которое управляет большинством типичных задач Reporting Services. Вы можете добавлять в свои веб-приложения функции управления отчетами с веб-портала. Например, вы захотите вернуть список отчетов, доступных в базе данных сервера отчетов, и отобразить их в элементе управления [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] **Listbox**, чтобы пользователи могли выбрать отчет. В следующем коде устанавливается соединение с базой данных сервера отчетов и возвращается список элементов в базе данных сервера отчетов. Затем доступные отчеты добавляются в элемент управления Listbox, в котором отображается путь к каждому отчету.  

::: moniker-end
  
```vb  
Private Sub Page_Load(sender As Object, e As System.EventArgs)  
   ' Create a Web service proxy object and set credentials  
   Dim rs As New ReportingService2005()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return a list of catalog items in the report server database  
   Dim items As CatalogItem() = rs.ListChildren("/", True)  
  
   ' For each report, display the path of the report in a Listbox  
   Dim ci As CatalogItem  
   For Each ci In  items  
      If ci.Type = ItemTypeEnum.Report Then  
         catalogListBox.Items.Add(ci.Path)  
      End If  
   Next ci  
End Sub ' Page_Load   
```  
  
```csharp  
private void Page_Load(object sender, System.EventArgs e)  
{  
   // Create a Web service proxy object and set credentials  
   ReportingService2005 rs = new ReportingService2005();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return a list of catalog items in the report server database  
   CatalogItem[] items = rs.ListChildren("/", true);  
  
   // For each report, display the path of the report in a Listbox  
   foreach(CatalogItem ci in items)  
   {  
      if (ci.Type == ItemTypeEnum.Report)  
         catalogListBox.Items.Add(ci.Path);  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  

 [Создание приложений с помощью веб-службы и .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Интеграция служб Reporting Services в приложения](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Использование API SOAP в приложении Windows](../../reporting-services/application-integration/integrating-reporting-services-using-soap-windows-application.md)  
  
  
