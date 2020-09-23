---
title: Практическое руководство по извлечению параметров ввода-вывода с помощью драйвера SQLSRV
description: В этом разделе описывается, как получить входные и выходные параметры с помощью хранимых процедур и драйвера Microsoft SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedure support
ms.assetid: 9a7c5f60-67f9-4968-a3a8-c256ee481da2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ce35c6c0b3025a328c71de657fd1e89358379be
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680689"
---
# <a name="how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver"></a>Практическое руководство. Извлечение параметров ввода и вывода с помощью драйвера SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья описывает, как использовать драйвер SQLSRV для вызова хранимой процедуры, в которой один параметр определен как параметр ввода/вывода, и получить результаты. При извлечении параметра ввода или вывода все результаты, возвращаемые хранимой процедурой, должны быть использованы до того, как становится доступно значение возвращаемого параметра.  
  
> [!NOTE]  
>  Переменные, которые инициализируются или обновляются с использованием **null**, **DateTime**или типов потоков, нельзя использовать в качестве параметров вывода.  
  
## <a name="example-1"></a>Пример 1
Следующий пример вызывает хранимую процедуру, которая вычитает использованные часы отпуска из доступных часов отпуска для указанного сотрудника. Переменная *$vacationHrs*, которая представляет использованные часы отпуска, передается в хранимую процедуру в качестве параметра ввода. После обновления доступных часов отпуска хранимая процедура использует тот же самый параметр для возврата количества оставшихся часов отпуска.  
  
> [!NOTE]  
> Инициализация *$vacationHrs* значением 4 задает для возвращаемого PHPTYPE целое число. Для обеспечения целостности типа данных параметры ввода/вывода должны быть инициализированы перед вызовом хранимой процедуры, либо должен быть указан нужный PHPTYPE. Сведения об указании PHPTYPE см. в статье [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
Так как хранимая процедура возвращает два результата, [sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md) следует вызывать после выполнения хранимой процедуры, чтобы сделать доступным значение параметра вывода. После вызова **sqlsrv_next_result***$vacationHrs* содержит значение параметра вывода, возвращенное хранимой процедурой.  
  
> [!NOTE]  
> Рекомендуется вызывать хранимые процедуры с использованием канонического синтаксиса. Дополнительные сведения о каноническом синтаксисе см. в статье [Вызов хранимой процедуры](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md).  
  
В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  
/* Drop the stored procedure if it already exists. */  
$tsql_dropSP = "IF OBJECT_ID('SubtractVacationHours', 'P') IS NOT NULL  
                DROP PROCEDURE SubtractVacationHours";  
$stmt1 = sqlsrv_query( $conn, $tsql_dropSP);  
if( $stmt1 === false )  
{  
     echo "Error in executing statement 1.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Create the stored procedure. */  
$tsql_createSP = "CREATE PROCEDURE SubtractVacationHours  
                        @EmployeeID int,  
                        @VacationHrs smallint OUTPUT  
                  AS  
                  UPDATE HumanResources.Employee  
                  SET VacationHours = VacationHours - @VacationHrs  
                  WHERE EmployeeID = @EmployeeID;  
                  SET @VacationHrs = (SELECT VacationHours  
                                      FROM HumanResources.Employee  
                                      WHERE EmployeeID = @EmployeeID)";  
  
$stmt2 = sqlsrv_query( $conn, $tsql_createSP);  
if( $stmt2 === false )  
{  
     echo "Error in executing statement 2.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*--------- The next few steps call the stored procedure. ---------*/  
  
/* Define the Transact-SQL query. Use question marks (?) in place of  
the parameters to be passed to the stored procedure */  
$tsql_callSP = "{call SubtractVacationHours( ?, ?)}";  
  
/* Define the parameter array. By default, the first parameter is an  
INPUT parameter. The second parameter is specified as an INOUT  
parameter. Initializing $vacationHrs to 8 sets the returned PHPTYPE to  
integer. To ensure data type integrity, output parameters should be  
initialized before calling the stored procedure, or the desired  
PHPTYPE should be specified in the $params array.*/  
  
$employeeId = 4;  
$vacationHrs = 8;  
$params = array(   
                 array($employeeId, SQLSRV_PARAM_IN),  
                 array(&$vacationHrs, SQLSRV_PARAM_INOUT)  
               );  
  
/* Execute the query. */  
$stmt3 = sqlsrv_query( $conn, $tsql_callSP, $params);  
if( $stmt3 === false )  
{  
     echo "Error in executing statement 3.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Display the value of the output parameter $vacationHrs. */  
sqlsrv_next_result($stmt3);  
echo "Remaining vacation hours: ".$vacationHrs;  
  
/*Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_free_stmt( $stmt3);  
sqlsrv_close( $conn);  
?>  
```  

> [!NOTE]
> При привязке входного или выходного параметра к типу bigint, если значение может находиться вне диапазона для типа [integer](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md), нужно указать для него тип поля SQL SQLSRV_SQLTYPE_BIGINT. В противном случае может возникать исключение "Значение вне диапазона".

## <a name="example-2"></a>Пример 2
В этом примере кода показано, как привязать большое значение bigint в качестве входного или выходного параметра.  

```
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"testDB");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Assume the stored procedure spTestProcedure exists, which retrieves a bigint value of some large number
// e.g. 9223372036854
$bigintOut = 0;
$outSql = "{CALL spTestProcedure (?)}";
$stmt = sqlsrv_prepare($conn, $outSql, array(array(&$bigintOut, SQLSRV_PARAM_INOUT, null, SQLSRV_SQLTYPE_BIGINT)));
sqlsrv_execute($stmt);
echo "$bigintOut\n";   // Expect 9223372036854

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```

## <a name="see-also"></a>См. также:  
[Практическое руководство. Указание направления параметров с помощью драйвера SQLSRV](../../connect/php/how-to-specify-parameter-direction-using-the-sqlsrv-driver.md)

[Практическое руководство. Извлечение параметров вывода с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)

[Извлечение данных](../../connect/php/retrieving-data.md)  
  
