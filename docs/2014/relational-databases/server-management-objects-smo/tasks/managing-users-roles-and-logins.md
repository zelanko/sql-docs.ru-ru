---
title: Управление пользователями, ролями и имена входа | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 9bac188dcc6eb26c1bca77ec292a096f4eac2f35
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52815206"
---
# <a name="managing-users-roles-and-logins"></a>Управление пользователями, ролями и именами входа
  В SMO имена входа представлены объектом <xref:Microsoft.SqlServer.Management.Smo.Login>. Если имя входа существует в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], его можно добавить в роль сервера. Роль сервера представлена объектом <xref:Microsoft.SqlServer.Management.Smo.ServerRole>. Роль базы данных представлена объектом <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole>, а роль приложения представлена объектом <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole>.  
  
 Права доступа уровня сервера перечислены в виде свойств объекта <xref:Microsoft.SqlServer.Management.Smo.ServerPermission>. Права доступа уровня сервера можно предоставлять, запрещать или отзывать для отдельных учетных записей входа.  
  
 У каждого объекта <xref:Microsoft.SqlServer.Management.Smo.Database> есть объект <xref:Microsoft.SqlServer.Management.Smo.UserCollection>, в котором указываются все пользователи базы данных. С каждым пользователем связано имя входа. Одно имя входа может быть связано с пользователями в нескольких базах данных. Метод <xref:Microsoft.SqlServer.Management.Smo.Login> объекта <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> используется для перечисления всех пользователей во всех базах данных, связанных с именем входа. И наоборот, свойство <xref:Microsoft.SqlServer.Management.Smo.User> объекта <xref:Microsoft.SqlServer.Management.Smo.Login> содержит имя входа, связанное с пользователем.  
  
 В базах данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] также есть роли, которые определяют набор прав доступа уровня базы данных, позволяющих пользователям выполнять определенные задачи. В отличие от ролей сервера, роли базы данных не являются фиксированными. Их можно создавать, изменять и удалять. Права доступа и пользователей можно назначать роли базы данных для пакетного администрирования.  
  
## <a name="example"></a>Пример  
 В следующем примере кода для создания приложения необходимо выбрать среду программирования, шаблон программирования и язык программирования. Дополнительные сведения см. в разделе [Создание проекта SMO на Visual Basic в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) и [Visual C создайте&#35; проекта SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="enumerating-logins-and-associated-users-in-visual-basic"></a>Перечисление имен входа и связанных пользователей на языке Visual Basic  
 Каждый пользователь базы данных связан с именем входа. Имя входа может быть связано с пользователями в нескольких базах данных. В этом примере кода показан вызов метода <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Login> для перечисления всех пользователей базы данных, связанных с именем входа. В примере создается имя входа и пользователь в базе данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] , чтобы обеспечить сведения о сопоставлении для перечисления.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLogins1](SMO How to#SMO_VBLogins1)]  -->  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a>Перечисление имен входа и связанных пользователей на языке Visual C#  
 Каждый пользователь базы данных связан с именем входа. Имя входа может быть связано с пользователями в нескольких базах данных. В этом примере кода показан вызов метода <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Login> для перечисления всех пользователей базы данных, связанных с именем входа. В примере создается имя входа и пользователь в базе данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] , чтобы обеспечить сведения о сопоставлении для перечисления.  
  
```  
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
  
```  
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
 Этот образец демонстрирует методы управления ролями и пользователями. В первом образце используется язык C#, во втором — Visual Basic. В образцы необходимо включить ссылки на следующие сборки:  
  
-   Microsoft.SqlServer.Smo.dll  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
-   Microsoft.SqlServer.ConnectionInfo.dll  
  
-   Microsoft.SqlServer.SqlEnum.dll  
  
```  
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
  
 Далее приведена версия этого образца на языке Visual Basic:  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
  
Public Class A  
   Public Shared Sub Main()  
      Dim svr As New Server()  
      Dim db As New Database(svr, "TESTDB")  
      db.Create()  
  
      ' Creating Logins  
      Dim login As New Login(svr, "Login1")  
      login.LoginType = LoginType.SqlLogin  
      login.Create("password@1")  
  
      Dim login2 As New Login(svr, "Login2")  
      login2.LoginType = LoginType.SqlLogin  
      login2.Create("password@1")  
  
      ' Creating Users in the database for the logins created  
      Dim user1 As New User(db, "User1")  
      user1.Login = "Login1"  
      user1.Create()  
  
      Dim user2 As New User(db, "User2")  
      user2.Login = "Login2"  
      user2.Create()  
  
      ' Creating database permission Sets  
      Dim dbPermSet As New DatabasePermissionSet(DatabasePermission.AlterAnySchema)  
      dbPermSet.Add(DatabasePermission.AlterAnyUser)  
  
      Dim dbPermSet2 As New DatabasePermissionSet(DatabasePermission.CreateType)  
      dbPermSet2.Add(DatabasePermission.CreateSchema)  
      dbPermSet2.Add(DatabasePermission.CreateTable)  
  
      ' Creating Database roles  
      Dim role1 As New DatabaseRole(db, "Role1")  
      role1.Create()  
  
      Dim role2 As New DatabaseRole(db, "Role2")  
      role2.Create()  
  
      ' Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name)  
      db.Grant(dbPermSet2, role2.Name)  
  
      ' Adding members (Users / Roles) to Role  
      role1.AddMember("User1")  
  
      role2.AddMember("User2")  
  
      ' Role1 becomes a member of Role2  
      role2.AddMember("Role1")  
  
      ' Enumerating through explicit permissions granted to Role1  
      ' enumerates all database permissions for the Grantee  
      Dim dbPermsRole1 As DatabasePermissionInfo() = db.EnumDatabasePermissions("Role1")  
      For Each dbp As DatabasePermissionInfo In dbPermsRole1  
         Console.WriteLine(dbp.Grantee + " has " & dbp.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine(" ")  
   End Sub  
End Class  
```  
  
  
