---
title: Типы курсоров (драйвер PDO_SQLSRV) | Документация Майкрософт
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8472d839-8124-4a62-a83c-7e771b0d4962
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6452fc506814cdfdeee4f61085ec9a1ee0cededa
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801489"
---
# <a name="cursor-types-sqlsrv-driver"></a>Типы курсоров (драйвер SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Драйвер SQLSRV позволяет создать результирующий набор со строками, доступ к которым можно осуществлять в любом порядке в зависимости от типа курсора.  В этом разделе будут рассмотрены (буферизованный) на стороне клиента и на сервере (без буферизации) курсоров.  
  
## <a name="cursor-types"></a>Типы курсоров  
При создании результирующего набора с [sqlsrv_query](../../connect/php/sqlsrv-query.md) или [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md), можно указать тип курсора. По умолчанию используется однонаправленный курсор, которого вы можете переместить одну строку за раз, начиная с первой строки результирующего набора, вплоть до конца результирующего набора.  
  
Можно создать результирующий набор с Прокручиваемый курсор, который позволяет получить доступ к любой строки в результирующем наборе, в любом порядке. В следующей таблице перечислены значения, которые могут быть переданы **возможна прокрутка** sqlsrv_query или sqlsrv_prepare.  
  
|Параметр|Описание|  
|----------|---------------|  
|SQLSRV_CURSOR_FORWARD|Вы можете переместить одну строку за раз, начиная с первой строки результирующего набора, вплоть до конца результирующего набора.<br /><br />Это тип курсора по умолчанию.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) возвращает ошибку для результирующих наборов, созданных с этим типом курсора.<br /><br />**вперед** — это сокращенное название SQLSRV_CURSOR_FORWARD.|  
|SQLSRV_CURSOR_STATIC|Позволяет получить доступ к строкам в любом порядке, но не будет отражать изменения в базе данных.<br /><br />**статические** — это сокращенное название SQLSRV_CURSOR_STATIC.|  
|SQLSRV_CURSOR_DYNAMIC|Позволяет получить доступ к строкам в любом порядке и будет отражать изменения в базе данных.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) возвращает ошибку для результирующих наборов, созданных с этим типом курсора.<br /><br />**динамические** — это сокращенное название SQLSRV_CURSOR_DYNAMIC.|  
|SQLSRV_CURSOR_KEYSET|Позволяет вам получить доступ к строкам в любом порядке. Однако курсор набора ключей не обновляет количество строк, если строка удаляется из таблицы (удаленная строка возвращается без значений).<br /><br />**управляемые набором ключей** — это сокращенное название SQLSRV_CURSOR_KEYSET.|  
|SQLSRV_CURSOR_CLIENT_BUFFERED|Позволяет вам получить доступ к строкам в любом порядке. Создает запрос курсор на стороне клиента.<br /><br />**буфер** — это сокращенное название SQLSRV_CURSOR_CLIENT_BUFFERED.|  
  
Если запрос создает несколько результирующих наборов, **возможна прокрутка** параметр применяется для всех результирующих наборов.  
  
## <a name="selecting-rows-in-a-result-set"></a>Выбор строк в результирующем наборе  
После создания результирующего набора, можно использовать [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md), [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md), или [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) для указания строки.  
  
В следующей таблице описаны значения, указываемые в *строки* параметра.  
  
|Параметр|Описание|  
|-------------|---------------|  
|SQLSRV_SCROLL_NEXT|Задает следующую строку. Это значение по умолчанию, если вы не укажете *строки* параметр для прокручиваемых результирующих набора.|  
|SQLSRV_SCROLL_PRIOR|Указывает данной строки перед текущей строкой.|  
|SQLSRV_SCROLL_FIRST|Указывает первую строку в результирующем наборе.|  
|SQLSRV_SCROLL_LAST|Указывает последнюю строку в результирующем наборе.|  
|SQLSRV_SCROLL_ABSOLUTE|Указывает строки, заданной с помощью *смещение* параметра.|  
|SQLSRV_SCROLL_RELATIVE|Указывает строки, заданной с помощью *смещение* параметр из текущей строки.|  
  
## <a name="server-side-cursors-and-the-sqlsrv-driver"></a>Курсоры на стороне сервера и драйвера SQLSRV  
Следующий пример иллюстрирует различные курсоров. В строке 33 примера см. первый из трех операторы запросов, которые определяют курсоров.  Два из инструкции запроса снабжены комментариями. Каждый раз при запуске программы, используйте другой тип курсора и анализируя обновления базы данных в строке 47.  
  
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
Клиентские курсоры — это функция, добавленные в версии 3.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] , позволяет кэшировать весь результирующий набор в памяти. Число строк доступно после выполнения запроса при использовании клиентского курсора.  
  
Курсоры на стороне клиента следует использовать только для малых и средних результирующих наборов. Использование серверных курсоров для больших результирующих наборов.  
  
Запрос будет возвращать значение false, если буфер недостаточно велик для хранения весь результирующий набор. Вы можете увеличить размер этого буфера вплоть до максимального объема памяти PHP.  
  
С помощью драйвера SQLSRV, можно настроить размер буфера, который содержит результирующий набор с параметром ClientBufferMaxKBSize для [sqlsrv_configure](../../connect/php/sqlsrv-configure.md). [sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md) возвращает значение ClientBufferMaxKBSize. Можно также задать максимальный размер буфера в файле php.ini с sqlsrv. ClientBufferMaxKBSize (например, sqlsrv. ClientBufferMaxKBSize = 1024).  
  
В следующем примере показано:  
  
-   Число строк всегда входит в состав клиентского курсора.  
  
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
  
В следующем примере показан клиентский курсор с помощью [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) и размер буфера другого клиента.
  
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
$stmt = sqlsrv_prepare( $conn, $tsql, array(), array("Scrollable" => SQLSRV_CURSOR_CLIENT_BUFFERED, "ClientBufferMaxKBSize" => 51200));
  
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
  
