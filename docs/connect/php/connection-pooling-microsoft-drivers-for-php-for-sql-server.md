---
title: Организация пулов соединений (драйверы Майкрософт для PHP для SQL Server)
description: Сведения о создании пулов подключений при использовании драйверов Майкрософт для PHP для SQL Server и о том, как они могут отличаться в зависимости от операционной системы.
ms.custom: ''
ms.date: 08/01/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 147e744a69850a5c76b9706c03a96fa67d2efb5f
ms.sourcegitcommit: 129f8574eba201eb6ade1f1620c6b80dfe63b331
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2020
ms.locfileid: "87435262"
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>Организация пулов соединений (драйверы Майкрософт для PHP для SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ниже перечислены важные замечания об организации пулов соединений в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]:  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] использует организацию пулов соединений ODBC.  
  
-   По умолчанию организация пулов подключений в Windows включена. В Linux и MacOS подключения объединяются в пулы только в том случае, если для ODBC включено группировку подключений (см. раздел [Включение и отключение группировки подключений](#enablingdisabling-connection-pooling) этой статьи). Если группировку подключений включено и вы подключаетесь к серверу, драйвер пытается использовать соединение из пула перед созданием нового. Если в пуле нет эквивалентного соединения, создается новое соединение, которое добавляется в пул. Драйвер определяет эквивалентность соединений путем сравнения строк подключения.  
  
-   При использовании соединения из пула выполняется сброс состояния соединения (только Windows).  
  
-   После закрытия соединение возвращается в пул.  
  
Дополнительные сведения о пуле подключений см. в статье [Driver Manager Connection Pooling](../../odbc/reference/develop-app/driver-manager-connection-pooling.md) (Организация пулов подключений для диспетчера драйверов).  
  
## <a name="enablingdisabling-connection-pooling"></a>Включение и отключение группировки подключений
### <a name="windows"></a>Windows
Можно настроить драйвер на принудительное создание нового подключения (вместо поиска эквивалентного подключения в пуле подключений), задав для атрибута *ConnectionPooling* в строке подключения значение **false** (или 0).  
  
Когда атрибут *ConnectionPooling* отсутствует в строке подключения или имеет значение **true** (или 1), драйвер создает новое подключение, только если в пуле подключений нет эквивалентного подключения.  

> [!NOTE]  
> По умолчанию множественные активные результирующие наборы (MARS) включены. При использовании MARS и пулов для правильной работы MARS драйверу требуется более длительное время для сброса соединения на *первом* запросе, таким образом, игнорируя указанное время ожидания запроса. Тем не менее, параметр времени ожидания запроса активируется в последующих запросах.
  
При необходимости ознакомьтесь с документом [Практическое руководство, как отключить множественные активные результирующие наборы (функция MARS)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md). Сведения о других атрибутах соединения см. в статье [Connection Options](../../connect/php/connection-options.md).  

### <a name="linux-and-macos"></a>Linux и macOS
Атрибут *ConnectionPooling* нельзя использовать для включения или отключения группировки подключений. 

Группировку подключений можно включить или отключить, изменив файл конфигурации odbcinst.ini. Чтобы изменения вступили в силу, необходимо перезагрузить драйвер.

Если для параметра `Pooling` задано значение `Yes`, положительное значение `CPTimeout` в файле odbcinst.ini включает использование группировки подключений. 
```
[ODBC]
Pooling=Yes

[ODBC Driver 17 for SQL Server]
CPTimeout=<int value>
```
  
Как минимум файл odbcinst.ini должен выглядеть примерно так, как показано в следующем примере:

```
[ODBC]
Pooling=Yes

[ODBC Driver 17 for SQL Server]
Description=Microsoft ODBC Driver 17 for SQL Server
Driver=/opt/microsoft/msodbcsql17/lib64/libmsodbcsql-17.5.so.2.1
UsageCount=1
CPTimeout=120
```

Установка `Pooling` в `No` в файле odbcinst.ini заставляет драйвер создать новое соединение.
```
[ODBC]
Pooling=No
```

## <a name="remarks"></a>Remarks
- В Linux или macOS не рекомендуется использовать пулы соединений с unixODBC ниже версии 2.3.7. Если в файле odbcinst.ini включен пул, то все подключения будут помещены в пул, что означает, что параметр подключения ConnectionPooling не действует. Чтобы отключить группировку, установите Pooling=No в файле odbcinst.ini и перезагрузите драйверы. 
  - unixODBC < = 2.3.4 (Linux и macOS) может не возвращать правильную диагностическую информацию, например сообщения об ошибках, предупреждения и информативные сообщения.
  - По этой причине драйверы SQLSRV и PDO_SQLSRV могут не иметь правильной выборки данных типа long (например, XML, двоичные) в виде строк. В качестве обходного пути можно получить данные типа long в виде потоков. Дополнительные сведения о SQLSRV см. в приведенном ниже примере.

```
<?php
$connectionInfo = array("Database"=>"test", "UID"=>"username", "PWD"=>"password");

$conn1 = sqlsrv_connect("servername", $connectionInfo);

$longSample = str_repeat("a", 8500);
$xml1 = 
'<ParentXMLTag>
  <ChildTag01>'.$longSample.'</ChildTag01>
</ParentXMLTag>';

// Create table and insert xml string into it
sqlsrv_query($conn1, "CREATE TABLE xml_table (field xml)");
sqlsrv_query($conn1, "INSERT into xml_table values ('$xml1')");

// retrieve the inserted xml
$column1 = getColumn($conn1);

// return the connection to the pool
sqlsrv_close($conn1);

// This connection is from the pool
$conn2 = sqlsrv_connect("servername", $connectionInfo);
$column2 = getColumn($conn2);

sqlsrv_query($conn2, "DROP TABLE xml_table");
sqlsrv_close($conn2);

function getColumn($conn)
{
    $tsql = "SELECT * from xml_table";
    $stmt = sqlsrv_query($conn, $tsql);
    sqlsrv_fetch($stmt);
    // This might fail in Linux and macOS
    // $column = sqlsrv_get_field($stmt, 0, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR));
    // The workaround is to fetch it as a stream
    $column = sqlsrv_get_field($stmt, 0, SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_CHAR));
    sqlsrv_free_stmt($stmt);
    return ($column);
}
?>
```


## <a name="see-also"></a>См. также:  
[Руководство. Подключение с помощью проверки подлинности Windows](../../connect/php/how-to-connect-using-windows-authentication.md)

[Руководство. Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md) (Как установить подключение с использованием проверки подлинности SQL Server)  
  
