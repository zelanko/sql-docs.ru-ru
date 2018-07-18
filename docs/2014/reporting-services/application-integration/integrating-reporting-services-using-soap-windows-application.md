---
title: Использование API SOAP в приложении Windows | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- Windows applications [Reporting Services]
- Windows Forms [Reporting Services]
- SOAP [Reporting Services], Windows applications
ms.assetid: e4804792-20cd-4df2-9257-fb958ff447b4
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b0656f3b44e4b0aa42a1b69f2290da82b0131abd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208884"
---
# <a name="using-the-soap-api-in-a-windows-application"></a>Использование API SOAP в приложении Windows
  С помощью API SOAP служб Reporting Services можно получить доступ ко всем функциональным возможностям сервера отчетов. Поскольку API SOAP является веб-службой, к нему легко получить доступ, чтобы предоставить для пользовательских бизнес-приложений функции создания отчетов в масштабе предприятия. Чтобы получить доступ к веб-службе в приложении Windows, можно просто написать код, который вызывает службу. С помощью платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] можно создать класс-посредник, который делает доступными свойства и методы веб-службы и позволяет воспользоваться привычной инфраструктурой и программными средствами для построения бизнес-приложений на основе технологии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="integrating-report-management-functionality-using-windows-forms"></a>Интеграция функций управления отчетами с помощью Windows Forms  
 В отличие от доступа по URL-адресу, API SOAP дает доступ к полному набору функций управления, доступных на сервере отчетов. Это значит, что все административные функции диспетчера отчетов становятся доступными для разработчиков по протоколу SOAP. Таким образом, с помощью Windows Forms можно разработать законченное средство по управлению и администрированию. Например, в приложении Windows может понадобиться разрешить пользователям получать содержимое пространства имен для сервера отчетов. Чтобы вывести список всех элементов в базе данных сервера отчетов, можно использовать метод веб-службы <xref:ReportService2010.ReportingService2010.ListChildren%2A>, а затем представить эти элементы пользователям в списке, в поле со списком или в элементе управления иерархического представления. С помощью следующего кода веб-службы можно получить текущий список доступных отчетов в пользовательской папке My Reports, когда пользователь нажимает кнопку на форме:  
  
```vb  
' Button click event that retrieves a list of reports from  
' the My Reports folder and displays them in a combo box  
Private Sub listReportsButton_Click(sender As Object, e As System.EventArgs)  
   ' Create a new Web service object and set credentials  
   ' to Windows Authentication  
   Dim rs As New ReportingService2010()  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
   ' Return the list of items in My Reports  
   Dim items As CatalogItem() = rs.ListChildren("/Adventureworks 2008 Sample Reports", False)  
  
   Dim ci As CatalogItem  
   For Each ci In  items  
      ' If the item is a report, add it to   
      ' a combo box  
      If ci.TypeName = "Report" Then  
         catalogComboBox.Items.Add(ci.Name)  
      End If  
   Next ci  
End Sub 'listReportsButton_Click  
```  
  
```csharp  
// Button click event that retrieves a list of reports from  
// the My Reports folder and displays them in a combo box  
private void listReportsButton_Click(object sender, System.EventArgs e)  
{  
   // Create a new Web service object and set credentials  
   // to Windows Authentication  
   ReportingService2010 rs = new ReportingService2010();  
   rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
  
   // Return the list of items in My Reports  
   CatalogItem[] items = rs.ListChildren("/Adventureworks 2008 Sample Reports", false);  
  
   foreach (CatalogItem ci in items)  
   {  
      // If the item is a report, add it to   
      // a combo box  
      if (ci.TypeName == "Report")  
         catalogComboBox.Items.Add(ci.Name);  
   }  
}  
```  
  
 Затем можно разрешить пользователям выбрать отчет из поля со списком и просмотреть отчет на форме с помощью элемента управления веб-браузера или элемента управления «Изображение».  
  
## <a name="enabling-report-viewing-and-navigation-using-windows-forms"></a>Включение просмотра отчетов и перехода по отчетам с помощью Windows Forms  
 Для интеграции отчетов в приложения Windows Forms доступно два метода.  
  
 Можно использовать API SOAP для подготовки отчетов к просмотру в любом из поддерживаемых форматов с помощью метода <xref:ReportExecution2005.ReportExecutionService.Render%2A>. Включение просмотра отчетов и переходов по отчетов с помощью протокола SOAP сопряжено с некоторыми недостатками.  
  
-   Нельзя воспользоваться встроенными функциями панели инструментов отчета, которая доступна в средстве просмотра HTML-страниц при доступе по URL-адресу.  
  
-   При подготовке к просмотру в формате HTML изображения или ресурсы необходимо обрабатывать в отдельных потоках с помощью метода <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A>.  
  
-   Использование доступа по URL-адресу для подготовки отчетов к просмотру дает небольшое преимущество в производительности по сравнению с API SOAP.  
  
 Однако метод <xref:ReportExecution2005.ReportExecutionService.Render%2A> API SOAP позволяет готовить отчеты к просмотру и сохранять их в различных выходных форматах программным образом. Такая возможность дает преимущество над доступом по URL-адресу, для которого необходимо участие пользователя. С помощью метода <xref:ReportExecution2005.ReportExecutionService.Render%2A> API SOAP отчет можно подготовить к просмотру в любом из поддерживаемых выходных форматов.  
  
 Также можно использовать свободно распространяемые элементы управления ReportViewer, входящие в состав среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]. Элементы управления ReportViewer упрощают внедрение функций служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в пользовательские приложения. Элементы управления ReportViewer предназначены для разработчиков, которым нужно встроить в приложения заранее спроектированные отчеты. Например, приложение, предназначенное для управления веб-сайтом, может содержать отчеты, отображающие анализ посещений различных разделов веб-сайта компании. Элементы управления, внедряемые в приложение, служат простой альтернативой включению серверных компонентов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на этапе развертывания приложения. Эти элементы управления обеспечивают функциональные возможности отчетов, но не поддерживают дополнительные возможности создания, публикации, распространения и доставки отчетов, доступные в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Существует две версии элементов управления ReportViewer: одна предназначена для многофункциональных клиентских приложений Windows, а вторая — для приложений [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. Элементы управления поддерживают режимы локальной и удаленной обработки. В режиме локальной обработки приложение предоставляет определения отчетов, наборы данных и триггерную обработку отчетов. В режиме удаленной обработки получение данных и обработка отчетов выполняется на сервере отчетов, а элементы управления используются для отображения и навигации по отчету. Такая модель позволяет разрабатывать мощные, легкомасштабируемые приложения.  
  
 Документацию по элементам управления ReportViewer см. в справке по среде [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в Интернете. Дополнительные сведения см. в документации по продукту [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Создание приложений с помощью веб-службы и .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Интеграция служб Reporting Services в приложения](../application-integration/integrating-reporting-services-into-applications.md)   
 [Использование API SOAP в веб-приложении](integrating-reporting-services-using-soap-web-application.md)  
  
  
