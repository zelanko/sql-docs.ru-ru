---
title: 'Как: подключение с использованием проверки подлинности Windows | Документы Microsoft'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, Windows Authentication
ms.assetid: f403a4e0-b0a8-4939-9dc1-e1209626367e
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8a1e43874edbdf5cc3ece40a141f3b32b7fe121e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-connect-using-windows-authentication"></a>Практическое руководство. Подключение с использованием проверки подлинности Windows
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

По умолчанию [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] использует для подключения к серверу проверку подлинности Windows. Важно отметить, что в большинстве случаев это означает, что удостоверение процесса веб-сервера или удостоверение потока (если веб-сервер использует олицетворение) используется для подключения к серверу, а не удостоверение конечного пользователя.  
  
При использовании проверки подлинности Windows для подключения к SQL Server необходимо учитывать следующие аспекты.  
  
-   Для установки соединения учетные данные, с которыми выполняется процесс (или поток) веб-сервера, должны соответствовать допустимому имени входа SQL Server.  
  
-   Если SQL Server и веб-сервер находятся на разных компьютерах, необходимо настроить SQL Server для поддержки удаленных подключений.  
  
> [!NOTE]  
> Атрибуты соединения, такие как *Database* и *ConnectionPooling* , можно задать при установке соединения. Полный список поддерживаемых атрибутов соединения см. в статье [Connection Options](../../connect/php/connection-options.md).  
  
Для подключения к SQL Server следует по возможности использовать проверку подлинности Windows по следующим причинам.  
  
-   Во время проверки подлинности по сети не передаются никакие учетные данные; имена пользователей и пароли не внедряются в строку подключения базы данных. Это означает, что злоумышленники или пользователи-злоумышленники не смогут получить учетные данные путем мониторинга сети или просмотра строк подключения в файлах конфигурации.  
  
-   На пользователей распространяется централизованное управление учетными записями, применяются политики безопасности, касающиеся, например, сроков действия паролей, минимальной длины паролей и блокировки учетных записей после нескольких неудачных запросов на вход.  
  
Если использование проверки подлинности Windows не является целесообразным, см. статью [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md).  
  
## <a name="example"></a>Пример  
Благодаря драйверу SQLSRV [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]следующий пример использует проверку подлинности Windows для подключения к локальному экземпляру SQL Server. После установки соединения на сервер отправляет запрос имени входа пользователя, осуществляющего доступ к базе данных.  
  
Предполагается, что SQL Server и [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) базы данных установлены на локальном компьютере. При выполнении примера в браузере все выходные данные выводятся в браузер.  
  
```  
<?php  
/* Specify the server and connection string attributes. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
  
/* Connect using Windows Authentication. */  
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
Следующий пример использует драйвер PDO_SQLSRV для выполнения той же задачи, что и в предыдущем примере.  
  
```  
<?php  
try {  
   $conn = new PDO( "sqlsrv:Server=(local);Database=AdventureWorks", NULL, NULL);   
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
?>  
```  
  
## <a name="see-also"></a>См. также  
[Практическое руководство. Подключение с использованием проверки подлинности SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)

[Руководство по программированию для драйвера Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)

[Как: создать имя входа SQL Server](../../relational-databases/security/authentication-access/create-a-login.md)

[Как: Создание пользователя базы данных](../../relational-databases/security/authentication-access/create-a-database-user.md)

[Управление пользователями, ролями и именами входа](../../relational-databases/server-management-objects-smo/tasks/managing-users-roles-and-logins.md)

[Отделение пользователей от схем](../../relational-databases/server-management-objects-smo/tasks/managing-users-roles-and-logins.md)

[Разрешения объекта GRANT (Transact-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  
