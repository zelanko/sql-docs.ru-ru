---
title: "Типы курсоров (драйвер SQLSRV) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8472d839-8124-4a62-a83c-7e771b0d4962
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 92fa89c2f477b867930d1b53da7e6fa318a3d39d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="cursor-types-sqlsrv-driver"></a>Типы курсоров (драйвер SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Драйвер SQLSRV позволяет создать результирующий набор со строками, которые можно открыть в любом порядке, в зависимости от типа курсора.  В этом разделе обсуждаются (с буферизацией) на стороне клиента и стороне сервера (без буферизации) курсоров.  
  
## <a name="cursor-types"></a>Типы курсоров  
При создании результирующий набор с [sqlsrv_query](../../connect/php/sqlsrv-query.md) или [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md), можно указать тип курсора. По умолчанию используется однонаправленный курсор, которая позволяет переместить одной строке за раз, начиная с первой строки результирующего набора, пока не будет достигнут конец результирующего набора.  
  
Можно создать результирующий набор с Прокручиваемый курсор, который позволяет получить доступ к любой строки в результирующем наборе, в любом порядке. В следующей таблице перечислены значения, которые могут быть переданы в **прокручиваемый** sqlsrv_query или sqlsrv_prepare.  
  
|Параметр|Description|  
|----------|---------------|  
|SQLSRV_CURSOR_FORWARD|Позволяет перемещать одной строке за раз, начиная с первой строки результирующего набора, пока не будет достигнут конец результирующего набора.<br /><br />Это тип курсора по умолчанию.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) возвращает ошибку для результирующих наборов, созданных с этим типом курсора.<br /><br />**вперед** является сокращенной формой SQLSRV_CURSOR_FORWARD.|  
|SQLSRV_CURSOR_STATIC|Позволяет осуществлять доступ к строкам в любом порядке, но не будет отражать изменения в базе данных.<br /><br />**статические** является сокращенной формой SQLSRV_CURSOR_STATIC.|  
|SQLSRV_CURSOR_DYNAMIC|Позволяет осуществлять доступ к строкам в любом порядке и будет отражать изменения в базе данных.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) возвращает ошибку для результирующих наборов, созданных с этим типом курсора.<br /><br />**динамические** является сокращенной формой SQLSRV_CURSOR_DYNAMIC.|  
|SQLSRV_CURSOR_KEYSET|Позволяет вам получить доступ к строкам в любом порядке. Тем не менее курсор набора ключей не обновляет количество строк, если строка удаляется из таблицы (Удаленная строка возвращается без значений).<br /><br />**управляемые набором ключей** является сокращенной формой SQLSRV_CURSOR_KEYSET.|  
|SQLSRV_CURSOR_CLIENT_BUFFERED|Позволяет вам получить доступ к строкам в любом порядке. Создает запрос клиентского курсора.<br /><br />**буфер** является сокращенной формой SQLSRV_CURSOR_CLIENT_BUFFERED.|  
  
Если запрос создает несколько результирующих наборов, **прокручиваемый** параметр применяется для всех результирующих наборов.  
  
## <a name="selecting-rows-in-a-result-set"></a>При выборе строк в результирующем наборе  
После создания результирующего набора, можно использовать [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md), [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md), или [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) для указания строки.  
  
В следующей таблице описаны значения, можно указать в *строки* параметра.  
  
|Параметр|Description|  
|-------------|---------------|  
|SQLSRV_SCROLL_NEXT|Задает следующую строку. Это значение по умолчанию, если вы не укажете *строки* параметра для прокрутки результирующего набора.|  
|SQLSRV_SCROLL_PRIOR|Задает строку перед текущей строкой.|  
|SQLSRV_SCROLL_FIRST|Задает первую строку в результирующем наборе.|  
|SQLSRV_SCROLL_LAST|Задает последнюю строку в результирующем наборе.|  
|SQLSRV_SCROLL_ABSOLUTE|Указывает строку, указанную с *смещение* параметра.|  
|SQLSRV_SCROLL_RELATIVE|Указывает строку, указанную с *смещение* параметра из текущей строки.|  
  
## <a name="server-side-cursors-and-the-sqlsrv-driver"></a>Серверные курсоры и драйвера SQLSRV  
В следующем примере показано влияние различных курсоров. В строке 33 примера отображается первым из трех операторы запросов, которые определяют курсоров.  Две инструкции запроса в комментарий. Каждый раз при запуске программы, используйте другой тип курсора, анализируя обновления базы данных в строке 47.  
  
