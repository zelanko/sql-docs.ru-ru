---
title: "Отправка сообщения электронной почты в формате HTML с помощью задачи «скрипт» | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Send Mail task [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], HTML mail message
ms.assetid: dd2b1eef-b04f-4946-87ab-7bc56bb525ce
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: b5f50a79ca83243ea130c77a0d95ab402ba2d31a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="sending-an-html-mail-message-with-the-script-task"></a>Отправка почтового сообщения в формате HTML с помощью задачи «Скрипт»
  Задача «Отправка почты» служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] поддерживает только почтовые сообщения в текстовом формате. Однако отправлять почтовые сообщения в формате HTML можно с помощью задачи «Скрипт» и почтовых функций платформы .NET Framework.  
  
> [!NOTE]  
>  Если нужно создать задачу, которую будет удобно использовать в нескольких пакетах, рекомендуется начать разработку пользовательской задачи с этого образца задачи «Скрипт». Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 В следующем примере используется **System.Net.Mail** пространство имен для настройки и передачи почтового сообщения в формате HTML. Скрипт получает To, From, темы и текст сообщения электронной почты из переменных пакета, использует их для создания нового **MailMessag**e и присваивает его **IsBodyHtml** свойства **True**. Затем сценарий получает имя SMTP-сервера из другой переменной пакета, инициализирует экземпляр **System.Net.Mail.SmtpClient**и вызывает его **отправки** метод для отправки сообщения в формате HTML. В образце функциональность отправки сообщений инкапсулируется в подпрограмме, которая может быть использована повторно в других скриптах.  
  
#### <a name="to-configure-this-script-task-example-without-an-smtp-connection-manager"></a>Настройка этого примера задачи «Скрипт» без диспетчера соединений SMTP  
  
1.  Создайте строковые переменные с именами `HtmlEmailTo`, `HtmlEmailFrom` и `HtmlEmailSubject`, затем присвойте им соответствующие значения, чтобы получить допустимое тестовое сообщение.  
  
2.  Создайте строковую переменную с именем `HtmlEmailBody` и присвойте ей в качестве значения строку с разметкой HTML. Например:  
  
    ```  
    <html><body><h1>Testing</h1><p>This is a <b>test</b> message.</p></body></html>  
    ```  
  
3.  Создайте строковую переменную с именем `HtmlEmailServer` и присвойте ей в качестве значения имя доступного SMTP-сервера, принимающего анонимные исходящие сообщения.  
  
4.  Все эти пять переменных для назначения **ReadOnlyVariables** свойства новой задачи «скрипт».  
  
5.  Импорт **System.Net** и **System.Net.Mail** пространства имен в код.  
  
 В образце кода в этом разделе имя SMTP-сервера извлекается из переменной пакета. Однако можно также воспользоваться возможностью диспетчера соединений SMTP по инкапсуляции данных соединения и извлечению имени сервера из диспетчера соединений в пользовательском коде. Метод <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> диспетчера соединений SMTP возвращает строку в следующем формате:  
  
 `SmtpServer=smtphost;UseWindowsAuthentication=False;EnableSsl=False;`  
  
 Можно использовать **String.Split** метод, чтобы разделить этот список аргументов в массив отдельных строк по каждой точки с запятой (;), или равен знак (=), а затем извлечь второй аргумент (subscript 1) из массива в качестве имени сервера.  
  
#### <a name="to-configure-this-script-task-example-with-an-smtp-connection-manager"></a>Настройка этого примера задачи «Скрипт» с диспетчером соединений SMTP  
  
1.  Измените задачу «скрипт», настроенную выше, удалив `HtmlEmailServer` переменных из списка **ReadOnlyVariables**.  
  
2.  Замените строку кода, извлекающую имя сервера:  
  
    ```  
    Dim smtpServer As String = _  
      Dts.Variables("HtmlEmailServer").Value.ToString  
    ```  
  
     следующими строками:  
  
    ```  
    Dim smtpConnectionString As String = _  
      DirectCast(Dts.Connections("SMTP Connection Manager").AcquireConnection(Dts.Transaction), String)  
    Dim smtpServer As String = _  
      smtpConnectionString.Split(New Char() {"="c, ";"c})(1)  
    ```  
  
## <a name="code"></a>код  
  
```vb  
Public Sub Main()  
  
  Dim htmlMessageTo As String = _  
    Dts.Variables("HtmlEmailTo").Value.ToString  
  Dim htmlMessageFrom As String = _  
    Dts.Variables("HtmlEmailFrom").Value.ToString  
  Dim htmlMessageSubject As String = _  
    Dts.Variables("HtmlEmailSubject").Value.ToString  
  Dim htmlMessageBody As String = _  
    Dts.Variables("HtmlEmailBody").Value.ToString  
  Dim smtpServer As String = _  
    Dts.Variables("HtmlEmailServer").Value.ToString  
  
  SendMailMessage( _  
      htmlMessageTo, htmlMessageFrom, _  
      htmlMessageSubject, htmlMessageBody, _  
      True, smtpServer)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
  
Private Sub SendMailMessage( _  
    ByVal SendTo As String, ByVal From As String, _  
    ByVal Subject As String, ByVal Body As String, _  
    ByVal IsBodyHtml As Boolean, ByVal Server As String)  
  
  Dim htmlMessage As MailMessage  
  Dim mySmtpClient As SmtpClient  
  
  htmlMessage = New MailMessage( _  
    SendTo, From, Subject, Body)  
  htmlMessage.IsBodyHtml = IsBodyHtml  
  
  mySmtpClient = New SmtpClient(Server)  
  mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials  
  mySmtpClient.Send(htmlMessage)  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            string htmlMessageTo = Dts.Variables["HtmlEmailTo"].Value.ToString();  
            string htmlMessageFrom = Dts.Variables["HtmlEmailFrom"].Value.ToString();  
            string htmlMessageSubject = Dts.Variables["HtmlEmailSubject"].Value.ToString();  
            string htmlMessageBody = Dts.Variables["HtmlEmailBody"].Value.ToString();  
            string smtpServer = Dts.Variables["HtmlEmailServer"].Value.ToString();  
  
            SendMailMessage(htmlMessageTo, htmlMessageFrom, htmlMessageSubject, htmlMessageBody, true, smtpServer);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
        private void SendMailMessage(string SendTo, string From, string Subject, string Body, bool IsBodyHtml, string Server)  
        {  
  
            MailMessage htmlMessage;  
            SmtpClient mySmtpClient;  
  
            htmlMessage = new MailMessage(SendTo, From, Subject, Body);  
            htmlMessage.IsBodyHtml = IsBodyHtml;  
  
            mySmtpClient = new SmtpClient(Server);  
            mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials;  
            mySmtpClient.Send(htmlMessage);  
  
        }  
```  
  
## <a name="see-also"></a>См. также:  
 [Отправка почты задач](../../integration-services/control-flow/send-mail-task.md)  
  
  
