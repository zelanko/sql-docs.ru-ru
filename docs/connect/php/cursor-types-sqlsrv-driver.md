---
title: Типы курсоров (драйвер SQLSRV) | Документация Майкрософт
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8472d839-8124-4a62-a83c-7e771b0d4962
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 763795618eb90fe24db313b801bc01af3cd6737b
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928037"
---
# <a name="cursor-types-sqlsrv-driver"></a>Типы курсоров (драйвер SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Драйвер SQLSRV позволяет создать результирующий набор со строками, доступ к которым можно осуществлять в любом порядке в зависимости от типа курсора.  В этой статье рассматриваются клиентские (в буфере) и серверные курсоры (без буферизации).  
  
## <a name="cursor-types"></a>Типы курсоров  
При создании результирующего набора с помощью [sqlsrv_query](../../connect/php/sqlsrv-query.md) или [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) можно указать тип курсора. По умолчанию используется курсор последовательного доступа, который позволяет переместить одну строку за раз, начиная с первой строки результирующего набора и до его конца.  
  
Можно создать результирующий набор с прокручиваемым курсором, который позволяет получить доступ к любой строке в результирующем наборе в любом порядке. В следующей таблице перечислены значения, которые можно передать в параметре **Scrollable** в sqlsrv_query или sqlsrv_prepare.  
  
|Параметр|Description|  
|----------|---------------|  
|SQLSRV_CURSOR_FORWARD|Позволяет переместить одну строку за раз, начиная с первой строки результирующего набора и до его конца.<br /><br />Это тип курсора по умолчанию.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) возвращает ошибку для результирующих наборов, созданных с этим типом курсора.<br /><br />**forward** является сокращенной формой SQLSRV_CURSOR_FORWARD.|  
|SQLSRV_CURSOR_STATIC|Позволяет получать доступ к строкам в любом порядке, но не отражает изменения в базе данных.<br /><br />**static** является сокращенной формой SQLSRV_CURSOR_STATIC.|  
|SQLSRV_CURSOR_DYNAMIC|Позволяет получать доступ к строкам в любом порядке и будет отражать изменения в базе данных.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) возвращает ошибку для результирующих наборов, созданных с этим типом курсора.<br /><br />**dynamic** является сокращенной формой SQLSRV_CURSOR_DYNAMIC.|  
|SQLSRV_CURSOR_KEYSET|Позволяет получать доступ к строкам в любом порядке. Однако курсор набора ключей не обновляет количество строк, если строка удаляется из таблицы (удаленная строка возвращается без значений).<br /><br />**keyset** является сокращенной формой SQLSRV_CURSOR_KEYSET.|  
|SQLSRV_CURSOR_CLIENT_BUFFERED|Позволяет получать доступ к строкам в любом порядке. Создает запрос курсора на стороне клиента.<br /><br />**buffered** является сокращенной формой SQLSRV_CURSOR_CLIENT_BUFFERED.|  
  
Если запрос формирует несколько результирующих наборов, параметр **Scrollable** применяется ко всем результирующим наборам.  
  
## <a name="selecting-rows-in-a-result-set"></a>Выбор строк в результирующем наборе  
После создания результирующего набора можно использовать [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md), [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) или [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md), чтобы указать строку.  
  
В следующей таблице описаны значения, которые можно указать в параметре *row*.  
  
|Параметр|Description|  
|-------------|---------------|  
|SQLSRV_SCROLL_NEXT|Задает следующую строку. Это значение по умолчанию, если параметр *row* для прокручиваемого набора результатов не указан.|  
|SQLSRV_SCROLL_PRIOR|Указывает строку перед текущей строкой.|  
|SQLSRV_SCROLL_FIRST|Указывает первую строку в результирующем наборе.|  
|SQLSRV_SCROLL_LAST|Указывает последнюю строку в результирующем наборе.|  
|SQLSRV_SCROLL_ABSOLUTE|Указывает строку, заданную в параметре *offset*.|  
|SQLSRV_SCROLL_RELATIVE|Указывает строку, заданную в параметре *offset* из текущей строки.|  
  
## <a name="server-side-cursors-and-the-sqlsrv-driver"></a>Курсоры на стороне сервера и драйвер SQLSRV  
В следующем примере показано воздействие различных курсоров. В строке 33 в примере показаны первые три оператора запроса, указывающие разные курсоры.  Два оператора запроса имеют комментарии. Каждый раз при запуске программы используйте другой тип курсора, чтобы увидеть результат обновления базы данных в строке 47.  
  
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
  
## <a name="client-side-cursors-and-the-sqlsrv-driver"></a>Курсоры на стороне клиента и драйвер SQLSRV  
Курсоры на стороне клиента были добавлены как функция в [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] версии 3.0. Они позволяют кэшировать в памяти весь результирующий набор. Число строк доступно после выполнения запроса при использовании курсора на стороне клиента.  
  
Курсоры на стороне клиента следует использовать только для малых и средних результирующих наборов. Используйте курсоры на стороне сервера для больших результирующих наборов.  
  
Запрос возвратит значение false, если буфер недостаточно большой для хранения всего результирующего набора. Вы можете увеличить размер этого буфера вплоть до максимального объема памяти PHP.  
  
С помощью драйвера SQLSRV можно настроить размер буфера, содержащего результирующий набор. Для этого нужно задать параметр ClientBufferMaxKBSize для [sqlsrv_configure](../../connect/php/sqlsrv-configure.md). [sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md) возвращает значение ClientBufferMaxKBSize. Можно также задать максимальный размер буфера в файле php.ini с помощью sqlsrv.ClientBufferMaxKBSize (например, sqlsrv.ClientBufferMaxKBSize = 1024).  
  
В примере ниже используется следующее:  
  
-   число строк всегда доступно для курсора на стороне клиента;  
  
-   использование курсоров на стороне клиента и пакетных операторов.  
  
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
  
В следующем примере показан курсор на стороне клиента, использующий [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) и размер буфера другого клиента.
  
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
  
