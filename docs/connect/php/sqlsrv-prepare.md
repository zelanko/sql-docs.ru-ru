---
title: sqlsrv_prepare | Документация Майкрософт
ms.custom: ''
ms.date: 04/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_prepare
apitype: NA
helpviewer_keywords:
- executing queries
- API Reference, sqlsrv_prepare
- sqlsrv_prepare
ms.assetid: 8c74c697-3296-4f5d-8fb9-e361f53f19a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef36e929b44517a6e4688346d72923a0a2f897ca
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925498"
---
# <a name="sqlsrv_prepare"></a>sqlsrv_prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Создает ресурс инструкции, связанный с указанным соединением. Эта функция удобна для выполнения нескольких запросов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_prepare(resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>Параметры  
*$conn*: ресурс подключения, связанный с созданной инструкцией.  
  
*$tsql*: выражение Transact-SQL, соответствующее созданной инструкции.  
  
*$params* (необязательно): **массив** значений, которые соответствуют параметрам в параметризованном запросе. Каждый элемент массива может быть одним из следующих значений:
  
-   Буквенное значение.  
  
-   Ссылка на переменную PHP.  
  
-   **Массив** со следующей структурой:  
  
    ```  
    array(&$value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    > [!NOTE]  
    > Переменные, передаваемые в виде параметров запроса, должны передаваться по ссылке, а не по значению. Например, передайте `&$myVariable` вместо `$myVariable`. При выполнении запроса с параметрами по значению выдается предупреждение PHP.  
  
    Эти элементы массива описаны в следующей таблице:  
  
    |Элемент|Description|  
    |-----------|---------------|  
    |*&$value*|Буквенное значение или ссылка на переменную PHP.|  
    |*$direction*(необязательно)|Одна из следующих констант **SQLSRV_PARAM_\*** , используемая для указания направления параметра: **SQLSRV_PARAM_IN**, **SQLSRV_PARAM_OUT**, **SQLSRV_PARAM_INOUT**. Значение по умолчанию — **SQLSRV_PARAM_IN**.<br /><br />Дополнительные сведения о константах PHP см. в статье [Константы &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*(необязательно)|Константа **SQLSRV_PHPTYPE_\*** , указывающая тип данных PHP для возвращаемого значения.|  
    |*$sqlType*(необязательно)|Константа **SQLSRV_SQLTYPE_\*** , указывающая тип данных SQL Server для входного значения.|  
  
*$options* (необязательно): ассоциативный массив, который задает <a name="properties">свойства запроса</a>. В приведенной ниже таблице содержится перечень поддерживаемых ключей и соответствующих значений.

|Клавиши|Поддерживаемые значения|Description|  
|-------|--------------------|---------------|  
|ClientBufferMaxKBSize|Положительное целое число|Задает размер буфера, который содержит результирующий набор для клиентского курсора.<br /><br />Значение по умолчанию — 10 240 КБ. Дополнительные сведения см. в статье [Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).|
|DecimalPlaces|Целое число от 0 до 4 (включительно)|Указывает число десятичных знаков при форматировании полученных денежных значений.<br /><br />Любое отрицательное целое число или значение больше 4 будет игнорироваться.<br /><br />Этот параметр работает, только если параметру FormatDecimals установлено значение **true**.|
|FormatDecimals|**true** или **false**<br /><br />Значение по умолчанию — **false**.|Указывает, следует ли добавлять начальные нули к десятичным строкам, когда это применимо, и включает параметр `DecimalPlaces` для форматирования денежных типов.<br /><br />Дополнительные сведения см. в статье [Форматирование десятичных строк и денежных значений (драйвер SQLSRV)](../../connect/php/formatting-decimals-sqlsrv-driver.md).|
|QueryTimeout|Положительное целое число|Задает время ожидания выполнения запроса в секундах. По умолчанию драйвер ожидает результаты бесконечно.|  
|ReturnDatesAsStrings|**true** или **false**<br /><br />Значение по умолчанию — **false**.|Настраивает оператор для получения типов даты и времени в виде строк (**true**). Дополнительные сведения см. в [практическом руководстве по получению типов даты и времени в виде строк с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).
|Прокручиваемые курсоры|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|Дополнительные сведения об этих значениях см. в статье [Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).|  
|SendStreamParamsAtExec|**true** или **false**<br /><br />Значение по умолчанию — **true**|Настраивает драйвер для отправки всех потоковых данных во время выполнения (**true**) или отправки потоковых данных в виде блоков (**false**). По умолчанию устанавливается значение **true**. Дополнительные сведения см. в статье [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md).|  
  
## <a name="return-value"></a>Возвращаемое значение  
Ресурс инструкции. Если не удается создать ресурс инструкции, возвращается значение **false** .  
  
## <a name="remarks"></a>Remarks  
При подготовке инструкции, которая использует переменные в качестве параметров, эти переменные привязываются к инструкции. Это означает, что в случае обновления значений переменных при следующем выполнении инструкции она будет использовать обновленные значения параметров.  
  
Сочетание **sqlsrv_prepare** и **sqlsrv_execute** разделяет подготовку и выполнение инструкции между двумя вызовами функции и может использоваться для выполнения параметризованных запросов. Эта функция оптимально подходит для многократного выполнения инструкции с различными значениями параметров для каждого выполнения.  
  
Сведения об альтернативных стратегиях для записи и чтения больших объемов информации см. в статьях [Пакеты инструкций SQL](../../odbc/reference/develop-app/batches-of-sql-statements.md) и [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
Дополнительные сведения см. в статье [Практическое руководство. Извлечение параметров вывода с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a>Пример  
Следующий пример подготавливает и выполняет инструкцию. При выполнении инструкция (см. [sqlsrv_execute](../../connect/php/sqlsrv-execute.md)) обновляет поле в таблице *Sales.SalesOrderDetail* базы данных AdventureWorks. В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
Следующий пример показывает, как подготовить инструкцию и затем повторно выполнить ее с другими значениями параметров. Пример обновляет столбец *OrderQty* в таблице *Sales.SalesOrderDetail* базы данных AdventureWorks. После завершения обновлений в базу данных направляется запрос, чтобы убедиться, что обновления выполнены успешно. В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
> Рекомендуется использовать строки в качестве входных данных при привязке значений к [десятичным или числовым столбцам](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql), чтобы обеспечить точность и правильность, поскольку PHP имеет ограниченную точность для [чисел с плавающей запятой](https://php.net/manual/en/language.types.float.php). То же касается и столбцов bigint, особенно в том случае, если значения выходят за пределы диапазона [целых чисел](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

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

## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Практическое руководство. Выполнение параметризованных запросов](../../connect/php/how-to-perform-parameterized-queries.md)

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)

[Практическое руководство. Отправка данных в виде потока](../../connect/php/how-to-send-data-as-a-stream.md)

[Использование параметров направления](../../connect/php/using-directional-parameters.md)

[Извлечение данных](../../connect/php/retrieving-data.md)

[Обновление данных (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

