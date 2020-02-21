---
title: Руководство. Отправка и извлечение ASCII-данных в Linux и macOS (SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/16/2018
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, ASCII data
- sending data
- linux
- macOS
author: yitam
ms.author: v-yitam
manager: v-mabarw
ms.openlocfilehash: 9edd73f5ef01d1d3f22db78400cc3c204efe1379
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "68251904"
---
# <a name="how-to-send-and-retrieve-ascii-data-in-linux-and-macos"></a>Руководство. отправлять и извлекать ASCII-данные в Linux и macOS 
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья предполагает, что языковые стандарты ASCII (non-UTF-8) были сгенерированы или установлены в системе Linux или MacOS. 

Для отправки или получения наборов символов ASCII на сервер.  

1.  Если желаемый языковой стандарт не установлен по умолчанию в системной среде, убедитесь, что вы вызвали `setlocale(LC_ALL, $locale)` перед первым подключением. Функция PHP setlocale() изменяет языковой стандарт только для текущего скрипта, и если она вызывается после первого соединения, то ее можно проигнорировать.
 
2.  При использовании драйвера SQLSRV `'CharacterSet' => SQLSRV_ENC_CHAR` можно указать в качестве параметра соединения, но этот шаг является необязательным, поскольку это стандартное кодирование.

3.  При использовании драйвера PDO_SQLSRV существует два способа. Сначала, при установлении соединения, укажите для параметра `PDO::SQLSRV_ATTR_ENCODING` значение `PDO::SQLSRV_ENCODING_SYSTEM` (пример установки опции соединения см. в [PDO::__construct](../../connect/php/pdo-construct.md)). В качестве альтернативы, после успешного подключения, добавьте эту строку `$conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);` 
  
Когда вы указываете кодировку ресурса подключения (в SQLSRV) или объекта соединения (PDO_SQLSRV), драйвер делает предположение, что другие строки опции подключения используют ту же самую кодировку. Для строк имени сервера и запроса также предполагается использование той же кодировки.  
  
По умолчанию драйвер PDO_SQLSRV имеет кодировку UTF-8 (PDO::SQLSRV_ENCODING_UTF8), в отличие от драйвера SQLSRV. Дополнительные сведения об этих константах см. в статье [Константы &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md). 
  
## <a name="example"></a>Пример  
Следующие примеры демонстрируют, как отправлять и получать данные ASCII с помощью PHP-драйверов для SQL Server, указав определенный языковой стандарт перед установлением соединения. Языковые стандарты на различных платформах Linux могут называться иначе, чем те же самые языковые стандарты в MacOS. Например, языковой стандарт US ISO-8859-1 (Latin 1) в Linux называется `en_US.ISO-8859-1`, в то время как в macOS — `en_US.ISO8859-1`.
  
В примерах предполагается, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен на сервере. При запуске примеров в браузере все выходные данные выводятся в браузер.  
  
```  
<?php  
  
// SQLSRV Example
//
// Setting locale for the script is only necessary if Latin 1 is not the default 
// in the environment
$locale = strtoupper(PHP_OS) === 'LINUX' ? 'en_US.ISO-8859-1' : 'en_US.ISO8859-1';
setlocale(LC_ALL, $locale);
        
$serverName = 'MyServer';
$database = 'Test';
$connectionInfo = array('Database'=>'Test', 'UID'=>$uid, 'PWD'=>$pwd);
$conn = sqlsrv_connect($serverName, $connectionInfo);
  
if ($conn === false) {
    echo "Could not connect.<br>";  
    die(print_r(sqlsrv_errors(), true));
}  
  
// Set up the Transact-SQL query to create a test table
//   
$stmt = sqlsrv_query($conn, "CREATE TABLE [Table1] ([c1_int] int, [c2_varchar] varchar(512))");

// Insert data using a parameter array 
//
$tsql = "INSERT INTO [Table1] (c1_int, c2_varchar) VALUES (?, ?)";
  
// Execute the query, $value being some ASCII string
//   
$stmt = sqlsrv_query($conn, $tsql, array(1, array($value, SQLSRV_PARAM_IN, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR))));
  
if ($stmt === false) {
    echo "Error in statement execution.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  
else {  
    echo "The insertion was successfully executed.<br>";  
}  
  
// Retrieve the newly inserted data
//   
$stmt = sqlsrv_query($conn, "SELECT * FROM Table1");
$outValue = null;  
if ($stmt === false) {  
    echo "Error in statement execution.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
// Retrieve and display the data
//   
if (sqlsrv_fetch($stmt)) {  
    $outValue = sqlsrv_get_field($stmt, 1, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR));
    echo "Value: " . $outValue . "<br>";
    if ($value !== $outValue) {
        echo "Data retrieved, \'$outValue\', is unexpected!<br>";
    }
}  
else {  
    echo "Error in fetching data.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Free statement and connection resources
//   
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
```
<?php  
  
// PDO_SQLSRV Example:
//
// Setting locale for the script is only necessary if Latin 1 is not the default 
// in the environment
$locale = strtoupper(PHP_OS) === 'LINUX' ? 'en_US.ISO-8859-1' : 'en_US.ISO8859-1';
setlocale(LC_ALL, $locale);
        
$serverName = 'MyServer';
$database = 'Test';

try {
    $conn = new PDO("sqlsrv:Server=$serverName;Database=$database;", $uid, $pwd);
    $conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);
    
    // Set up the Transact-SQL query to create a test table
    //   
    $stmt = $conn->query("CREATE TABLE [Table1] ([c1_int] int, [c2_varchar] varchar(512))");
    
    // Insert data using parameters, $value being some ASCII string
    //
    $stmt = $conn->prepare("INSERT INTO [Table1] (c1_int, c2_varchar) VALUES (:var1, :var2)");
    $stmt->bindValue(1, 1);
    $stmt->bindParam(2, $value);
    $stmt->execute();
    
    // Retrieve and display the data
    //
    $stmt = $conn->query("SELECT * FROM [Table1]");
    $outValue = null;
    if ($row = $stmt->fetch()) {
        $outValue = $row[1];
        echo "Value: " . $outValue . "<br>";
        if ($value !== $outValue) {
            echo "Data retrieved, \'$outValue\', is unexpected!<br>";
        }
    }
} catch (PDOException $e) {
    echo $e->getMessage() . "<br>";
} finally {
    // Free statement and connection resources
    //
    unset($stmt);
    unset($conn);
}

?>  
```  

## <a name="see-also"></a>См. также:  
[Извлечение данных](../../connect/php/retrieving-data.md)  
[How to: Send and Retrieve UTF-8 Data Using Built-In UTF-8 Support](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md) (Практическое руководство. Отправка и извлечение данных UTF-8 с помощью встроенной поддержки UTF-8)
[Обновление данных (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Пример приложения (драйвер SQLSRV)](../../connect/php/example-application-sqlsrv-driver.md)  
  
