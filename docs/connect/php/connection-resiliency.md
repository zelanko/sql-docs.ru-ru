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
manager: v-hakaka
ms.openlocfilehash: a2361c8a2e8cbc709d50a9139678a08e2e850e2d
ms.sourcegitcommit: 7d4a3fc0f2622cbc6930d792be4a9b3fcac4c4b6
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2019
ms.locfileid: "58305922"
---
# <a name="idle-connection-resiliency"></a>Устойчивость соединения в режиме ожидания
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Устойчивость подключения](../odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) — принцип, что разорванное соединение простоя будет переустановлена, в рамках определенных ограничений. В случае сбоя подключения к Microsoft SQL Server, устойчивость подключения позволяет клиентскому компьютеру автоматически пытаются восстановить подключение. Устойчивость подключений — это свойство источника данных. только SQL Server 2014 и более поздней версии и базы данных SQL Azure поддерживает устойчивость подключений.

Устойчивость подключений реализуется с помощью двух ключевых слов подключения, которые могут быть добавлены строки подключения: **ConnectRetryCount** и **ConnectRetryInterval**.

|Ключевое слово|Значения|По умолчанию|Описание|
|-|-|-|-|
|**ConnectRetryCount**| Целое число от 0 до 255 (включительно)|1|Максимальное количество попыток восстановления прерванного разорванное соединение перед прекращением. По умолчанию единый предпринимается попытка восстановить подключение, если нечитаемым. Значение 0 означает, что будет выполняться без повторного подключения.|
|**ConnectRetryInterval**| Целое число от 1 до 60 (включительно)|1| Время в секундах между попытками создания потерянного подключения. Приложение будет пытаться сразу же повторно подключиться при обнаружении разорванное соединение и затем ожидает **ConnectRetryInterval** секунд перед повторной попыткой. Это ключевое слово учитывается, если **ConnectRetryCount** равно 0.

Если произведение **ConnectRetryCount** умноженное **ConnectRetryInterval** больше, чем **LoginTimeout**, то клиент прекращает попытки подключения один раз  **LoginTimeout** достигнут; в противном случае она будет продолжать повторите попытку подключения до **ConnectRetryCount** достижения.

#### <a name="remarks"></a>Remarks

Устойчивость подключения применяется, если подключение бездействует. Сбои, возникающие во время выполнения транзакции, например, не вызовет попытки повторного подключения — они не удастся как в противном случае было бы ожидать. Следующие ситуации, известные как состояния без возможности восстановления сеанса, не сможет запустить попытки повторного подключения:

* Временные таблицы
* Глобальные и локальные курсоры
* Контекст транзакции и сеанс уровень блокировки транзакций
* Блокировки приложений
* EXECUTE AS / вернуть контекст безопасности
* Дескрипторы автоматизации OLE
* Подготовленный дескрипторах XML
* Флаги трассировки

## <a name="example"></a>Пример

Следующий код подключается к базе данных и выполняет запрос. Прервано подключение с закрытием сеанса и выполнить новый запрос с помощью разорванное соединение. В примере используется образец базы данных [AdventureWorks](https://msdn.microsoft.com/library/ms124501%28v=sql.100%29.aspx).

В этом примере мы указываем буферизованных курсора до следующей соединения. Если буферизованных курсор не был указан, соединение будет заново не так, как бы активного серверного курсора, и таким образом подключение не будет устанавливаться простоя, если нечитаемым. Тем не менее в этом случае мы могли бы вызвать sqlsrv_free_stmt() до следующей vacate курсор соединение и соединение может быть успешно повторно установил.

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
