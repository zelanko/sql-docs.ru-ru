---
description: Использование компонента Database Mail
title: Использование Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 43a49f3ec79b75aeef6fe4282a2933616af723ae
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420178"
---
# <a name="using-database-mail"></a>Использование компонента Database Mail
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  В SMO подсистема компонента Database Mail представлена объектом <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>, на который ссылается свойство <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A>. С помощью объекта SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> можно настраивать подсистему компонента Database Mail и управлять профилями и учетными записями почты. Объект SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> принадлежит объекту **Server** , что означает, что область действия учетных записей почты находится на уровне сервера.  
  
## <a name="examples"></a>Примеры  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. [в статье Создание проекта Visual C&#35; SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
 В программах, в которых используется компонент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Database Mail, необходимо включать инструкцию **Imports** для определения пространства имен Mail. Вставьте инструкцию после других инструкций **Imports** и перед любыми декларациями в приложении.  
  
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
  
  
