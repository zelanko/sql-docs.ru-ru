---
title: Устойчивость соединения в режиме ожидания
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-mabarw
ms.openlocfilehash: 3edba0cde94d8661eed053319142ce7f84a70613
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265169"
---
# <a name="idle-connection-resiliency"></a>Устойчивость соединения в режиме ожидания
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Устойчивость подключения](../odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) — это принцип, в рамках которого может быть восстановлено неактивное соединение в определенных ограничениях. В случае сбоя подключения к Microsoft SQL Server, устойчивость подключения позволяет клиенту автоматически пытаться восстановить подключение. Устойчивость подключения является свойством источника данных; устойчивость подключений поддерживается только SQL Server 2014 и более поздних версий и базе данных SQL Azure.

Устойчивость подключения реализуется с помощью двух ключевых слов подключения, которые можно добавить в строки подключения: **ConnectRetryCount** и **ConnectRetryInterval**.

|Ключевое слово|Значения|По умолчанию|Описание|
|-|-|-|-|
|**ConnectRetryCount**| Целое число от 0 до 255 (включительно).|1|Максимальное число попыток повторного установления неработающего соединения перед тем, как будет выдаваться. По умолчанию выполняется одна попытка восстановить подключение, если оно разорвано. Значение 0 означает, что повторная связь не будет выполнена.|
|**ConnectRetryInterval**| Целое число от 1 до 60 (включительно).|1| Время в секундах между попытками восстановить соединение. Приложение попытается повторно подключиться сразу после обнаружения неработающего подключения, а затем будет ждать **ConnectRetryInterval** секунд, прежде чем повторять попытку. Это ключевое слово игнорируется, если **ConnectRetryCount** равен 0.

Если продукт **ConnectRetryCount** , умноженный на **ConnectRetryInterval** , больше **LoginTimeOut**, то клиент прекратит попытки подключиться после достижения **LoginTimeOut** . в противном случае он продолжит попытки повторного подключения до тех пор, пока не будет достигнут **ConnectRetryCount** .

#### <a name="remarks"></a>Remarks

Устойчивость подключения применяется, когда соединение бездействует. Ошибки, возникающие при выполнении транзакции, например, не активируют попытки повторного подключения, так как в противном случае они будут завершаться ошибкой. Следующие ситуации, известные как невосстанавливаемые состояния сеанса, не активируют попытки повторного подключения:

* Временные таблицы
* Глобальные и локальные курсоры
* Контекст транзакции и блокировки транзакций на уровне сеанса
* Блокировки приложений
* Контекст безопасности выполнение от имени или откат
* Дескрипторы OLE Automation
* Подготовленные дескрипторы XML
* Флаги трассировки

## <a name="example"></a>Пример

Следующий код подключается к базе данных и выполняет запрос. Соединение прервано из-за разрыва сеанса, и предпринята попыток выполнить новый запрос с использованием разорванного соединения. В примере используется образец базы данных [AdventureWorks](https://msdn.microsoft.com/library/ms124501%28v=sql.100%29.aspx).

В этом примере мы указываем буферизованный курсор перед разрывом соединения. Если не указать буферизованный курсор, соединение не будет восстановлено из-за наличия активного серверного курсора, поэтому соединение не будет бездействующим при нарушении работы. Однако в этом случае мы могли бы вызвать sqlsrv_free_stmt () перед разрывом соединения для освобождения курсора, и соединение было бы успешно восстановлено.

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

## <a name="see-also"></a>См. также:
[Устойчивость подключения в драйвере ODBC в Windows](../odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)
