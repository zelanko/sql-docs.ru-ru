---
title: 'Практическое: отправка и получение ASCII-данных в Linux и macOS (SQL) | Документация Майкрософт'
ms.custom: ''
ms.date: 01/16/2018
ms.prod: sql
ms.prod_service: connectivity
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, ASCII data
- sending data
- linux
- macOS
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.openlocfilehash: 32599ca0facc7a35877f6d59573b27209ce68d31
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979826"
---
# <a name="how-to-send-and-retrieve-ascii-data-in-linux-and-macos"></a>Практическое руководство. Отправка и получение ASCII-данных в Linux и macOS 
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В этой статье предполагается, что языковые стандарты ASCII (отличные от UTF-8) были создан или установлен в системах Linux или macOS. 

Отправка и извлечение наборов символов ASCII, к серверу:  

1.  Если нужного языкового стандарта не по умолчанию в системной среде, убедитесь, что вы вызываете `setlocale(LC_ALL, $locale)` перед установкой первого подключения. Функция setlocale() PHP изменяет языковой стандарт только для текущего скрипта, и если вызван после первого подключения, оно может игнорироваться.
 
2.  При использовании драйвера SQLSRV, можно указать `'CharacterSet' => SQLSRV_ENC_CHAR` как подключение параметр, но этот шаг является необязательным, поскольку он используется по умолчанию кодировки.

3.  При использовании драйвера PDO_SQLSRV, двумя способами. Во-первых, при установке соединения, задайте `PDO::SQLSRV_ATTR_ENCODING` для `PDO::SQLSRV_ENCODING_SYSTEM` (пример установки параметра подключения, см. в разделе [PDO::__construct](../../connect/php/pdo-construct.md)). Кроме того после успешного подключения, добавьте следующую строку `$conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);` 
  
При указании кодировки ресурс подключения (в SQLSRV) или объект соединения (PDO_SQLSRV), драйвер предполагает, что другие строки параметров соединения использовать эту же кодировку. Для строк имени сервера и запроса также предполагается использование той же кодировки.  
  
Для драйвера PDO_SQLSRV кодировку по умолчанию используется UTF-8 (PDO::SQLSRV_ENCODING_UTF8), в отличие от драйвера SQLSRV. Дополнительные сведения об этих константах см. в статье [Константы &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md). 
  
## <a name="example"></a>Пример  
Следующие примеры демонстрируют, как отправлять и получать данные в формате ASCII с помощью драйверов PHP для SQL Server, указав перед подключением конкретного языкового стандарта. Национальные настройки в различных платформах Linux из языковых стандартов в macOS может называться по-разному. Например, языковой стандарт нам ISO-8859-1 (Latin 1) является `en_US.ISO-8859-1` в Linux, хотя в macOS имеет имя `en_US.ISO8859-1`.
  
В примерах предполагается, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] устанавливается на сервере. При запуске примеров в браузере все выходные данные выводятся в браузер.  
  
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
[Работа с данными UTF-8](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)
[обновление данных &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Пример приложения (драйвер SQLSRV)](../../connect/php/example-application-sqlsrv-driver.md)  
  