```  
<?php  
$server = "server_name";  
$conn = sqlsrv_connect( $server, array( 'Database' => 'test' ));  
if ( $conn === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "DROP TABLE dbo.ScrollTest" );  
if ( $stmt !== false ) {   
   sqlsrv_free_stmt( $stmt );   
}  
  
$stmt = sqlsrv_query( $conn, "CREATE TABLE ScrollTest (id int, value char(10))" );  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 1, "Row 1" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 2, "Row 2" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 3, "Row 3" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'keyset' ));  
// $stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'dynamic' ));  
// $stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'static' ));  
  
$rows = sqlsrv_has_rows( $stmt );  
if ( $rows != true ) {  
   die( "Should have rows" );  
}  
  
$result = sqlsrv_fetch( $stmt, SQLSRV_SCROLL_LAST );  
$field1 = sqlsrv_get_field( $stmt, 0 );  
$field2 = sqlsrv_get_field( $stmt, 1 );  
echo "\n$field1 $field2\n";  
  
$stmt2 = sqlsrv_query( $conn, "delete from ScrollTest where id = 3" );  
// or  
// $stmt2 = sqlsrv_query( $conn, "UPDATE ScrollTest SET id = 4 WHERE id = 3" );  
if ( $stmt2 !== false ) {   
   sqlsrv_free_stmt( $stmt2 );   
}  
  
$result = sqlsrv_fetch( $stmt, SQLSRV_SCROLL_LAST );  
$field1 = sqlsrv_get_field( $stmt, 0 );  
$field2 = sqlsrv_get_field( $stmt, 1 );  
echo "\n$field1 $field2\n";  
  
sqlsrv_free_stmt( $stmt );  
sqlsrv_close( $conn );  
?>  
```  
  
## <a name="client-side-cursors-and-the-sqlsrv-driver"></a>Клиентские курсоры и драйвера SQLSRV  
Клиентские курсоры — это функция, добавленные в версии 3.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] , позволяет кэшировать весь результирующий набор в памяти. Число строк становится доступной, после выполнения запроса при использовании клиентского курсора.  
  
Клиентские курсоры следует использовать для малых средних результирующих наборов. Используйте серверные курсоры для больших результирующих наборов.  
  
Запрос будет возвращать значение false, если буфер недостаточно велик для хранения всего результирующего набора. Можно увеличить размер буфера, вплоть до предела памяти PHP.  
  
С помощью драйвера SQLSRV, можно настроить размер буфера, который содержит результирующий набор с параметром ClientBufferMaxKBSize для [sqlsrv_configure](../../connect/php/sqlsrv-configure.md). [sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md) возвращает значение ClientBufferMaxKBSize. Можно также задать максимальный размер буфера в файле php.ini с sqlsrv. ClientBufferMaxKBSize (например, sqlsrv. ClientBufferMaxKBSize = 1024).  
  
Ниже приведен пример:  
  
-   Число строк всегда доступен в клиентский курсор.  
  
-   Использование курсоров на стороне клиента и пакетных инструкций.  
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "select * from HumanResources.Department";  
  
// Execute the query with client-side cursor.  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
if (! $stmt) {  
   echo "Error in statement execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// row count is always available with a client-side cursor  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count = $row_count\n";  
  
// Move to a specific row in the result set.  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
  
// Client-side cursor and batch statements  
$tsql = "select top 2 * from HumanResources.Employee;Select top 3 * from HumanResources.EmployeeAddress";  
  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
if (! $stmt) {  
   echo "Error in statement execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for first result set = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
  
sqlsrv_next_result($stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for second result set = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_LAST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
?>  
```  
  
В следующем примере показан клиентский курсор с помощью [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md).  
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "select * from HumanResources.Employee";  
$stmt = sqlsrv_prepare( $conn, $tsql, array(), array("Scrollable"=>SQLSRV_CURSOR_CLIENT_BUFFERED));  
  
if (! $stmt ) {  
   echo "Statement could not be prepared.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_execute( $stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
if ($row_count)  
   echo "\nRow count = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
if ($row ) {  
   $EmployeeID = sqlsrv_get_field( $stmt, 0);  
   echo "Employee ID = $EmployeeID \n";  
}  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)  
  

