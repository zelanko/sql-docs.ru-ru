---
title: Azure Active Directory | Документация Майкрософт
ms.date: 02/25/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- azure active directory, authentication, access token
author: david-puglielli
ms.author: v-dapugl
manager: v-mabarw
ms.openlocfilehash: 8712681a244e969d230b0b7099acd4aa56334f11
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265181"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Подключение с использованием проверки подлинности Azure Active Directory
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) — это центральная технология управления ИДЕНТИФИКАТОРами пользователей, которая работает в качестве альтернативы [SQL Server проверки](../../connect/php/how-to-connect-using-sql-server-authentication.md)подлинности. Azure AD разрешает подключения к База данных SQL Microsoft Azure и хранилищу данных SQL с федеративными удостоверениями в Azure AD с помощью имени пользователя и пароля, встроенной проверки подлинности Windows или маркера доступа Azure AD. Драйверы PHP для SQL Server предлагают частичную поддержку этих функций.

Чтобы использовать Azure AD, используйте ключевые слова **authentication** или **AccessToken** (они являются взаимоисключающими), как показано в следующей таблице. Дополнительные технические сведения см. в разделе [использование Azure Active Directory с драйвером ODBC](../../connect/odbc/using-azure-active-directory.md).

|Ключевое слово|Значения|Описание|
|-|-|-|
|**AccessToken**|Не задано (по умолчанию)|Режим проверки подлинности, определенный другими ключевыми словами. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md). |
||Строка байтов|Маркер доступа Azure AD, извлеченный из ответа OAuth JSON. Строка подключения не должна содержать идентификатор пользователя, пароль или ключевое слово проверки подлинности (требуется драйвер ODBC версии 17 или более поздней в Linux или macOS). |
|**Проверка подлинности**|Не задано (по умолчанию)|Режим проверки подлинности, определенный другими ключевыми словами. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|Пройти проверку подлинности напрямую в экземпляре SQL Server (который может быть экземпляром Azure), используя имя пользователя и пароль. Имя пользователя и пароль должны быть переданы в строку подключения с помощью ключевых слов **UID** и **PWD** . |
||`ActiveDirectoryPassword`|Проверка подлинности с помощью удостоверения Azure Active Directory с использованием имени пользователя и пароля. Имя пользователя и пароль должны быть переданы в строку подключения с помощью ключевых слов **UID** и **PWD** . |
||`ActiveDirectoryMsi`|Проверка подлинности с помощью управляемого системой удостоверения или управляемого удостоверения, назначенного пользователем (требуется драйвер ODBC версии 17.3.1.1 или выше). Общие сведения и учебники см. в статье [что такое управляемые удостоверения для ресурсов Azure?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).|

Ключевое слово **authentication** влияет на параметры безопасности подключения. Если оно задано в строке подключения, по умолчанию ключевое слово **Encrypt** имеет значение true, что означает, что клиент запросит шифрование. Кроме того, сертификат сервера будет проверяться независимо от параметра шифрования, если для **TrustServerCertificate** не задано значение true (по умолчанию**false** ). Эта функция отличается от старого, менее безопасного метода входа в систему, при котором сертификат сервера проверяется только в том случае, если шифрование запрашивается в строке подключения.

