---
title: Управление пользователями, ролями и имена входа | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ae6c07026bbbc12fc526eca1b5079bcc9cf36782
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030265"
---
# <a name="managing-users-roles-and-logins"></a>Управление пользователями, ролями и именами входа
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  В SMO имена входа представлены объектом <xref:Microsoft.SqlServer.Management.Smo.Login>. Если имя входа существует в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], его можно добавить в роль сервера. Роль сервера представлена объектом <xref:Microsoft.SqlServer.Management.Smo.ServerRole>. Роль базы данных представлена объектом <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole>, а роль приложения представлена объектом <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole>.  
  
 Права доступа уровня сервера перечислены в виде свойств объекта <xref:Microsoft.SqlServer.Management.Smo.ServerPermission>. Права доступа уровня сервера можно предоставлять, запрещать или отзывать для отдельных учетных записей входа.  
  
 У каждого объекта <xref:Microsoft.SqlServer.Management.Smo.Database> есть объект <xref:Microsoft.SqlServer.Management.Smo.UserCollection>, в котором указываются все пользователи базы данных. С каждым пользователем связано имя входа. Одно имя входа может быть связано с пользователями в нескольких базах данных. Метод <xref:Microsoft.SqlServer.Management.Smo.Login> объекта <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> используется для перечисления всех пользователей во всех базах данных, связанных с именем входа. И наоборот, свойство <xref:Microsoft.SqlServer.Management.Smo.User> объекта <xref:Microsoft.SqlServer.Management.Smo.Login> содержит имя входа, связанное с пользователем.  
  
 В базах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] также есть роли, которые определяют набор прав доступа уровня базы данных, позволяющих пользователям выполнять определенные задачи. В отличие от ролей сервера, роли базы данных не являются фиксированными. Их можно создавать, изменять и удалять. Права доступа и пользователей можно назначать роли базы данных для пакетного администрирования.  
  
## <a name="example"></a>Пример  
 В следующих примерах кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в разделе [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a>Перечисление имен входа и связанных пользователей на языке Visual C#  
 Каждый пользователь базы данных связан с именем входа. Имя входа может быть связано с пользователями в нескольких базах данных. В этом примере кода показан вызов метода <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Login> для перечисления всех пользователей базы данных, связанных с именем входа. В примере создается имя входа и пользователь в базе данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] , чтобы обеспечить сведения о сопоставлении для перечисления.  
  
```csharp  
{   
Server srv = new Server();   
//Iterate through each database and display.   
  
foreach ( Database db in srv.Databases) {   
   Console.WriteLine("========");   
   Console.WriteLine("Login Mappings for the database: " + db.Name);   
   Console.WriteLine(" ");   
   //Run the EnumLoginMappings method and return details of database user-login mappings to a DataTable object variable.   
   DataTable d;  
   d = db.EnumLoginMappings();   
   //Display the mapping information.   
   foreach (DataRow r in d.Rows) {   
      foreach (DataColumn c in r.Table.Columns) {   
         Console.WriteLine(c.ColumnName + " = " + r[c]);   
      }   
      Console.WriteLine(" ");   
   }   
}   
}  
```  
  
## <a name="enumerating-logins-and-associated-users-in-powershell"></a>Перечисление имен входа и связанных пользователей в PowerShell  
 Каждый пользователь базы данных связан с именем входа. Имя входа может быть связано с пользователями в нескольких базах данных. В этом примере кода показан вызов метода <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Login> для перечисления всех пользователей базы данных, связанных с именем входа. В примере создается имя входа и пользователь в базе данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] , чтобы обеспечить сведения о сопоставлении для перечисления.  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\Default\Databases  
  
#Iterate through all databases  
 foreach ($db in Get-ChildItem)  
 {  
 "====="  
 "Login Mappings for the database: "+ $db.Name  
  
 #get the datatable containing the mapping from the smo database oject  
 $dt = $db.EnumLoginMappings()  
  
 #display the results  
 foreach($row in $dt.Rows)  
     {  
        foreach($col in $row.Table.Columns)  
      {  
        $col.ColumnName + "=" + $row[$col]  
       }  
  
     }  
 }  
```  
  
## <a name="managing-roles-and-users"></a>Управление ролями и пользователями  
 Этот образец демонстрирует методы управления ролями и пользователями. Для выполнения этого примера необходимы ссылки на следующие сборки:  
  
-   Microsoft.SqlServer.Smo.dll  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
-   Microsoft.SqlServer.ConnectionInfo.dll  
  
-   Microsoft.SqlServer.SqlEnum.dll  
  
```csharp  
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // Creating Logins  
      Login login = new Login(svr, "Login1");  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      Login login2 = new Login(svr, "Login2");  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@1");  
  
      // Creating Users in the database for the logins created  
      User user1 = new User(db, "User1");  
      user1.Login = "Login1";  
      user1.Create();  
  
      User user2 = new User(db, "User2");  
      user2.Login = "Login2";  
      user2.Create();  
  
      // Creating database permission Sets  
      DatabasePermissionSet dbPermSet = new DatabasePermissionSet(DatabasePermission.AlterAnySchema);  
      dbPermSet.Add(DatabasePermission.AlterAnyUser);  
  
      DatabasePermissionSet dbPermSet2 = new DatabasePermissionSet(DatabasePermission.CreateType);  
      dbPermSet2.Add(DatabasePermission.CreateSchema);  
      dbPermSet2.Add(DatabasePermission.CreateTable);  
  
      // Creating Database roles  
      DatabaseRole role1 = new DatabaseRole(db, "Role1");  
      role1.Create();  
  
      DatabaseRole role2 = new DatabaseRole(db, "Role2");  
      role2.Create();  
  
      // Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name);  
      db.Grant(dbPermSet2, role2.Name);  
  
      // Adding members (Users / Roles) to Role  
      role1.AddMember("User1");  
  
      role2.AddMember("User2");  
  
      // Role1 becomes a member of Role2  
      role2.AddMember("Role1");  
  
      // Enumerating through explicit permissions granted to Role1  
      // enumerates all database permissions for the Grantee  
      DatabasePermissionInfo[] dbPermsRole1 = db.EnumDatabasePermissions("Role1");     
      foreach (DatabasePermissionInfo dbp in dbPermsRole1) {  
         Console.WriteLine(dbp.Grantee + " has " + dbp.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
   }  
}  
```
  
  
