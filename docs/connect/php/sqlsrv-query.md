---
title: "sqlsrv_query | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqlsrv_query
apitype: NA
helpviewer_keywords:
- sqlsrv_query
- executing queries
- API Reference, sqlsrv_query
ms.assetid: 9fa7c4c8-4da8-4299-9893-f61815055aa3
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a1dbc5c20a1d9fb1210bb7729f36299ea4392ebc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvquery"></a>sqlsrv_query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Подготавливает и выполняет инструкцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_query( resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>Параметры  
*$conn*: ресурс подключения, связанный с подготовленной инструкцией.  
  
*$tsql*: выражение Transact-SQL, соответствующее подготовленной инструкции.  
  
*$params* [необязательно]: **массива** значений, которые соответствуют параметрам в параметризованном запросе. Каждый элемент массива может быть одним из следующих значений:  
  
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
    |*$direction*[необязательно]|Одно из следующих **SQLSRV_PARAM_\* ** константы, используемые для указания направления параметра: **SQLSRV_PARAM_IN**, **SQLSRV_PARAM_OUT**, **SQLSRV_PARAM_INOUT**. Значение по умолчанию — **SQLSRV_PARAM_IN**.<br /><br />Дополнительные сведения о константах PHP см. в разделе [константы &#40; Драйверы Майкрософт для PHP для SQL Server &#41; ](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*[необязательно]|Объект **SQLSRV_PHPTYPE_\* ** константа, указывающая тип данных PHP для возвращаемого значения.<br /><br />Дополнительные сведения о константах PHP см. в разделе [константы &#40; Драйверы Майкрософт для PHP для SQL Server &#41; ](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$sqlType*[необязательно]|Объект **SQLSRV_SQLTYPE_\* ** константа, указывающая тип данных SQL Server для входного значения.<br /><br />Дополнительные сведения о константах PHP см. в разделе [константы &#40; Драйверы Майкрософт для PHP для SQL Server &#41; ](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
  
*$options* [необязательно]: ассоциативный массив, который задает свойства запроса. Поддерживаются следующие ключи:  
  
|Key|Поддерживаемые значения|Описание|  
|-------|--------------------|---------------|  
|QueryTimeout|Положительное целое значение.|Задает время ожидания выполнения запроса в секундах. По умолчанию драйвер ожидает результаты бесконечно.|  
|SendStreamParamsAtExec|**true** или **false**<br /><br />Значение по умолчанию — **true**|Настраивает драйвер на отправку всех потоковых данных во время выполнения (**true**), или для отправки потоковых данных в виде блоков (**false**). По умолчанию устанавливается значение **true**. Дополнительные сведения см. в статье [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md).|  
|Прокручиваемые курсоры|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|Дополнительные сведения об этих значениях см. в статье [Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).|  
  
## <a name="return-value"></a>Возвращаемое значение  
Ресурс инструкции. Если инструкция не удается создать или выполнить, **false** возвращается.  
  
## <a name="remarks"></a>Замечания  
**Sqlsrv_query** функция хорошо подходит для одноразовых запросов и должна использоваться по умолчанию для выполнения запросов, если только не действуют особые обстоятельства. Эта функция предоставляет оптимальный метод для выполнения запроса с использованием минимального количества кода. Функция **sqlsrv_query** подготавливает и выполняет инструкцию, а также может применяться для выполнения параметризованных запросов.  
  
Дополнительные сведения см. в статье [How to: Retrieve Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a>Пример  
В следующем примере отдельная строка вставляется в таблицу *Sales.SalesOrderDetail* базы данных AdventureWorks. В примере предполагается, что SQL Server и базы данных [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
> [!NOTE]  
> Несмотря на то, что в следующем примере инструкция INSERT для демонстрации использования **sqlsrv_query** для однократного выполнения инструкции, эта концепция распространяется на все инструкции Transact-SQL.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
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
$stmt = sqlsrv_query( $conn, $tsql, $params);  
if( $stmt )  
{  
     echo "Row successfully inserted.\n";  
}  
else  
{  
     echo "Row insertion failed.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Пример  
Следующий пример обновляет поле в таблице *Sales.SalesOrderDetail* базы данных AdventureWorks. В примере предполагается, что SQL Server и базы данных [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ( ?)   
         WHERE SalesOrderDetailID = ( ?)";  
  
/* Assign literal parameter values. */  
$params = array( 5, 10);  
  
/* Execute the query. */  
if( sqlsrv_query( $conn, $tsql, $params))  
{  
      echo "Statement executed.\n";  
}   
else  
{  
      echo "Error in statement execution.\n";  
      die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Практическое руководство. Выполнение параметризованных запросов](../../connect/php/how-to-perform-parameterized-queries.md)  
[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
[Практическое руководство. Отправка данных в виде потока](../../connect/php/how-to-send-data-as-a-stream.md)  
[Использование параметров направления](../../connect/php/using-directional-parameters.md)  
  

