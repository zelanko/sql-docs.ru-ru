---
title: sqlsrv_query | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_query
apitype: NA
helpviewer_keywords:
- sqlsrv_query
- executing queries
- API Reference, sqlsrv_query
ms.assetid: 9fa7c4c8-4da8-4299-9893-f61815055aa3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 19d7f4d6562f64061f01bf0ff7a73fcd03a4f63c
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606254"
---
# <a name="sqlsrvquery"></a>sqlsrv_query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Подготавливает и выполняет инструкцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_query(resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>Параметры  
*$conn*: ресурс подключения, связанный с подготовленной инструкцией.  
  
*$tsql*: выражение Transact-SQL, соответствующее подготовленной инструкции.  
  
*$params* (необязательно): **массив** значений, которые соответствуют параметрам в параметризованном запросе. Каждый элемент массива может быть одним из следующих значений:
  
-   Буквенное значение.  
  
-   Переменная PHP.  
  
-   **Массив** со следующей структурой:  
  
    ```  
    array($value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    Описание для каждого элемента массива приводится в следующей таблице:  
  
    |Элемент|Описание|  
    |-----------|---------------|  
    |*$value*|Буквенное значение, переменная PHP или ссылочная переменная PHP.|  
    |*$direction*[необязательно]|Одна из следующих констант **SQLSRV_PARAM_\***, используемая для указания направления параметра: **SQLSRV_PARAM_IN**, **SQLSRV_PARAM_OUT**, **SQLSRV_PARAM_INOUT**. Значение по умолчанию — **SQLSRV_PARAM_IN**.<br /><br />Дополнительные сведения о константах PHP см. в статье [Константы &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*[необязательно]|Константа **SQLSRV_PHPTYPE_\***, указывающая тип данных PHP для возвращаемого значения.<br /><br />Дополнительные сведения о константах PHP см. в статье [Константы &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$sqlType*[необязательно]|Константа **SQLSRV_SQLTYPE_\***, указывающая тип данных SQL Server для входного значения.<br /><br />Дополнительные сведения о константах PHP см. в статье [Константы &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
  
*$options* (НЕОБЯЗАТЕЛЬНО): ассоциативный массив, который задает свойства запроса. Поддерживаются следующие ключи:  
  
|Key|Поддерживаемые значения|Описание|  
|-------|--------------------|---------------|  
|QueryTimeout|Положительное целое значение.|Задает время ожидания выполнения запроса в секундах. По умолчанию драйвер ожидает результаты бесконечно.|  
|SendStreamParamsAtExec|**true** или **false**<br /><br />Значение по умолчанию — **true**|Настраивает драйвер для отправки всех потоковых данных во время выполнения (**true**) или отправки потоковых данных в виде блоков (**false**). По умолчанию устанавливается значение **true**. Дополнительные сведения см. в статье [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md).|  
|Прокручиваемые курсоры|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|Дополнительные сведения об этих значениях см. в статье [Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).|  
  
## <a name="return-value"></a>Возвращаемое значение  
Ресурс инструкции. Если не удается создать или выполнить инструкцию, возвращается значение **false**.  
  
## <a name="remarks"></a>Remarks  
Функция **sqlsrv_query** хорошо подходит для одноразовых запросов и должна использоваться по умолчанию для выполнения запросов, если только не действуют особые обстоятельства. Эта функция предоставляет оптимальный метод для выполнения запроса с использованием минимального количества кода. Функция **sqlsrv_query** подготавливает и выполняет инструкцию, а также может применяться для выполнения параметризованных запросов.  
  
Дополнительные сведения см. в статье [How to: Retrieve Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a>Пример  
В следующем примере отдельная строка вставляется в таблицу *Sales.SalesOrderDetail* базы данных AdventureWorks. В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
> [!NOTE]  
> Хотя в следующем примере используется инструкция INSERT, чтобы продемонстрировать использование **sqlsrv_query** для однократного выполнения инструкции, эта концепция распространяется на любую инструкцию Transact-SQL.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "INSERT INTO Sales.SalesOrderDetail   
        (SalesOrderID,   
         OrderQty,   
         ProductID,   
         SpecialOfferID,   
         UnitPrice,   
         UnitPriceDiscount)  
        VALUES   
        (?, ?, ?, ?, ?, ?)";  
  
/* Set parameter values. */  
$params = array(75123, 5, 741, 1, 818.70, 0.00);  
  
/* Prepare and execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if ($stmt) {  
    echo "Row successfully inserted.\n";  
} else {  
    echo "Row insertion failed.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="example"></a>Пример  
В приведенном ниже примере обновляется поле в таблице *Sales.SalesOrderDetail* базы данных AdventureWorks. В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = (?)   
         WHERE SalesOrderDetailID = (?)";  
  
/* Assign literal parameter values. */  
$params = array(5, 10);  
  
/* Execute the query. */  
if (sqlsrv_query($conn, $tsql, $params)) {  
    echo "Statement executed.\n";  
} else {  
    echo "Error in statement execution.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close($conn);  
?>  
```  
  
> [!NOTE]
> Рекомендуется использовать строки в качестве входных данных при привязке значения [столбца decimal или numeric](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) чтобы обеспечить точность и правильность, как PHP имеет ограниченную точность для [чисел с плавающей запятой](https://php.net/manual/en/language.types.float.php). То же применимо к столбцами bigint, особенно в том случае, если значения вне диапазона [целое число](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

## <a name="example"></a>Пример  
В этом примере кода показано, как привязать десятичное значение в качестве входного параметра.  

```
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
     echo "Could not connect.\n";  
     die(print_r(sqlsrv_errors(), true));  
}  

// Assume TestTable exists with a decimal field 
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_query($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```

## <a name="example"></a>Пример
В этом примере кода показано, как создать таблицу [sql_variant](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql) типов и получения вставляемых данных.

```
<?php
$server = 'serverName';
$dbName = 'databaseName';
$uid = 'yourUserName';
$pwd = 'yourPassword';

$options = array("Database"=>$dbName, "UID"=>$uid, "PWD"=>$pwd);
$conn = sqlsrv_connect($server, $options);
if($conn === false) {
    die(print_r(sqlsrv_errors(), true));
}

$tableName = 'testTable';
$query = "CREATE TABLE $tableName ([c1_int] sql_variant, [c2_varchar] sql_variant)";

$stmt = sqlsrv_query($conn, $query);
if($stmt === false) {
    die(print_r(sqlsrv_errors(), true));
}
sqlsrv_free_stmt($stmt);

$query = "INSERT INTO [$tableName] (c1_int, c2_varchar) VALUES (1, 'test_data')";
$stmt = sqlsrv_query($conn, $query);
if($stmt === false) {
    die(print_r(sqlsrv_errors(), true));
}
sqlsrv_free_stmt($stmt);

$query = "SELECT * FROM $tableName";
$stmt = sqlsrv_query($conn, $query);

if(sqlsrv_fetch($stmt) === false) {
    die(print_r(sqlsrv_errors(), true));
}

$col1 = sqlsrv_get_field($stmt, 0);
echo "First field:  $col1 \n";

$col2 = sqlsrv_get_field($stmt, 1);
echo "Second field:  $col2 \n";

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

?>
```

Ожидаемый результат будет следующим:

```
First field:  1
Second field:  test_data
```

## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Практическое руководство. Выполнение параметризованных запросов](../../connect/php/how-to-perform-parameterized-queries.md)  

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  

[Практическое руководство. Отправка данных в виде потока](../../connect/php/how-to-send-data-as-a-stream.md)  

[Использование параметров направления](../../connect/php/using-directional-parameters.md)  

  
