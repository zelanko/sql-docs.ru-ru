---
title: Использование синонимов | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
caps.latest.revision: 49
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: f1d5af23cdfc6ae45bd8ef70fbd11585c9602302
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561634"
---
# <a name="using-synonyms"></a>Использование синонимов
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Синоним — это альтернативное имя, которое дается объекту в области схемы. В SMO синонимы представлены <xref:Microsoft.SqlServer.Management.Smo.Synonym> объекта. Объект <xref:Microsoft.SqlServer.Management.Smo.Synonym> является дочерним для объекта <xref:Microsoft.SqlServer.Management.Smo.Database>. Это означает, что синонимы действительны только в пределах базы данных, в которой они определены. Однако синоним может относиться к объектам на другую базу данных или на удаленном экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Объект, которому дано альтернативное имя, известен как базовый объект. Свойство имени объекта <xref:Microsoft.SqlServer.Management.Smo.Synonym> служит альтернативным именем базового объекта.  
  
## <a name="example"></a>Пример  
 В следующих примерах кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в разделе [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-synonym-in-visual-c"></a>Создание синонима на языке Visual C#  
 Этот пример кода показывает, как создать синоним или альтернативное имя для объекта из области схемы. Клиентские приложения для ссылки на базовый объект могут использовать одну ссылку на него через синоним вместо использования имени, состоящего из нескольких частей.  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Synonym object variable by supplying the   
            //parent database, name, and schema arguments in the constructor.   
            //The name is also a synonym of the name of the base object.   
            Synonym syn = new Synonym(db, "Shop", "Sales");  
  
            //Specify the base object, which is the object on which   
            //the synonym is based.   
            syn.BaseDatabase = "AdventureWorks2012";  
            syn.BaseSchema = "Sales";  
            syn.BaseObject = "Store";  
            syn.BaseServer = srv.Name;  
  
            //Create the synonym on the instance of SQL Server.   
            syn.Create();  
        }  
```  
  
## <a name="creating-a-synonym-in-powershell"></a>Создание синонима в PowerShell  
 Этот пример кода показывает, как создать синоним или альтернативное имя для объекта из области схемы. Клиентские приложения для ссылки на базовый объект могут использовать одну ссылку на него через синоним вместо использования имени, состоящего из нескольких частей.  
  
```powershell  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#And the database object corresponding to Adventureworks  
$db = $srv.Databases["AdventureWorks2012"]  
  
$syn = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Synonym `  
-argumentlist $db, "Shop", "Sales"  
  
#Specify the base object, which is the object on which the synonym is based.  
$syn.BaseDatabase = "AdventureWorks2012"  
$syn.BaseSchema = "Sales"  
$syn.BaseObject = "Store"  
$syn.BaseServer = $srv.Name  
  
#Create the synonym on the instance of SQL Server.  
$syn.Create()  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE SYNONYM (Transact-SQL)](../../../t-sql/statements/create-synonym-transact-sql.md)  
  
  
