---
title: Устойчивость простоя подключения
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: 250e4e6334a31d760c8fcb3e1e571ec1a726d020
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307263"
---
# <a name="idle-connection-resiliency"></a>Устойчивость простоя подключения
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Устойчивость подключения](https://msdn.microsoft.com/library/dn632678.aspx) — принцип, что разорванное соединение простоя можно установить повторно, в рамках определенных ограничений. В случае сбоя подключения к Microsoft SQL Server, устойчивость подключений позволяет клиенту автоматически пытаются восстановить подключение. Устойчивость подключений — это свойство источника данных. только SQL Server 2014 и более поздней версии и базы данных SQL Azure поддерживает устойчивость подключений.

Устойчивость подключений реализуется с помощью два ключевых слова подключения, которые могут быть добавлены в строки подключения: **ConnectRetryCount** и **ConnectRetryInterval**.

|Ключевое слово|Значения|По умолчанию|Описание|
|-|-|-|-|
|**ConnectRetryCount**| Целое число от 0 до 255 (включительно)|1|Максимальное количество попыток восстановить подключение прервано начинал. По умолчанию один попытка восстановить подключение, если нечитаемым. Значение 0 означает попыток без повторного подключения.|
|**ConnectRetryInterval**| Целое число от 1 до 60 (включительно)|1| Время в секундах между попытками создания потерянного подключения. Приложение будет пытаться переподключить немедленно при обнаружении разорванное соединение, а затем будет ожидать **ConnectRetryInterval** секунд перед повторной попыткой. Это ключевое слово учитывается, если **ConnectRetryCount** равно 0.

Если произведение **ConnectRetryCount** умноженное **ConnectRetryInterval** больше, чем **LoginTimeout**, то клиент прекращает попытки подключения один раз  **LoginTimeout** достигается; в противном случае она будет продолжать повторить попытку подключения до **ConnectRetryCount** достигается.

#### <a name="remarks"></a>Примечания

Устойчивость подключения применяется, если соединение находится в состоянии простоя. Сбои, которые могут возникнуть при выполнении транзакции, например, не будет вызывать попыток повторного соединения — произойдет сбой, в противном случае было бы ожидать. Следующие ситуации, известные как состояния сеанса без возможности восстановления, не будет вызывать попыток повторного соединения:

* Временные таблицы
* Глобальные и локальные курсоры
* Контекст транзакции и сеанс уровень блокировки транзакций
* Блокировки приложений
* EXECUTE AS / вернуть контекст безопасности
* Дескрипторы автоматизации OLE
* Подготовленный дескрипторах XML
* Флаги трассировки

## <a name="example"></a>Пример

Следующий код подключается к базе данных и выполняет запрос. Прервано подключение с закрытием сеанса и попытке выполнить новый запрос с помощью разорванное соединение. В этом примере используется [AdventureWorks](https://msdn.microsoft.com/library/ms124501%28v=sql.100%29.aspx) образца базы данных.

В этом примере мы указываем буферизованный курсор перед разрыва соединения. Если мы не указан буфер курсора, соединение будет повторно не так, как бы active серверный курсор и таким образом соединение будет простоя, если нечитаемым. Однако в этом случае мы могли бы вызвать sqlsrv_free_stmt() перед подключение к vacate курсор и соединение будет успешно повторно.

```php
<?php
// This function breaks the connection by determining its session ID and killing it.
// A separate connection is used to break the main connection because a session
// cannot kill itself. The sleep() function ensures enough time has passed for KILL
// to finish ending the session.
function BreakConnection( $conn, $conn_break )
{
    $stmt1 = sqlsrv_query( $conn, "SELECT @@SPID" );
    if ( sqlsrv_fetch( $stmt1 ) )
    {
        $spid=sqlsrv_get_field( $stmt1, 0 );
    }

    $stmt2 = sqlsrv_prepare( $conn_break, "KILL ".$spid );
    sqlsrv_execute( $stmt2 );
    sleep(1);
}

// Connect to the local server using Windows authentication and specify
// AdventureWorks as the database in use. Specify values for
// ConnectRetryCount and ConnectRetryInterval as well.
$databaseName = 'AdventureWorks2014';
$serverName = '(local)';
$connectionInfo = array( "Database"=>$databaseName, "ConnectRetryCount"=>10, "ConnectRetryInterval"=>10 );

$conn = sqlsrv_connect( $serverName, $connectionInfo );
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}

// A separate connection that will be used to break the main connection $conn
$conn_break = sqlsrv_connect( $serverName, array( "Database"=>$databaseName) );

// Create a statement to retrieve the contents of a table
$stmt1 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Employee",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt1 === false )
{
     echo "Error in statement 1.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 1 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt1 );
    echo $rowcount." rows in result set.\n";
}

// Now break the connection $conn
BreakConnection( $conn, $conn_break );

// Create another statement. The connection will be reestablished.
$stmt2 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Department",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt2 === false )
{
     echo "Error in statement 2.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 2 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt2 );
    echo $rowcount." rows in result set.\n";
}

sqlsrv_close( $conn );
sqlsrv_close( $conn_break );
?>
```
Ожидаемый результат:
```
Statement 1 successful.
290 rows in result set.
Statement 2 successful.
16 rows in result set.
```

## <a name="see-also"></a>См. также
[Устойчивость подключения в драйвере ODBC в Windows](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver)
