---
title: "С помощью компонента Database Mail | Документы Microsoft"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 28082a9c402700a17c7072ed6d7dcd3a87c92bd9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="using-database-mail"></a>Использование компонента Database Mail
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]В SMO подсистема компонента Database Mail представлена <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> объекта, на который ссылается <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> свойство. С помощью объекта SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> можно настраивать подсистему компонента Database Mail и управлять профилями и учетными записями почты. SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> объект принадлежит **сервера** объекта, это означает, что область действия учетных записей почты соответствует на уровне сервера.  
  
## <a name="examples"></a>Примеры  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в разделе [Create Visual C# 35; Проект SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
 Для программ, использующих [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] компонента Database Mail, необходимо включить **Imports** инструкции для уточнения пространства имен Mail. Вставьте инструкцию после других инструкций **Imports** и перед любыми декларациями в приложении.  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a>Создание учетной записи для компонента Database Mail на языке Visual Basic  
 В этом примере кода демонстрируется создание учетной записи электронной почты в объектах SMO. Компонент Database Mail представлен объектом <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>, и на него ссылается свойство <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Server>. Объекты SMO можно использовать для программной настройки компонента Database Mail, но не для отправления или обработки полученной почты.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server()
'Define the Database Mail service with a SqlMail object variable and reference it using the Server Mail property.
Dim sm As SqlMail
sm = srv.Mail
'Define and create a mail account by supplying the Database Mail service, name, description, display name, and email address arguments in the constructor.
Dim a As MailAccount
a = New MailAccount(sm, "AdventureWorks Administrator", "AdventureWorks Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com")
a.Create()
```
  
## <a name="creating-a-database-mail-account-by-using-visual-c"></a>Создание учетной записи для компонента Database Mail на языке Visual C#  
 В этом примере кода демонстрируется создание учетной записи электронной почты в объектах SMO. Компонент Database Mail представлен объектом <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>, и на него ссылается свойство <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Server>. Объекты SMO можно использовать для программной настройки компонента Database Mail, но не для отправления или обработки полученной почты.  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.  
         Server srv = default(Server);   
           srv = new Server();   
           //Define the Database Mail service with a SqlMail object variable   
           //and reference it using the Server Mail property.   
           SqlMail sm;   
           sm = srv.Mail;   
           //Define and create a mail account by supplying the Database Mail  
           //service, name, description, display name, and email address  
           //arguments in the constructor.   
           MailAccount a = default(MailAccount);   
           a = new MailAccount(sm, "AdventureWorks2012 Administrator", "AdventureWorks2012 Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com");   
           a.Create();    
}  
```  
  
## <a name="creating-a-database-mail-account-by-using-powershell"></a>Создание учетной записи для компонента Database Mail в PowerShell  
 В этом примере кода демонстрируется создание учетной записи электронной почты в объектах SMO. Компонент Database Mail представлен объектом <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>, и на него ссылается свойство <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Server>. Объекты SMO можно использовать для программной настройки компонента Database Mail, но не для отправления или обработки полученной почты.  
  
  
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define the Database Mail; reference it using the Server Mail property.  
$sm = $srv.Mail  
  
#Define and create a mail account by supplying the Database Mail service,  
#name, description, display name, and email address arguments in the constructor.  
$a = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Mail.MailAccount -argumentlist $sm, `  
"Adventure Works Administrator", "Adventure Works Automated Mailer",`  
 "Mail account for administrative e-mail.", "dba@Adventure-Works.com"  
$a.Create()  
```  
  
  
