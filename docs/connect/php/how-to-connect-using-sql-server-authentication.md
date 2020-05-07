---
title: Руководство. подключиться с использованием проверки подлинности SQL Server
description: Узнайте об особенностях подключения к базе данных с применением проверки подлинности SQL Server.
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, SQL Server Authentication
ms.assetid: 8d298830-3186-47e7-aef6-586b457901c1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55f87063904a0201b9aa1a98cdb296d27c821083
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81728328"
---
# <a name="how-to-connect-using-sql-server-authentication"></a>Руководство. подключиться с использованием проверки подлинности SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддерживает проверку подлинности SQL Server при подключении к SQL Server.  
  
Проверку подлинности SQL Server следует использовать только в том случае, если невозможно реализовать проверку подлинности Windows. Сведения о подключении с использованием проверки подлинности Windows см. в руководстве[ Подключение с помощью проверки подлинности Windows](../../connect/php/how-to-connect-using-windows-authentication.md).  
  
При использовании проверки подлинности SQL Server для подключения к SQL Server необходимо учитывать следующие аспекты.  
  
-   На сервере должен быть включен смешанный режим проверки подлинности SQL Server.  
  
-   Идентификатор пользователя и пароль (атрибуты подключения *UID* и *PWD* в драйвере SQLSRV) должны быть установлены, когда предпринимается попытка соединения. Идентификатор пользователя и пароль необходимо сопоставить с допустимым пользователем и паролем SQL Server.  
  
> [!NOTE]  
> Пароли, которые содержат закрывающую фигурную скобку (}), необходимо экранировать с помощью второй закрывающей фигурной скобки. Например, если пароль SQL Server имеет значение "па}роль", для атрибута соединения *PWD* следует задать значение "па}}роль".  
  
При использовании проверки подлинности SQL Server для подключения к SQL Server необходимо принять следующие меры предосторожности.  
  
-   Защитите (зашифруйте) учетные данные, передаваемые по сети с веб-сервера в базу данных. Начиная с SQL Server 2005, учетные данные шифруются по умолчанию. Чтобы повысить уровень безопасности, присвойте атрибуту соединения Encrypt значение "on" для шифрования всех данных, отправляемых на сервер.  
  
> [!NOTE]  
> Присвоение атрибуту соединения Encrypt значения "on" может привести к снижению производительности, поскольку для шифрования данных может требоваться большой объем вычислений.  
  
-   Не указывайте значения для атрибутов соединения *UID* и *PWD* в виде открытого текста в скриптах PHP. Эти значения должны храниться в каталоге для конкретного приложения с соответствующими ограниченными разрешениями.  
  
-   Избегайте использования учетной записи *sa* . Сопоставьте приложение с пользователем базы данных, обладающим необходимыми привилегиями, и используйте надежный пароль.  
  
> [!NOTE]  
> Атрибуты соединения, кроме идентификатора пользователя и пароля, можно задать при установке соединения. Полный список поддерживаемых атрибутов соединения см. в статье [Connection Options](../../connect/php/connection-options.md).  
  
## <a name="example"></a>Пример  
Следующий пример использует драйвер SQLSRV с проверкой подлинности SQL Server для подключения к локальному экземпляру SQL Server. Значения для необходимых атрибутов подключения *UID* и *PWD* берутся из текстовых файлов для конкретного приложения (*uid.txt* и *pwd.txt*), находящихся в каталоге *C:\AppData*. После установки соединения на сервер отправляется запрос для проверки имени входа пользователя.  
  
В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера в браузере все выходные данные выводятся в браузер.  
  
```  
<?php  
/* Specify the server and connection string attributes. */  
$serverName = "(local)";  
  
/* Get UID and PWD from application-specific files.  */  
$uid = file_get_contents("C:\AppData\uid.txt");  
$pwd = file_get_contents("C:\AppData\pwd.txt");  
$connectionInfo = array( "UID"=>$uid,  
                         "PWD"=>$pwd,  
                         "Database"=>"AdventureWorks");  
  
/* Connect using SQL Server Authentication. */  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Unable to connect.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Query SQL Server for the login of the user accessing the  
database. */  
$tsql = "SELECT CONVERT(varchar(32), SUSER_SNAME())";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in executing query.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the results of the query. */  
$row = sqlsrv_fetch_array($stmt);  
echo "User login: ".$row[0]."</br>";  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Пример  
Этот пример использует драйвер PDO_SQLSRV для демонстрации подключения с помощью проверки подлинности SQL Server.  
  
```  
<?php  
   $serverName = "(local)";   
   $database = "AdventureWorks";  
  
   // Get UID and PWD from application-specific files.   
   $uid = file_get_contents("C:\AppData\uid.txt");  
   $pwd = file_get_contents("C:\AppData\pwd.txt");  
  
   try {  
      $conn = new PDO( "sqlsrv:server=$serverName;Database = $database", $uid, $pwd);   
      $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );   
   }  
  
   catch( PDOException $e ) {  
      die( "Error connecting to SQL Server" );   
   }  
  
   echo "Connected to SQL Server\n";  
  
   $query = 'select * from Person.ContactType';   
   $stmt = $conn->query( $query );   
   while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){   
      print_r( $row );   
   }  
  
   // Free statement and connection resources.   
   $stmt = null;   
   $conn = null;   
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Руководство. Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md) (Как установить подключение с использованием проверки подлинности SQL Server)

[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)

[SUSER_SNAME (Transact-SQL)](../../t-sql/functions/suser-sname-transact-sql.md)

[Руководство. Создание имени входа SQL Server](../../relational-databases/security/authentication-access/create-a-login.md)

[Руководство. Создание пользователя базы данных](../../relational-databases/security/authentication-access/create-a-database-user.md)

[Управление пользователями, ролями и именами входа](../../relational-databases/server-management-objects-smo/tasks/managing-users-roles-and-logins.md)

[Отделение пользователей от схем](../../relational-databases/server-management-objects-smo/tasks/managing-users-roles-and-logins.md)

[Предоставление разрешений для объекта (Transact-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  
