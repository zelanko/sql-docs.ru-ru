---
title: Azure Active Directory
description: Узнайте, как использовать проверку подлинности Azure Active Directory с драйверами Майкрософт для PHP для SQL Server.
ms.date: 02/25/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- azure active directory, authentication, access token
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f7abb90d32f93975c9a984670ca450dc791a46ae
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "92004556"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Подключение с использованием проверки подлинности Azure Active Directory
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](/azure/active-directory/active-directory-whatis) (Azure AD) — это центральная технология управления идентификаторами пользователей, которая действует в качестве альтернативы [проверки подлинности SQL Server](how-to-connect-using-sql-server-authentication.md). Azure AD разрешает подключения к Базе данных SQL Microsoft Azure и Azure Synapse Analytics с помощью федеративных удостоверений в Azure AD с использованием имени пользователя и пароля, встроенной проверки подлинности Windows или маркера доступа Azure AD. Драйверы PHP для SQL Server предоставляют частичную поддержку этих функций.

Чтобы использовать Azure AD, используйте ключевые слова **Authentication** или **AccessToken** (они являются взаимоисключающими), как показано в следующей таблице. Дополнительные технические сведения см. в статье [Using Azure Active Directory with the ODBC Driver](../odbc/using-azure-active-directory.md) (Использование Azure Active Directory с драйвером ODBC).

|Ключевое слово|Значения|Описание|
|-|-|-|
|**AccessToken**|Не задано (по умолчанию).|Режим проверки подлинности определяется другими ключевыми словами. Дополнительные сведения см. в статье [Connection Options](connection-options.md). |
||Байтовая строка|Маркер доступа Azure AD, извлеченный из ответа OAuth JSON. Строка подключения не должна содержать идентификатор пользователя, пароль или ключевое слово Authentication (требуется драйвер ODBC версии 17 или более поздней версии в Linux или macOS). |
|**Аутентификация**|Не задано (по умолчанию).|Режим проверки подлинности определяется другими ключевыми словами. Дополнительные сведения см. в статье [Connection Options](connection-options.md). |
||`SqlPassword`|Прямая проверка подлинности в экземпляре SQL Server (может быть экземпляром Azure) по имени пользователя и паролю. Имя пользователя и пароль необходимо передать в строку подключения с использованием ключевых слов **UID** и **PWD**. |
||`ActiveDirectoryPassword`|Проверка подлинности по удостоверению Azure Active Directory с использованием имени пользователя и пароля. Имя пользователя и пароль необходимо передать в строку подключения с использованием ключевых слов **UID** и **PWD**. |
||`ActiveDirectoryMsi`|Проверка подлинности с помощью управляемого удостоверения, назначаемого системой или пользователем (требуется драйвер ODBC версии 17.3.1.1 или более поздней версии). Общие сведения и учебники см. в статье [Что такое управляемые удостоверения для ресурсов Azure?](/azure/active-directory/managed-identities-azure-resources/overview).|

Ключевое слово **Authentication** влияет на параметры безопасности подключения. Если оно задано в строке подключения, по умолчанию для ключевого слова **Encrypt** указано значение true, то есть клиент будет запрашивать шифрование. Кроме того, сертификат сервера будет проверяться независимо от параметра шифрования, если для параметра **TrustServerCertificate** установлено значение true (**false** по умолчанию). Эта функция отличается от старого, менее безопасного метода входа в систему, при котором сертификат сервера проверяется только в том случае, если шифрование запрашивается в строке подключения.

#### <a name="limitations"></a>Ограничения

В Windows базовый драйвер ODBC поддерживает еще одно значение для ключевого слова **Authentication** — **ActiveDirectoryIntegrated**, но драйверы PHP не поддерживают это значение в любой платформе.

## <a name="example---connect-using-sqlpassword-and-activedirectorypassword"></a>Пример: подключение с использованием SqlPassword и ActiveDirectoryPassword

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

## <a name="example---connect-using-the-pdo_sqlsrv-driver"></a>Пример: подключение с использованием драйвера PDO_SQLSRV

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

## <a name="example---connect-using-azure-ad-access-token"></a>Пример: подключение с использованием маркера доступа Azure AD

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

### <a name="pdo_sqlsrv-driver"></a>Драйвер PDO_SQLSRV

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

## <a name="example---connect-using-managed-identities-for-azure-resources"></a>Пример: подключение с использованием управляемых удостоверений для ресурсов Azure

### <a name="using-the-system-assigned-managed-identity-with-sqlsrv-driver"></a>Использование управляемого удостоверения, назначаемого системой, с драйвером SQLSRV

При подключении с использованием управляемого удостоверения, назначаемого системой, не указывайте параметры UID или PWD.

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

### <a name="using-the-user-assigned-managed-identity-with-pdo_sqlsrv-driver"></a>Использование управляемого удостоверения, назначаемого пользователем, с драйвером PDO_SQLSRV

Назначаемое пользователем управляемое удостоверение создается как изолированный ресурс Azure. Azure создает удостоверение в доверенном клиенте Azure AD используемой подписки. После создания удостоверения оно может быть назначено одному или нескольким экземплярам служб Azure. Скопируйте `Object ID` этого удостоверения и укажите его в качестве имени пользователя в строке подключения. 

Поэтому при подключении с помощью управляемого удостоверения, назначаемого пользователем, укажите идентификатор объекта в качестве имени пользователя, но не указывайте пароль.

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
[Использование Azure Active Directory с драйвером ODBC](../odbc/using-azure-active-directory.md)

[Что такое управляемые удостоверения для ресурсов Azure?](/azure/active-directory/managed-identities-azure-resources/overview)