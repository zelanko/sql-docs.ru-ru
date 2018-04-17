---
title: С помощью шифрования | Документы Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9badeac31829eeb8b4558eae4b8aeb7f4afe11ca
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-encryption"></a>Использование шифрования
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  В SMO главный ключ службы, представленного <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey> объекта. Это ссылается <xref:Microsoft.SqlServer.Management.Smo.Server.ServiceMasterKey%2A> свойство <xref:Microsoft.SqlServer.Management.Smo.Server> объекта. Его можно сформировать заново с помощью <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey.Regenerate%2A> метод.  
  
 Главный ключ базы данных представлена <xref:Microsoft.SqlServer.Management.Smo.MasterKey> объекта. <xref:Microsoft.SqlServer.Management.Smo.MasterKey.IsEncryptedByServer%2A> Свойство указывает, зашифрован ли главный ключ базы данных с помощью главного ключа службы. Зашифрованная копия в базе данных master обновляется автоматически при любом изменении главного ключа базы данных.  
  
 Можно удалить службы с помощью ключа шифрования <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> метод и зашифровать главный ключ базы данных с паролем. В таком случае потребуется явно открыть главный ключ базы данных перед доступом к хранящимся в нем закрытым ключам.  
  
 При присоединении базы данных к экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], необходимо указать пароль для главного ключа базы данных или выполнения <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> метод, чтобы сделать доступными для шифрования со службой незашифрованную копию главного ключа базы данных главный ключ. Этот шаг рекомендуется, поскольку он позволяет избежать необходимости явно открывать главный ключ базы данных.  
  
 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.Regenerate%2A> Метод повторно создает главный ключ базы данных. При повторном создании главного ключа базы данных все ключи, которые были зашифрованы главным ключом базы данных, расшифровываются, а затем шифруются с использованием нового главного ключа базы данных. <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> Используется для удаления шифрования главного ключа базы данных с помощью главного ключа службы. Сущность <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> используется для шифрования копии главного ключа с помощью главного ключа службы и сохраняется как в текущей базе данных, так и в базе данных master.  
  
 В SMO сертификаты представлены <xref:Microsoft.SqlServer.Management.Smo.Certificate> объекта. <xref:Microsoft.SqlServer.Management.Smo.Certificate> Объект имеет свойства, которые определяют открытый ключ, имя субъекта, срок действия и сведения об издателе. Разрешение на доступ к сертификату управляется с помощью методов **Grant**, **Revoke** и **Deny** .  
  
## <a name="example"></a>Пример  
 В следующих примерах кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в разделе [создать Visual C&#35; проекта SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="adding-a-certificate-in-visual-c"></a>Добавление сертификата на языке Visual C#  
 В этом примере кода создается простой сертификат с паролем для шифрования. В отличие от других объектов <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> метода есть несколько перегрузок. Перегруженный метод, используемый в этом примере, создает новый сертификат с паролем для шифрования.  
  
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
 В этом примере кода создается простой сертификат с паролем для шифрования. В отличие от других объектов <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> метода есть несколько перегрузок. Перегруженный метод, используемый в этом примере, создает новый сертификат с паролем для шифрования.  
  
```powershell  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
#Create a certificate  
  
$c = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Certificate -argumentlist $db, "Test_Certificate"  
$c.StartDate = "January 01, 2010"  
$c.Subject = "This is a test certificate."  
$c.ExpirationDate = "January 01, 2015"  
  
#Create the certificate on the instance of SQL Server by supplying the certificate password argument.  
$c.Create("pGFD4bb925DGvbd2439587y")  
  
```  
  
## <a name="see-also"></a>См. также  
 [С помощью ключей шифрования](../../../relational-databases/server-management-objects-smo/tasks/using-encryption.md)  
  
  
