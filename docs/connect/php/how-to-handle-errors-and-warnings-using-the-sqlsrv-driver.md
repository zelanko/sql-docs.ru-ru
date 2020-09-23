---
title: Практическое руководство. Обработка ошибок и предупреждений с помощью драйвера SQLSRV
description: Сведения об обработке ошибок и предупреждений при использовании драйвера Microsoft SQLSRV для PHP для SQL Server
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- errors and warnings
ms.assetid: fa231d60-4c06-4137-89e8-097c28638c5d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebb3ef454e23ad181bfee856a5b09d01b20632e9
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680649"
---
# <a name="how-to-handle-errors-and-warnings-using-the-sqlsrv-driver"></a>Практическое руководство. Обработка ошибок и предупреждений с помощью драйвера SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

По умолчанию драйвер SQLSRV рассматривает предупреждения как ошибки. Вызов функции **sqlsrv**, создающий ошибку или предупреждение, возвращает значение **false**. Эта статья показывает, как отключить это поведение по умолчанию и обрабатывать предупреждения отдельно от ошибок.  
  
> [!NOTE]  
> Существуют некоторые исключения из поведения по умолчанию, заключающегося в обработке предупреждений как ошибок. Предупреждения, которые соответствуют значениям SQLSTATE 01000, 01001, 01003 и 01S02, никогда не обрабатываются как ошибки.  
  
## <a name="example"></a>Пример  
Следующий пример кода использует две пользовательские функции — **DisplayErrors** и **DisplayWarnings** — для обработки ошибок и предупреждений. Пример показывает раздельную обработку ошибок и предупреждений, выполняя следующие действия:  
  
1.  отключает поведение по умолчанию, заключающееся в обработке предупреждений как ошибок;  
  
2.  создает хранимую процедуру, которая обновляет часы отпуска сотрудника и возвращает оставшиеся часы отпуска в качестве параметра вывода. Если количество доступных часов отпуска сотрудника меньше нуля, хранимая процедура выводит предупреждение.  
  
3.  Обновляет количество часов отпуска для нескольких сотрудников посредством вызова хранимой процедуры для каждого сотрудника и отображает сообщения, связанные со всеми возникающими предупреждениями и ошибками.  
  
4.  Отображает оставшиеся часы отпуска для каждого сотрудника.  
  
В первом вызове функции **sqlsrv** ([sqlsrv_configure](../../connect/php/sqlsrv-configure.md)) предупреждения обрабатываются как ошибки. Так как предупреждения добавляются в коллекцию ошибок, вам не нужно проверять предупреждения отдельно от ошибок. Однако при последующих вызовах функций **sqlsrv** предупреждения не обрабатываются как ошибки, поэтому необходимо явным образом выполнять проверку как для предупреждений, так и для ошибок.  
  
Также обратите внимание, что код примера проверяет наличие ошибок после каждого вызова функции **sqlsrv** . Именно такой подход и рекомендуется использовать.  
  
В примере предполагается, что SQL Server и база данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль. При запуске примера для вновь установленной базы данных AdventureWorks он выдает три предупреждения и две ошибки. Первые два предупреждения являются стандартными и выдаются при подключении к базе данных. Третье предупреждение возникает из-за того, что количество доступных часов отпуска сотрудника принимает значение меньше нуля. Ошибки возникают потому, что количество доступных часов отпуска сотрудника принимает значение меньше −40 часов, что является нарушением ограничения для таблицы.  
  
