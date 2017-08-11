---
title: "Использование доступа по URL-адрес в приложении Windows | Документы Microsoft"
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
- Windows applications [Reporting Services]
- Web Browser controls [Reporting Services]
- Windows Forms [Reporting Services]
- browser controls [Reporting Services]
- URL access [Reporting Services], Windows applications
ms.assetid: a4b222e5-0cbd-409c-92c4-046a674db8ac
caps.latest.revision: 48
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 782be214cb491e1fdddf6ff7d45ac377fcfbf8a4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="integrating-reporting-services-using-url-access---windows-application"></a>Интеграция служб Reporting Services с использованием URL - приложения Windows
  Доступ к серверу отчетов по URL-адресу оптимизирован для веб-среды, его также можно использовать для внедрения отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в приложение [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Однако для доступа по URL-адресу, в котором используется Windows Forms, по-прежнему необходимо применение технологии веб-браузера. Для интеграции доступа по URL-адресу и Windows Forms можно использовать следующие сценарии.  
  
-   Отображение отчета из приложения Windows Forms путем программного запуска веб-браузера.  
  
-   Использование элемента управления <xref:System.Windows.Forms.WebBrowser> на форме Windows Forms для отображения отчета.  
  
## <a name="starting-internet-explorer-from-a-windows-form"></a>Запуск обозревателя Internet Explorer из формы Windows Forms  
 С помощью класса <xref:System.Diagnostics.Process> можно получить доступ к процессу, выполняющемуся на компьютере. <xref:System.Diagnostics.Process> Класс полезен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] конструкция запуск, остановка, управление и наблюдение за приложениями. Чтобы просмотреть определенный отчет в базе данных сервера отчетов, можно запустить **IExplore** процесс, передавая ему в URL-АДРЕСЕ отчета. С помощью следующего примера кода можно запустить обозреватель [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer и передать определенный URL-адрес отчета, когда пользователь нажимает кнопку на форме Windows Forms.  
  
```vb  
Private Sub viewReportButton_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles viewReportButton.Click  
   ' Build the URL access string based on values supplied by a user  
   Dim url As String = serverUrlTextBox.Text + "?" & reportPathTextBox.Text & _  
   "&rs:Command=Render" & "&rs:Format=HTML4.0"  
  
   ' If the user does not select the toolbar check box,  
   ' turn the toolbar off in the HTML Viewer  
   If toolbarCheckBox.Checked = False Then  
      url += "&rc:Toolbar=False"  
   End If  
   ' load report in the Web browser  
   Try  
      System.Diagnostics.Process.Start("IExplore", url)  
   Catch  
      MessageBox.Show("The system could not start the specified report using Internet Explorer.", _  
      "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error)  
   End Try  
End Sub 'viewReportButton_Click  
```  
  
```csharp  
// Sample click event for a Button control on a Windows Form  
private void viewReportButton_Click(object sender, System.EventArgs e)  
{  
   // Build the URL access string based on values supplied by a user  
   string url = serverUrlTextBox.Text + "?" + reportPathTextBox.Text +  
      "&rs:Command=Render" + "&rs:Format=HTML4.0";  
  
   // If the user does not check the toolbar check box,  
   // turn the toolbar off in the HTML Viewer  
   if (toolbarCheckBox.Checked == false)  
      url += "&rc:Toolbar=False";  
  
   // load report in the Web browser  
   try  
   {  
      System.Diagnostics.Process.Start("IExplore", url);  
   }  
  
   catch (Exception)  
   {  
      MessageBox.Show(  
         "The system could not open the specified report using Internet Explorer.",   
         "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error);  
   }  
}  
```  
  
## <a name="embedding-a-browser-control-on-a-windows-form"></a>Внедрение элемента управления браузера в форму Windows Forms  
 Если не требуется просматривать отчет во внешнем веб-браузере, то можно обеспечить безукоризненное внедрение веб-браузера в форму Windows Forms с использованием элемента управления <xref:System.Windows.Forms.WebBrowser>.  
  
###### <a name="to-add-the-webbrowser-control-to-your-windows-form"></a>Добавление элемента управления WebBrowser в форму Windows Forms  
  
1.  Создайте новое приложение Windows либо [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
2.  Найдите <xref:System.Windows.Forms.WebBrowser> управления **элементов** диалоговое окно.  
  
     Если **элементов** является невидимым его можно открыть, щелкнув **представление** элемента меню и выбрав **элементов**.  
  
3.  Перетащите <xref:System.Windows.Forms.WebBrowser>управления на поверхность разработки формы Windows Forms.  
  
     <xref:System.Windows.Forms.WebBrowser>В форму добавляется элемент управления с именем webBrowser1  
  
 Чтобы направить <xref:System.Windows.Forms.WebBrowser> управления на URL-адрес путем вызова его **Navigate** метод. Для элемента управления <xref:System.Windows.Forms.WebBrowser> можно назначить строку доступа по URL-адресу во время выполнения, как показано в следующем примере.  
  
```vb  
Dim url As String = "http://localhost/reportserver?/" & _  
                    "AdventureWorks2012 Sample Reports/" & _  
                    "Company Sales&rs:Command=Render"  
WebBrowser1.Navigate(url)  
```  
  
```csharp  
string url = "http://localhost/reportserver?/" +  
             "AdventureWorks2012 Sample Reports/" +  
             "Company Sales&rs:Command=Render";  
webBrowser1.Navigate(url);  
```  
  
## <a name="see-also"></a>См. также:  
 [Интеграция служб Reporting Services в приложения](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Интеграция служб Reporting Services с помощью URL-адресов](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [Интеграция служб Reporting Services с использованием SOAP](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)   
 [Интеграция служб Reporting Services с помощью элементов управления ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)   
 [Доступ к URL-адрес &#40; Службы SSRS &#41;](../../reporting-services/url-access-ssrs.md)  
  
  
