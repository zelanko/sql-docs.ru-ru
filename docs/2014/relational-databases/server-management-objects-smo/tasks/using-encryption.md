---
title: Использование шифрования | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- database master key [SMO]
- cryptography [SMO]
- cryptography [SQL Server], SMO
- encryption keys [SMO]
- encryption [SQL Server], SMO
- encryption [SMO]
- certificates [SMO]
- service master key [SMO]
ms.assetid: 405e0ed7-50a9-430e-a343-471f54b4af76
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 233f5bc9decf5e8246f2aba6836ec5ecb650283b
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72781849"
---
# <a name="using-encryption"></a>Использование шифрования
  В SMO главный ключ службы представлен объектом <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey>. На него ссылается свойство <xref:Microsoft.SqlServer.Management.Smo.Server.ServiceMasterKey%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Server>. Его можно сформировать заново с помощью метода <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey.Regenerate%2A>.  
  
 Главный ключ базы данных представлен объектом <xref:Microsoft.SqlServer.Management.Smo.MasterKey>. Свойство <xref:Microsoft.SqlServer.Management.Smo.MasterKey.IsEncryptedByServer%2A> указывает, шифруется ли главный ключ базы данных с помощью главного ключа службы. Зашифрованная копия в базе данных master обновляется автоматически при любом изменении главного ключа базы данных.  
  
 С помощью метода <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> можно отключить шифрование с использованием ключа службы и зашифровать главный ключ базы данных с использованием пароля. В таком случае потребуется явно открыть главный ключ базы данных перед доступом к хранящимся в нем закрытым ключам.  
  
 При подключении базы данных к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо либо предоставить пароль для главного ключа базы данных, либо выполнить метод <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A>, чтобы создать незашифрованную копию главного ключа базы данных, доступную для шифрования с использованием главного ключа службы. Этот шаг рекомендуется, поскольку он позволяет избежать необходимости явно открывать главный ключ базы данных.  
  
 Метод <xref:Microsoft.SqlServer.Management.Smo.MasterKey.Regenerate%2A> используется для повторного создания главного ключа базы данных. При повторном создании главного ключа базы данных все ключи, которые были зашифрованы главным ключом базы данных, расшифровываются, а затем шифруются с использованием нового главного ключа базы данных. Метод <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> используется для удаления шифрования главного ключа базы данных с помощью главного ключа службы. Сущность <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> используется для шифрования копии главного ключа с помощью главного ключа службы и сохраняется как в текущей базе данных, так и в базе данных master.  
  
 В SMO сертификаты представлены объектом <xref:Microsoft.SqlServer.Management.Smo.Certificate>. У объекта <xref:Microsoft.SqlServer.Management.Smo.Certificate> есть свойства, указывающие открытый ключ, имя субъекта, срок действия и сведения об издателе. Разрешение на доступ к сертификату управляется с помощью методов `Grant`, `Revoke` и `Deny`.  
  
## <a name="example"></a>Пример  
 В следующем примере кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в статьях [Создание проекта Visual Basic SMO в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) и [Создание проекта Visual&#35; C SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="adding-a-certificate-in-visual-basic"></a>Добавление сертификата на языке Visual Basic  
 В этом примере кода создается простой сертификат с паролем для шифрования. В отличие от других объектов у метода <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> есть несколько перегруженных методов. Перегруженный метод, используемый в этом примере, создает новый сертификат с паролем для шифрования.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCertificate1](SMO How to#SMO_VBCertificate1)]  -->  
  
## <a name="adding-a-certificate-in-visual-c"></a>Добавление сертификата на языке Visual C#  
 В этом примере кода создается простой сертификат с паролем для шифрования. В отличие от других объектов у метода <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> есть несколько перегруженных методов. Перегруженный метод, используемый в этом примере, создает новый сертификат с паролем для шифрования.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            {  
                Server srv = new Server();  
  
                //Reference the AdventureWorks2012 database.   
                Database db = srv.Databases["AdventureWorks2012"];  
  
                //Define a Certificate object variable by supplying the parent database and name in the constructor.   
                Certificate c = new Certificate(db, "Test_Certificate");  
  
                //Set the start date, expiry date, and description.   
                System.DateTime dt;  
                DateTime.TryParse("January 01, 2010", out dt);  
                c.StartDate = dt;  
                DateTime.TryParse("January 01, 2015", out dt);  
                c.ExpirationDate = dt;  
                c.Subject = "This is a test certificate.";  
                //Create the certificate on the instance of SQL Server by supplying the certificate password argument.   
                c.Create("pGFD4bb925DGvbd2439587y");  
            }  
        }   
```  
  
## <a name="adding-a-certificate-in-powershell"></a>Добавление сертификата в PowerShell  
 В этом примере кода создается простой сертификат с паролем для шифрования. В отличие от других объектов у метода <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> есть несколько перегруженных методов. Перегруженный метод, используемый в этом примере, создает новый сертификат с паролем для шифрования.  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
#Create a certificate
$c = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Certificate -ArgumentList $db, "Test_Certificate"  
$c.StartDate = "January 01, 2010"  
$c.Subject = "This is a test certificate."  
$c.ExpirationDate = "January 01, 2015"  
  
#Create the certificate on the instance of SQL Server by supplying the certificate password argument.  
$c.Create("pGFD4bb925DGvbd2439587y")
```  
  
## <a name="see-also"></a>См. также статью  
 [Использование ключей шифрования](using-encryption.md)  
