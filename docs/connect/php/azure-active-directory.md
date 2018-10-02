---
title: Azure Active Directory | Документация Майкрософт
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: 67f32c2c48188b3bcff50e22ca66bf2f563b1704
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814832"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Подключение с использованием проверки подлинности Azure Active Directory
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) — это технология управления центрального пользовательского идентификатор, который работает как альтернативу [проверку подлинности SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md). Azure AD позволяет подключениями к базе данных SQL Microsoft Azure и хранилище данных SQL с федеративные удостоверения в Azure AD с помощью имени пользователя и пароля, встроенная проверка подлинности Windows или маркер доступа Azure AD; драйверы PHP для SQL Server предлагают частичная поддержка этих функций.

Чтобы использовать Azure AD, используйте **проверки подлинности** ключевое слово. Значения, **проверки подлинности** может занять на описаны в следующей таблице.

|Ключевое слово|Значения|Описание|
|-|-|-|
|**Проверка подлинности**|Не задано (по умолчанию)|Режим проверки подлинности определяется другими ключевыми словами. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|Прямой аутентификации к экземпляру SQL Server (который может быть экземпляром Azure) с помощью имени пользователя и пароля. Имя пользователя и пароль должен быть передан в строке подключения в **UID** и **PWD** ключевые слова. |
||`ActiveDirectoryPassword`|Проверка подлинности с помощью удостоверения Azure Active Directory, используя имя пользователя и пароль. Имя пользователя и пароль должен быть передан в строке подключения в **UID** и **PWD** ключевые слова. |

**Проверки подлинности** ключевое слово влияет на параметры безопасности подключения. Если он задан в строке подключения, а затем по умолчанию **Encrypt** ключевого слова задано значение true, чтобы клиент запрашивает шифрование. Кроме того, сертификат сервера будет проверяться независимо от параметра шифрования, если не **TrustServerCertificate** задано значение true. Этим оно отличается из старого и менее безопасный, метод входа, в котором сертификат сервера не проверяется, если шифрование специально не была запрошена в строке подключения.

Прежде чем использовать Azure AD с драйверами PHP для SQL Server в Windows, убедитесь, что у вас установлена [Microsoft Online Services Sign-In Assistant](https://www.microsoft.com/download/details.aspx?id=41950) (не требуется для Linux и MacOS).

#### <a name="limitations"></a>Ограничения

В Windows, основной драйвер ODBC поддерживает одно значение больше для **проверки подлинности** ключевое слово, **ActiveDirectoryIntegrated**, но драйверами PHP не поддерживают это значение на любой платформе и, следовательно также не поддерживают проверку подлинности на основе маркеров Azure AD.

## <a name="example"></a>Пример

В следующем примере показано, как подключиться с помощью **SqlPassword** и **ActiveDirectoryPassword**.

```php
    <?php
    // First connect to a local SQL Server instance by setting Authentication to SqlPassword
    $serverName = "myserver.mydomain";

    $connectionInfo = array( "UID"=>$myusername, "PWD"=>$mypassword, "Authentication"=>'SqlPassword' );

    $conn = sqlsrv_connect( $serverName, $connectionInfo );
    if( $conn === false )
    {
        echo "Could not connect with Authentication=SqlPassword.\n";
        print_r( sqlsrv_errors() );
    }
    else
    {
        echo "Connected successfully with Authentication=SqlPassword.\n";
        sqlsrv_close( $conn );
    }

    // Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
    $azureServer = "myazureserver.database.windows.net";
    $azureDatabase = "myazuredatabase";
    $azureUsername = "myuid";
    $azurePassword = "mypassword";
    $connectionInfo = array( "Database"=>$azureDatabase, "UID"=>$azureUsername, "PWD"=>$azurePassword,
                             "Authentication"=>'ActiveDirectoryPassword' );

    $conn = sqlsrv_connect( $azureServer, $connectionInfo );
    if( $conn === false )
    {
        echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
        print_r( sqlsrv_errors() );
    }
    else
    {
        echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
        sqlsrv_close( $conn );
    }

    ?>
```

В следующем примере выполняется аналогично описанному выше с помощью драйвера PDO_SQLSRV.

```php
    <?php
    // First connect to a local SQL Server instance by setting Authentication to SqlPassword
    $serverName = "myserver.mydomain";

    $connectionInfo = "Database = $databaseName; Authentication = SqlPassword;";

    try
    {
        $conn = new PDO( "sqlsrv:server = $serverName ; $connectionInfo", $myusername, $mypassword );
        echo "Connected successfully with Authentication=SqlPassword.\n";
        $conn = null;
    }
    catch( PDOException $e )
    {
        echo "Could not connect with Authentication=SqlPassword.\n";
        print_r( $e->getMessage() );
        echo "\n";
    }

    // Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
    $azureServer = "myazureserver.database.windows.net";
    $azureDatabase = "myazuredatabase";
    $azureUsername = "myuid";
    $azurePassword = "mypassword";
    $connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryPassword;";

    try
    {
        $conn = new PDO( "sqlsrv:server = $azureServer ; $connectionInfo", $azureUsername, $azurePassword );
        echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
        $conn = null;
    }
    catch( PDOException $e )
    {
        echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
        print_r( $e->getMessage() );
        echo "\n";
    }

    ?>
```
## <a name="see-also"></a>См. также:  
[Использование Azure Active Directory с драйвером ODBC](https://docs.microsoft.com/sql/connect/odbc/using-azure-active-directory)
