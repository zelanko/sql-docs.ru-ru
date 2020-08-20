---
description: Использование синонимов
title: Использование синонимов | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7fef9446721928315268db66d46af6ed3a4138c1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464956"
---
# <a name="using-synonyms"></a>Использование синонимов
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Синоним — это альтернативное имя, которое дается объекту в области схемы. В SMO синонимы представлены объектом <xref:Microsoft.SqlServer.Management.Smo.Synonym>. Объект <xref:Microsoft.SqlServer.Management.Smo.Synonym> является дочерним для объекта <xref:Microsoft.SqlServer.Management.Smo.Database>. Это означает, что синонимы действительны только в пределах базы данных, в которой они определены. Однако синоним может относиться к объектам другой базы данных или к удаленному экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Объект, которому дано альтернативное имя, известен как базовый объект. Свойство имени объекта <xref:Microsoft.SqlServer.Management.Smo.Synonym> служит альтернативным именем базового объекта.  
  
## <a name="example"></a>Пример  
 В следующих примерах кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. [в статье Создание проекта Visual C&#35; SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [CREATE SYNONYM (Transact-SQL)](../../../t-sql/statements/create-synonym-transact-sql.md)  
  
  
