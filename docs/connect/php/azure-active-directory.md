---
title: Azure Active Directory | Документы Microsoft
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.suite: sql
ms.custom: ''
ms.technology:
- drivers
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: e3f50ffe5aca4c620c756ed862187b8817dd6ae0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connect-using-azure-active-directory-authentication"></a>Подключение с использованием проверки подлинности Azure Active Directory
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-whatis) (Azure AD) — это технология управления идентификатор центра пользователь, работающий в качестве альтернативы [проверки подлинности SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md). Azure AD разрешает подключения к базе данных SQL Microsoft Azure и хранилище данных SQL с федеративные удостоверения в Azure AD с помощью имени пользователя и пароля, встроенная проверка подлинности Windows или маркера доступа Azure AD; драйверы PHP для SQL Server обеспечивают частичная поддержка этих возможностей.

Чтобы использовать Azure AD, используйте **проверки подлинности** ключевое слово. Значения, **проверки подлинности** может занять на приведены в следующей таблице.

|Ключевое слово|Значения|Описание|
|-|-|-|
|**Проверка подлинности**|Не задан (по умолчанию)|Режим проверки подлинности определяется другие ключевые слова. Дополнительные сведения см. в статье [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|Непосредственно проверку подлинности в экземпляр SQL Server (который может быть экземпляр Azure) с помощью имени пользователя и пароля. Имя пользователя и пароль должен быть передан в строку соединения с помощью **UID** и **PWD** ключевые слова. |
||`ActiveDirectoryPassword`|Проверка подлинности с помощью удостоверения Azure Active Directory, используя имя пользователя и пароль. Имя пользователя и пароль должен быть передан в строку соединения с помощью **UID** и **PWD** ключевые слова. |

**Проверки подлинности** ключевое слово влияет параметров безопасности подключения. Если значение задано в строке подключения, а затем по умолчанию **Encrypt** ключевого слова задано значение true, поэтому клиент запрашивает шифрование. Кроме того, сертификат сервера будет проверяться независимо от того, параметры шифрования, если не **TrustServerCertificate** задано значение true. Этим оно отличается от старого и менее надежна, метод входа, в котором сертификат сервера не проверяется без шифрования особого запроса в строке подключения.

Прежде чем использовать Azure AD с помощью драйверов PHP для SQL Server в Windows, убедитесь, что вы установили [Microsoft Online Services помощник по входу](https://www.microsoft.com/download/details.aspx?id=41950) (не требуется для Linux и MacOS).

#### <a name="limitations"></a>Ограничения

В Windows, основной драйвер ODBC поддерживает один дополнительные значения для **проверки подлинности** ключевое слово, **ActiveDirectoryIntegrated**, драйверы PHP не поддерживают это значение на любой платформе, но и поэтому также не поддерживает проверку подлинности на основе токена Azure AD.

## <a name="example"></a>Пример

Приведенный ниже показано, как подключаться с помощью **SqlPassword** и **ActiveDirectoryPassword**.

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
## <a name="see-also"></a>См. также  
[Использование Azure Active Directory с драйвером ODBC](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory)
