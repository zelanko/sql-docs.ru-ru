---
title: Организация пулов подключений (драйверы Майкрософт для PHP для SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02db1d891f02dce9912d4cdcf78ca0166eab9c32
ms.sourcegitcommit: ef7f2540ba731cc6a648005f2773d759df5c6405
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39415483"
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>Организация пулов соединений (драйверы Майкрософт для PHP для SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ниже перечислены важные замечания об организации пулов соединений в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]:  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] использует организацию пулов соединений ODBC.  
  
-   По умолчанию организация пулов подключений в Windows включена. В Linux и macOS, соединения заносятся в пул только в том случае, если включено использование пулов соединений для ODBC (см. в разделе [организация пулов соединений Включение и отключение](#enablingdisabling-connection-pooling)). Когда включено использование пулов соединений и подключиться к серверу, то драйвер пытается использовать соединение из пула перед созданием нового. Если в пуле нет эквивалентного соединения, создается новое соединение, которое добавляется в пул. Драйвер определяет эквивалентность соединений путем сравнения строк подключения.  
  
-   При использовании соединения из пула выполняется сброс состояния соединения.  
  
-   После закрытия соединение возвращается в пул.  
  
Дополнительные сведения о пуле подключений см. в статье [Driver Manager Connection Pooling](../../odbc/reference/develop-app/driver-manager-connection-pooling.md) (Организация пулов подключений для диспетчера драйверов).  
  
## <a name="enablingdisabling-connection-pooling"></a>Организация пулов соединений Включение и отключение
### <a name="windows"></a>Windows
Можно настроить драйвер на принудительное создание нового подключения (вместо поиска эквивалентного подключения в пуле подключений), задав для атрибута *ConnectionPooling* в строке подключения значение **false** (или 0).  
  
Когда атрибут *ConnectionPooling* отсутствует в строке подключения или имеет значение **true** (или 1), драйвер создает новое подключение, только если в пуле подключений нет эквивалентного подключения.  
  
Сведения о других атрибутах соединения см. в статье [Connection Options](../../connect/php/connection-options.md).  
### <a name="linux-and-macos"></a>Linux и macOS
*ConnectionPooling* атрибут не может использоваться для включения или отключения пула соединений. 

Организация пулов соединений можно включить или отключить, изменив файл odbcinst.ini конфигурации. Чтобы изменения вступили в силу требуется перезагрузка драйвер.

Установка `Pooling` для `Yes` и положительное `CPTimeout` значение в файл odbcinst.ini включает организация пулов соединений. 
```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
CPTimeout=<int value>
```
  
Как минимум файл odbcinst.ini выглядит примерно как в следующем примере:

```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
Description=Microsoft ODBC Driver 13 for SQL Server
Driver=/opt/microsoft/msodbcsql/lib64/libmsodbcsql-13.1.so.3.0
UsageCount=1
CPTimeout=120
```

Установка `Pooling` для `No` в odbcinst.ini файл заставляет драйвер создать новое соединение.
```
[ODBC]
Pooling=No
```

## <a name="remarks"></a>Remarks
- В Linux или macOS все подключения будут помещаться, если использование пула включено в файл odbcinst.ini. Это означает, что параметр подключения ConnectionPooling не влияет. Чтобы отключить группировку, задайте Pooling = нет в файл odbcinst.ini и перезагрузки драйверов.
  - unixODBC < = 2.3.4 (Linux и macOS) могут не возвращать нужные сведения диагностики, такие как сообщения об ошибках, предупреждения и информационные сообщения
  - по этой причине SQLSRV и PDO_SQLSRV драйверы могут быть не удавалось правильно получить данные большой длины (например, xml, двоичное) как строки. Длинных данных можно извлечь как потоки в качестве обходного решения. Дополнительные сведения о SQLSRV см. в приведенном ниже примере.

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
[Практическое руководство. Подключение с использованием проверки подлинности Windows](../../connect/php/how-to-connect-using-windows-authentication.md)

[Практическое руководство. Подключение с использованием проверки подлинности SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  