При использовании Azure AD с драйверами PHP для SQL Server в Windows может быть предложено установить [Помощник по входу в Microsoft Online Services](https://www.microsoft.com/download/details.aspx?id=41950) (не требуется для ODBC 17 +).

#### <a name="limitations"></a>Ограничения

В Windows базовый драйвер ODBC поддерживает еще одно значение для ключевого слова **authentication** , **ActiveDirectoryIntegrated**, но драйверы PHP не поддерживают это значение на любой платформе.

## <a name="example---connect-using-sqlpassword-and-activedirectorypassword"></a>Пример подключения с помощью SqlPassword и ActiveDirectoryPassword

```php
<?php
// First connect to a local SQL Server instance by setting Authentication to SqlPassword
$serverName = "myserver.mydomain";

$connectionInfo = array("UID"=>$myusername, "PWD"=>$mypassword, "Authentication"=>'SqlPassword');

$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Authentication=SqlPassword.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=SqlPassword.\n";
    sqlsrv_close($conn);
}

// Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
$azureServer = "myazureserver.database.windows.net";
$azureDatabase = "myazuredatabase";
$azureUsername = "myuid";
$azurePassword = "mypassword";
$connectionInfo = array("Database"=>$azureDatabase,
                        "UID"=>$azureUsername,
                        "PWD"=>$azurePassword,
                        "Authentication"=>'ActiveDirectoryPassword');

$conn = sqlsrv_connect($azureServer, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
    sqlsrv_close($conn);
}

?>
```

## <a name="example---connect-using-the-pdosqlsrv-driver"></a>Пример. подключение с помощью драйвера PDO_SQLSRV

```php
<?php
// First connect to a local SQL Server instance by setting Authentication to SqlPassword
$serverName = "myserver.mydomain";

$connectionInfo = "Database = $databaseName; Authentication = SqlPassword;";

try {
    $conn = new PDO("sqlsrv:server = $serverName ; $connectionInfo", $myusername, $mypassword);
    echo "Connected successfully with Authentication=SqlPassword.\n";
    $conn = null;
} catch (PDOException $e) {
    echo "Could not connect with Authentication=SqlPassword.\n";
    print_r($e->getMessage());
    echo "\n";
}

// Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
$azureServer = "myazureserver.database.windows.net";
$azureDatabase = "myazuredatabase";
$azureUsername = "myuid";
$azurePassword = "mypassword";
$connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryPassword;";

try {
    $conn = new PDO("sqlsrv:server = $azureServer ; $connectionInfo", $azureUsername, $azurePassword);
    echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="example---connect-using-azure-ad-access-token"></a>Пример. подключение с помощью маркера доступа Azure AD

### <a name="sqlsrv-driver"></a>Драйвер SQLSRV

```php
<?php
// Using an access token to connect: do not use UID or PWD connection options
// Assume $accToken is the valid byte string extracted from an OAuth JSON response
$connectionInfo = array("Database"=>$azureAdDatabase, "AccessToken"=>$accToken);
$conn = sqlsrv_connect($azureAdServer, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Azure AD Access Token.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Azure AD Access Token.\n";
    sqlsrv_close($conn);
}
?>
```

### <a name="pdosqlsrv-driver"></a>Драйвер PDO_SQLSRV

```php
<?php
try {
    // Using an access token to connect: do not pass in $uid or $pwd
    // Assume $accToken is the valid byte string extracted from an OAuth JSON response
    $connectionInfo = "Database = $azureAdDatabase; AccessToken = $accToken;";
    $conn = new PDO("sqlsrv:server = $azureAdServer; $connectionInfo");
    echo "Connected successfully with Azure AD Access Token\n";
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Azure AD Access Token.\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="example---connect-using-managed-identities-for-azure-resources"></a>Пример. подключение с использованием управляемых удостоверений для ресурсов Azure

### <a name="using-the-system-assigned-managed-identity-with-sqlsrv-driver"></a>Использование назначенного системой управляемого удостоверения с драйвером SQLSRV

При подключении с использованием управляемого системой удостоверения не используйте параметры UID или PWD.

```php
<?php

$azureServer = 'myazureserver.database.windows.net';
$azureDatabase = 'myazuredatabase';
$connectionInfo = array('Database'=>$azureDatabase,
                        'Authentication'=>'ActiveDirectoryMsi');
$conn = sqlsrv_connect($azureServer, $connectionInfo);

if ($conn === false) {
    echo "Could not connect with Authentication=ActiveDirectoryMsi (system-assigned).\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=ActiveDirectoryMsi (system-assigned).\n";
    
    $tsql = "SELECT @@Version AS SQL_VERSION";
    $stmt = sqlsrv_query($conn, $tsql);
    if ($stmt === false) {
        echo "Failed to run the simple query (system-assigned).\n";
        print_r(sqlsrv_errors());
    } else {
        while ($row = sqlsrv_fetch_array($stmt, SQLSRV_FETCH_ASSOC)) {
            echo $row['SQL_VERSION'] . PHP_EOL;
        }

        sqlsrv_free_stmt($stmt);
    }
    
    sqlsrv_close($conn);
}
?>
```

### <a name="using-the-user-assigned-managed-identity-with-pdosqlsrv-driver"></a>Использование назначенного пользователем управляемого удостоверения с драйвером PDO_SQLSRV

Назначаемое пользователем управляемое удостоверение создается как автономный ресурс Azure. Azure создает удостоверение в клиенте Azure AD, который является доверенным для используемой подписки. После создания удостоверения удостоверение может быть назначено одному или нескольким экземплярам службы Azure. `Object ID` Скопируйте это удостоверение и задайте его в качестве имени пользователя в строке подключения. 

Поэтому при подключении с помощью управляемого пользователем удостоверения укажите идентификатор объекта в качестве имени пользователя, но не указывайте пароль.

```php
<?php

$azureServer = 'myazureserver.database.windows.net';
$azureDatabase = 'myazuredatabase';
$azureUser = '2d68f56e-9547-4dae-aee8-f3g28ab9674x';    // Object ID of the identity
$connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryMsi;";

try {
    $conn = new PDO("sqlsrv:server = $azureServer; $connectionInfo", $azureUser);
    echo "Connected successfully with Authentication=ActiveDirectoryMsi (user-assigned).\n";
    
    $tsql = "SELECT @@Version AS SQL_VERSION";
    
    try {
        $stmt = $conn->query($tsql);
        $result = $stmt->fetchall(PDO::FETCH_ASSOC);
        print_r($result);

        unset($stmt);
    } catch (PDOException $e) {
        echo "Failed to run the simple query (user-assigned).\n";
    }
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Authentication=ActiveDirectoryMsi (user-assigned).\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="see-also"></a>См. также:
[Использование Azure Active Directory с драйвером ODBC](https://docs.microsoft.com/sql/connect/odbc/using-azure-active-directory)

[Что такое управляемые удостоверения для ресурсов Azure?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview)