```  
<?php  
/* Turn off the default behavior of treating errors as warnings.  
Note: Turning off the default behavior is done here for demonstration  
purposes only. If setting the configuration fails, display errors and  
exit the script. */  
if( sqlsrv_configure("WarningsReturnAsErrors", 0) === false)  
{  
     DisplayErrors();  
     die;  
}  
  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
/* If the connection fails, display errors and exit the script. */  
if( $conn === false )  
{  
     DisplayErrors();  
     die;  
}  
/* Display any warnings. */  
DisplayWarnings();  
  
/* Drop the stored procedure if it already exists. */  
$tsql1 = "IF OBJECT_ID('SubtractVacationHours', 'P') IS NOT NULL  
                DROP PROCEDURE SubtractVacationHours";  
$stmt1 = sqlsrv_query($conn, $tsql1);  
  
/* If the query fails, display errors and exit the script. */  
if( $stmt1 === false)  
{  
     DisplayErrors();  
     die;  
}  
/* Display any warnings. */  
DisplayWarnings();  
  
/* Free the statement resources. */  
sqlsrv_free_stmt( $stmt1 );  
  
/* Create the stored procedure. */  
$tsql2 = "CREATE PROCEDURE SubtractVacationHours  
                  @EmployeeID int,  
                  @VacationHours smallint OUTPUT  
              AS  
                  UPDATE HumanResources.Employee  
                  SET VacationHours = VacationHours - @VacationHours  
                  WHERE EmployeeID = @EmployeeID;  
                  SET @VacationHours = (SELECT VacationHours    
                                       FROM HumanResources.Employee  
                                       WHERE EmployeeID = @EmployeeID);  
              IF @VacationHours < 0   
              BEGIN  
                PRINT 'WARNING: Vacation hours are now less than zero.'  
              END;";  
$stmt2 = sqlsrv_query( $conn, $tsql2 );  
  
/* If the query fails, display errors and exit the script. */  
if( $stmt2 === false)  
{  
     DisplayErrors();  
     die;  
}  
/* Display any warnings. */  
DisplayWarnings();  
  
/* Free the statement resources. */  
sqlsrv_free_stmt( $stmt2 );  
  
/* Set up the array that maps employee ID to used vacation hours. */  
$emp_hrs = array (7=>4, 8=>5, 9=>8, 11=>50);  
  
/* Initialize variables that will be used as parameters. */  
$employeeId = 0;  
$vacationHrs = 0;  
  
/* Set up the parameter array. */  
$params = array(  
                 array(&$employeeId, SQLSRV_PARAM_IN),  
                 array(&$vacationHrs, SQLSRV_PARAM_INOUT)  
                );  
  
/* Define and prepare the query to subtract used vacation hours. */  
$tsql3 = "{call SubtractVacationHours(?, ?)}";  
$stmt3 = sqlsrv_prepare($conn, $tsql3, $params);  
  
/* If the statement preparation fails, display errors and exit the script. */  
if( $stmt3 === false)  
{  
     DisplayErrors();  
     die;  
}  
/* Display any warnings. */  
DisplayWarnings();  
  
/* Loop through the employee=>vacation hours array. Update parameter  
 values before statement execution. */  
foreach(array_keys($emp_hrs) as $employeeId)  
{  
     $vacationHrs = $emp_hrs[$employeeId];  
     /* Execute the query.  If it fails, display the errors. */  
     if( sqlsrv_execute($stmt3) === false)  
     {  
          DisplayErrors();  
          die;  
     }  
     /* Display any warnings. */  
     DisplayWarnings();  
  
     /*Move to the next result returned by the stored procedure. */  
     if( sqlsrv_next_result($stmt3) === false)  
     {  
          DisplayErrors();  
          die;  
     }  
     /* Display any warnings. */  
     DisplayWarnings();  
  
     /* Display updated vacation hours. */  
     echo "EmployeeID $employeeId has $vacationHrs ";  
     echo "remaining vacation hours.\n";  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt3 );  
sqlsrv_close( $conn );  
  
/* ------------- Error Handling Functions --------------*/  
function DisplayErrors()  
{  
     $errors = sqlsrv_errors(SQLSRV_ERR_ERRORS);  
     foreach( $errors as $error )  
     {  
          echo "Error: ".$error['message']."\n";  
     }  
}  
  
function DisplayWarnings()  
{  
     $warnings = sqlsrv_errors(SQLSRV_ERR_WARNINGS);  
     if(!is_null($warnings))  
     {  
          foreach( $warnings as $warning )  
          {  
               echo "Warning: ".$warning['message']."\n";  
          }  
     }  
}  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Практическое руководство. Настройка обработки ошибок и предупреждений с помощью драйвера SQLSRV](../../connect/php/how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver.md)

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  
