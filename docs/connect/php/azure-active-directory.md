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
manager: mbarwin
ms.openlocfilehash: 30423cd7c15a920d99fad4c0ea08e074beaece0b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62522797"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Подключение с использованием проверки подлинности Azure Active Directory
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) — это технология управления центрального пользовательского идентификатор, который работает как альтернативу [проверку подлинности SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md). Azure AD позволяет подключениями к базе данных SQL Microsoft Azure и хранилище данных SQL с федеративные удостоверения в Azure AD, используя имя пользователя и пароль, встроенная проверка подлинности Windows или маркер доступа Azure AD. Драйверы PHP для SQL Server предлагают частичная поддержка этих функций.

Чтобы использовать Azure AD, используйте **проверки подлинности** или **AccessToken** ключевые слова (они являются взаимоисключающими), как показано в следующей таблице. Дополнительные технические сведения см. [с помощью Azure Active Directory с помощью драйвера ODBC](../../connect/odbc/using-azure-active-directory.md).

|Ключевое слово|Значения|Описание|
|-|-|-|
|**AccessToken**|Не задано (по умолчанию)|Режим проверки подлинности определяется другими ключевыми словами. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md). |
||Строка байтов|Azure AD маркер доступа, извлеченных из ответа OAuth JSON. Строка подключения не может содержать идентификатор пользователя, пароль или ключевое слово проверки подлинности (требуется драйвер ODBC версии 17 или более поздней версии в Linux или macOS). |
|**Проверка подлинности**|Не задано (по умолчанию)|Режим проверки подлинности определяется другими ключевыми словами. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|Прямой аутентификации к экземпляру SQL Server (который может быть экземпляром Azure) с помощью имени пользователя и пароля. Имя пользователя и пароль должен быть передан в строке подключения в **UID** и **PWD** ключевые слова. |
||`ActiveDirectoryPassword`|Проверка подлинности с помощью удостоверения Azure Active Directory, используя имя пользователя и пароль. Имя пользователя и пароль должен быть передан в строке подключения в **UID** и **PWD** ключевые слова. |
||`ActiveDirectoryMsi`|Проверка подлинности с помощью управляемого удостоверения, назначенный системой или назначаемого пользователем управляемого удостоверения (требуется драйвер ODBC версии 17.3.1.1 или более поздней версии). Обзор и учебники, см. в разделе [что такое управляемые удостоверения для ресурсов Azure?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).|

**Проверки подлинности** ключевое слово влияет на параметры безопасности подключения. Если он задан в строке подключения, а затем по умолчанию **Encrypt** ключевого слова задано значение true, значит, клиент запрашивает шифрование. Кроме того, сертификат сервера будет проверяться независимо от параметра шифрования, если не **TrustServerCertificate** задано значение true (**false** по умолчанию). Эта функция отличается от старой и менее безопасного входа в систему, метод, в котором сертификат сервера проверяется только в том случае, если шифрование поступает конкретное требование в строке подключения.

При использовании Azure AD с драйверами PHP для SQL Server в Windows, может появиться запрос на установку [Microsoft Online Services Sign-In Assistant](https://www.microsoft.com/download/details.aspx?id=41950) (не требуется для ODBC 17 +).

#### <a name="limitations"></a>Ограничения

В Windows, основной драйвер ODBC поддерживает одно значение больше для **проверки подлинности** ключевое слово, **ActiveDirectoryIntegrated**, но драйверами PHP не поддерживают это значение на любой платформе.

## <a name="example---connect-using-sqlpassword-and-activedirectorypassword"></a>Пример - подключение с использованием SqlPassword и ActiveDirectoryPassword

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

## <a name="example---connect-using-the-pdosqlsrv-driver"></a>Пример - подключение с помощью драйвера PDO_SQLSRV

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

## <a name="example---connect-using-azure-ad-access-token"></a>Пример - подключение с использованием маркера доступа Azure AD

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

## <a name="example---connect-using-managed-identities-for-azure-resources"></a>Пример - подключение с помощью управляемых удостоверений для ресурсов Azure

### <a name="using-the-system-assigned-managed-identity-with-sqlsrv-driver"></a>С помощью управляемого удостоверения, назначенный системой с помощью драйвера SQLSRV

При подключении с использованием назначенное системой управляемого удостоверения, не используйте параметры UID и PWD.

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

### <a name="using-the-user-assigned-managed-identity-with-pdosqlsrv-driver"></a>С помощью назначаемого пользователем управляемого удостоверения с помощью драйвера PDO_SQLSRV

Назначаемое пользователем управляемое удостоверение создается как отдельный ресурс Azure. Azure создает удостоверение в клиенте Azure AD, который является доверенным для используемой подписки. После создания удостоверения удостоверения могут назначаться один или несколько экземпляров службы Azure. Копировать `Object ID` данного удостоверение и набор его как пользователь имя в строке подключения. 

Таким образом при подключении с помощью назначаемого пользователем управляемого удостоверения, указать идентификатор объекта в качестве имени пользователя, но не указывать пароль.

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
