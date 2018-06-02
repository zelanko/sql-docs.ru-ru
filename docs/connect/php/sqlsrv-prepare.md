---
title: sqlsrv_prepare | Документы Microsoft
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_prepare
apitype: NA
helpviewer_keywords:
- executing queries
- API Reference, sqlsrv_prepare
- sqlsrv_prepare
ms.assetid: 8c74c697-3296-4f5d-8fb9-e361f53f19a6
caps.latest.revision: 52
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d05dadf16e96589c2f16b7d31580cab61650b9e6
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34563922"
---
# <a name="sqlsrvprepare"></a>sqlsrv_prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Создает ресурс инструкции, связанный с указанным соединением. Эта функция удобна для выполнения нескольких запросов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_prepare(resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>Параметры  
*$conn*: ресурс подключения, связанный с созданной инструкцией.  
  
*$tsql*: выражение Transact-SQL, соответствующее созданной инструкции.  
  
*$params* [необязательно]: **массива** значений, которые соответствуют параметрам в параметризованном запросе. Каждый элемент массива может быть одним из следующих значений:
  
-   Буквенное значение.  
  
-   Ссылка на переменную PHP.  
  
-   **Массив** со следующей структурой:  
  
    ```  
    array(&$value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    > [!NOTE]  
    > Переменные, передаваемые в виде параметров запроса, должны передаваться по ссылке, а не по значению. Например, передайте `&$myVariable` вместо `$myVariable`. При выполнении запроса с параметрами по значению, возникает предупреждение PHP.  
  
    Эти элементы массива описаны в следующей таблице:  
  
    |Элемент|Описание|  
    |-----------|---------------|  
    |*&$value*|Буквенное значение или ссылка на переменную PHP.|  
    |*$direction*[необязательно]|Одно из следующих **SQLSRV_PARAM_\***  константы, используемые для указания направления параметра: **SQLSRV_PARAM_IN**, **SQLSRV_PARAM_OUT**, **SQLSRV_PARAM_INOUT**. Значение по умолчанию — **SQLSRV_PARAM_IN**.<br /><br />Дополнительные сведения о константах PHP см. в разделе [константы &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*[необязательно]|Объект **SQLSRV_PHPTYPE_\***  константа, указывающая тип данных PHP для возвращаемого значения.|  
    |*$sqlType*[необязательно]|Объект **SQLSRV_SQLTYPE_\***  константа, указывающая тип данных SQL Server для входного значения.|  
  
*$options* [необязательно]: ассоциативный массив, который задает свойства запроса. В следующей таблице перечислены поддерживаемые ключи и соответствующие значения:  
  
|Key|Поддерживаемые значения|Описание|  
|-------|--------------------|---------------|  
|QueryTimeout|Положительное целое значение.|Задает время ожидания выполнения запроса в секундах. По умолчанию драйвер ожидает бесконечно результаты.|  
|SendStreamParamsAtExec|**true** или **false**<br /><br />Значение по умолчанию — **true**|Настраивает драйвер на отправку всех потоковых данных во время выполнения (**true**), или для отправки потоковых данных в виде блоков (**false**). По умолчанию устанавливается значение **true**. Дополнительные сведения см. в статье [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md).|  
|Прокручиваемые курсоры|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|Дополнительные сведения об этих значениях см. в статье [Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).|  
  
## <a name="return-value"></a>Возвращаемое значение  
Ресурс инструкции. Если не удается создать ресурс инструкции, возвращается значение **false** .  
  
## <a name="remarks"></a>Примечания  
При подготовке инструкции, которая использует переменные в качестве параметров, эти переменные привязываются к инструкции. Это означает, что в случае обновления значений переменных при следующем выполнении инструкции она будет использовать обновленные значения параметров.  
  
Сочетание **sqlsrv_prepare** и **sqlsrv_execute** разделяет подготовку и выполнение инструкции между двумя вызовами функции и может использоваться для выполнения параметризованных запросов. Эта функция оптимально подходит для многократного выполнения инструкции с различными значениями параметров для каждого выполнения.  
  
Об альтернативных стратегиях для записи и чтения больших объемов информации см. в разделе [пакеты инструкций SQL](../../odbc/reference/develop-app/batches-of-sql-statements.md) и [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
Дополнительные сведения см. в статье [How to: Retrieve Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a>Пример  
Следующий пример подготавливает и выполняет инструкцию. При выполнении инструкция (см. [sqlsrv_execute](../../connect/php/sqlsrv-execute.md)), обновляется поле в *Sales.SalesOrderDetail* таблицы базы данных AdventureWorks. Предполагается, что SQL Server и [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) базы данных установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  
/* Set up Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ?   
         WHERE SalesOrderDetailID = ?";  
  
/* Assign parameter values. */  
$param1 = 5;  
$param2 = 10;  
$params = array(&$param1, &$param2);  
  
/* Prepare the statement. */  
if ($stmt = sqlsrv_prepare($conn, $tsql, $params)) {
    echo "Statement prepared.\n";  
} else {  
    echo "Statement could not be prepared.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Execute the statement. */  
if (sqlsrv_execute($stmt)) {  
    echo "Statement executed.\n";  
} else {  
    echo "Statement could not be executed.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="example"></a>Пример  
Следующий пример показывает, как подготовить инструкцию и затем повторно выполнить ее с другими значениями параметров. Пример обновляет столбец *OrderQty* в таблице *Sales.SalesOrderDetail* базы данных AdventureWorks. После завершения обновлений в базу данных направляется запрос, чтобы убедиться, что обновления выполнены успешно. Предполагается, что SQL Server и [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) базы данных установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  
/* Define the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail  
         SET OrderQty = ?  
         WHERE SalesOrderDetailID = ?";  
  
/* Initialize parameters and prepare the statement. Variables $qty  
and $id are bound to the statement, $stmt1. */  
$qty = 0; $id = 0;  
$stmt1 = sqlsrv_prepare($conn, $tsql, array(&$qty, &$id));  
if ($stmt1) {  
    echo "Statement 1 prepared.\n";  
} else {  
    echo "Error in statement preparation.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the SalesOrderDetailID and OrderQty information. This array  
maps the order ID to order quantity in key=>value pairs. */  
$orders = array(1=>10, 2=>20, 3=>30);  
  
/* Execute the statement for each order. */  
foreach ($orders as $id => $qty) {  
    // Because $id and $qty are bound to $stmt1, their updated  
    // values are used with each execution of the statement.   
    if (sqlsrv_execute($stmt1) === false) {  
        echo "Error in statement execution.\n";  
        die(print_r(sqlsrv_errors(), true));  
    }  
}  
echo "Orders updated.\n";  
  
/* Free $stmt1 resources.  This allows $id and $qty to be bound to a different statement.*/  
sqlsrv_free_stmt($stmt1);  
  
/* Now verify that the results were successfully written by selecting   
the newly inserted rows. */  
$tsql = "SELECT OrderQty   
         FROM Sales.SalesOrderDetail   
         WHERE SalesOrderDetailID = ?";  
  
/* Prepare the statement. Variable $id is bound to $stmt2. */  
$stmt2 = sqlsrv_prepare($conn, $tsql, array(&$id));  
if ($stmt2) {  
    echo "Statement 2 prepared.\n";  
} else {  
    echo "Error in statement preparation.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Execute the statement for each order. */  
foreach (array_keys($orders) as $id)  
{  
    /* Because $id is bound to $stmt2, its updated value   
    is used with each execution of the statement. */  
    if (sqlsrv_execute($stmt2)) {  
        sqlsrv_fetch($stmt2);  
        $quantity = sqlsrv_get_field($stmt2, 0);  
        echo "Order $id is for $quantity units.\n";  
    } else {  
        echo "Error in statement execution.\n";  
        die(print_r(sqlsrv_errors(), true));  
    }  
}  
  
/* Free $stmt2 and connection resources. */  
sqlsrv_free_stmt($stmt2);  
sqlsrv_close($conn);  
?>  
```  
  
> [!NOTE]
> Рекомендуется использовать строки в качестве входных данных при привязке значения [столбца decimal или numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) для обеспечения точности и точность как PHP имеет ограниченную точность для [чисел с плавающей запятой](http://php.net/manual/en/language.types.float.php). То же самое происходит со столбцами bigint, особенно при вне диапазона значений [целое](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

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
$stmt = sqlsrv_prepare($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);
sqlsrv_execute($stmt);

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```

## <a name="see-also"></a>См. также  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Практическое руководство. Выполнение параметризованных запросов](../../connect/php/how-to-perform-parameterized-queries.md)

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)

[Практическое руководство. Отправка данных в виде потока](../../connect/php/how-to-send-data-as-a-stream.md)

[Использование параметров направления](../../connect/php/using-directional-parameters.md)

[Извлечение данных](../../connect/php/retrieving-data.md)

[Обновление данных (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

