---
title: Использование доступа по URL-адресу в приложении Windows | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- Windows applications [Reporting Services]
- Web Browser controls [Reporting Services]
- Windows Forms [Reporting Services]
- browser controls [Reporting Services]
- URL access [Reporting Services], Windows applications
ms.assetid: a4b222e5-0cbd-409c-92c4-046a674db8ac
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: fe263ce5008c98fa620aa54baad10490529aed0e
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018086"
---
# <a name="using-url-access-in-a-windows-application"></a>Использование доступа по URL-адресу в приложении Windows
  Доступ к серверу отчетов по URL-адресу оптимизирован для веб-среды, его также можно использовать для внедрения отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в приложение [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Однако для доступа по URL-адресу, в котором используется Windows Forms, по-прежнему необходимо применение технологии веб-браузера. Для интеграции доступа по URL-адресу и Windows Forms можно использовать следующие сценарии.  
  
-   Отображение отчета из приложения Windows Forms путем программного запуска веб-браузера.  
  
-   Использование элемента управления <xref:System.Windows.Forms.WebBrowser> на форме Windows Forms для отображения отчета.  
  
## <a name="starting-internet-explorer-from-a-windows-form"></a>Запуск обозревателя Internet Explorer из формы Windows Forms  
 С помощью класса <xref:System.Diagnostics.Process> можно получить доступ к процессу, выполняющемуся на компьютере. Класс <xref:System.Diagnostics.Process> является конструкцией [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], которую удобно использовать для запуска и остановки приложений, управления приложениями и наблюдения за приложениями. Чтобы просмотреть определенный отчет в базе данных сервера отчетов, можно запустить процесс **IExplore**, передав URL-адрес отчета. С помощью следующего примера кода можно запустить обозреватель [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer и передать определенный URL-адрес отчета, когда пользователь нажимает кнопку на форме Windows Forms.  
  
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
  
1.  Создайте новое приложение Windows на языке [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] или [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
2.  Перейдите к элементу управления <xref:System.Windows.Forms.WebBrowser> в диалоговом окне **Область элементов**.  
  
     Если окно **Область элементов** скрыто, его можно вызвать, выбрав в меню **Вид** пункт **Область элементов**.  
  
3.  Перетащите элемент управления <xref:System.Windows.Forms.WebBrowser> в область конструктора в Windows Forms.  
  
     В форму будет добавлен элемент управления <xref:System.Windows.Forms.WebBrowser> с именем webBrowser1.  
  
 Чтобы направить элемент управления <xref:System.Windows.Forms.WebBrowser> на URL-адрес, вызовите метод **Navigate**. Для элемента управления <xref:System.Windows.Forms.WebBrowser> можно назначить строку доступа по URL-адресу во время выполнения, как показано в следующем примере.  
  
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
  
## <a name="see-also"></a>См. также  
 [Интеграция служб Reporting Services в приложения](../application-integration/integrating-reporting-services-into-applications.md)   
 [Интеграция служб Reporting Services с помощью доступа по URL-адресу](integrating-reporting-services-using-url-access.md)   
 [Интеграция служб Reporting Services с использованием протокола SOAP](integrating-reporting-services-using-soap.md)   
 [Интеграция служб Reporting Services с помощью элементов управления ReportViewer](integrating-reporting-services-using-reportviewer-controls.md)   
 [Доступ по URL-адресу (службы SSRS)](../url-access-ssrs.md)  
  
  
