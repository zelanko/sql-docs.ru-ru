---
title: "Как: выполнение параметризованных запросов | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating data
- parameterized queries
ms.assetid: dc7d0ede-a9b6-4ce2-977e-4d1e7ec2131c
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b233b2ac8b3ca454381eb3e0782ece33d59cbc8a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-perform-parameterized-queries"></a>Практическое руководство. Выполнение параметризованных запросов
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта статья обобщает и демонстрирует возможности использования [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] для выполнения параметризованного запроса.  
  
Все действия по выполнению параметризованного запроса можно свести к четырем шагам.  
  
1.  Используйте знаки вопроса (?) в качестве заполнителей в строке Transact-SQL, которая представляет выполняемый запрос.  
  
2.  Инициализируйте или обновите переменные PHP, которые соответствуют заполнителям в запросе Transact-SQL.  
  
3.  Используйте переменные PHP из шага 2, чтобы создать или обновить массив значений параметров, порядок которых соответствует заполнителям параметров в строке Transact-SQL.  
  
4.  Выполните запрос:  
  
    -   При работе с драйвером SQLSRV используйте [sqlsrv_query](../../connect/php/sqlsrv-query.md) или [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)/[sqlsrv_execute](../../connect/php/sqlsrv-execute.md).  
  
    -   При использовании драйвера PDO_SQLSRV выполнение запроса с [PDO::prepare](../../connect/php/pdo-prepare.md) и [PDOStatement::execute](../../connect/php/pdostatement-execute.md). Статьи, посвященные [PDO::prepare](../../connect/php/pdo-prepare.md) и [PDOStatement::execute](../../connect/php/pdostatement-execute.md) , содержат примеры кода.  
  
Оставшаяся часть этой статьи посвящена работе с параметризованными запросами с помощью драйвера SQLSRV.  
  
> [!NOTE]  
> Выполняется неявная привязка параметров с помощью **sqlsrv_prepare**. Это означает, что если параметризованный запрос подготовлен с помощью **sqlsrv_prepare** и значения в массиве параметров обновлены, при следующем выполнении запроса будут использоваться обновленные значения. Для получения дополнительных сведений см. второй пример в этой статье.  
  
## <a name="example"></a>Пример  
Следующий пример обновляет количество для указанного кода продукта в таблице *Production.ProductInventory* базы данных AdventureWorks. Количество и код продукта являются параметрами в запросе UPDATE.  
  
Затем пример отправляет в базу данных запрос для проверки правильности обновления количества. Идентификатор продукта является параметром в запросе SELECT.  
  
В примере предполагается, что SQL Server и базы данных [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  
/* Define the Transact-SQL query.  
Use question marks as parameter placeholders. */  
$tsql1 = "UPDATE Production.ProductInventory   
          SET Quantity = ?   
          WHERE ProductID = ?";  
  
/* Initialize $qty and $productId */  
$qty = 10; $productId = 709;  
  
/* Execute the statement with the specified parameter values. */  
$stmt1 = sqlsrv_query( $conn, $tsql1, array($qty, $productId));  
if( $stmt1 === false )  
{  
     echo "Statement 1 could not be executed.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free statement resources. */  
sqlsrv_free_stmt( $stmt1);  
  
/* Now verify the updated quantity.  
Use a question mark as parameter placeholder. */  
$tsql2 = "SELECT Quantity   
          FROM Production.ProductInventory  
          WHERE ProductID = ?";  
  
/* Execute the statement with the specified parameter value.  
Display the returned data if no errors occur. */  
$stmt2 = sqlsrv_query( $conn, $tsql2, array($productId));  
if( $stmt2 === false )  
{  
     echo "Statement 2 could not be executed.\n";  
     die( print_r(sqlsrv_errors(), true));  
}  
else  
{  
     $qty = sqlsrv_fetch_array( $stmt2);  
     echo "There are $qty[0] of product $productId in inventory.\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_close( $conn);  
?>  
```  
  
В предыдущем примере для выполнения запросов используется функция **sqlsrv_query** . Эта функция хорошо подходит для выполнения однократных запросов, так как она объединяет в себе подготовку и выполнение инструкции. Сочетание **sqlsrv_prepare**/**sqlsrv_execute** лучше всего подходит для повторного выполнения запроса с различными значениями параметров. Чтобы ознакомиться с примером повторного выполнения запроса с другими значениями параметров, см. следующий пример.  
  
## <a name="example"></a>Пример  
Следующий пример демонстрирует неявную привязку переменных при использовании функции **sqlsrv_prepare** . Этот пример вставляет несколько заказов на продажу в таблицу *Sales.SalesOrderDetail* . *$Params* привязывается к инструкции (*$stmt*) при **sqlsrv_prepare** вызывается. Перед каждым выполнением запроса, который вставляет в таблицу новый заказ на продажу, массив *$params* обновляется новыми значениями, соответствующими сведениям об этом заказе на продажу. При последующем выполнении запроса используются новые значения параметров.  
  
В примере предполагается, что SQL Server и базы данных [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  
$tsql = "INSERT INTO Sales.SalesOrderDetail (SalesOrderID,   
                                             OrderQty,   
                                             ProductID,   
                                             SpecialOfferID,   
                                             UnitPrice)  
         VALUES (?, ?, ?, ?, ?)";  
  
/* Each sub array here will be a parameter array for a query.  
The values in each sub array are, in order, SalesOrderID, OrderQty,  
 ProductID, SpecialOfferID, UnitPrice. */  
$parameters = array( array(43659, 8, 711, 1, 20.19),  
                     array(43660, 6, 762, 1, 419.46),  
                     array(43661, 4, 741, 1, 818.70)  
                    );  
  
/* Initialize parameter values. */  
$orderId = 0;  
$qty = 0;  
$prodId = 0;  
$specialOfferId = 0;  
$price = 0.0;  
  
/* Prepare the statement. $params is implicitly bound to $stmt. */  
$stmt = sqlsrv_prepare( $conn, $tsql, array( &$orderId,  
                                             &$qty,  
                                             &$prodId,  
                                             &$specialOfferId,  
                                             &$price));  
if( $stmt === false )  
{  
     echo "Statement could not be prepared.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Execute a statement for each set of params in $parameters.  
Because $params is bound to $stmt, as the values are changed, the  
new values are used in the subsequent execution. */  
foreach( $parameters as $params)  
{  
     list($orderId, $qty, $prodId, $specialOfferId, $price) = $params;  
     if( sqlsrv_execute($stmt) === false )  
     {  
          echo "Statement could not be executed.\n";  
          die( print_r( sqlsrv_errors(), true));  
     }  
     else  
     {  
          /* Verify that the row was successfully inserted. */  
          echo "Rows affected: ".sqlsrv_rows_affected( $stmt )."\n";  
     }  
}  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Преобразование типов данных](../../connect/php/converting-data-types.md)  
[Вопросы безопасности для драйвера SQL PHP](../../connect/php/security-considerations-for-php-sql-driver.md)
[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
[sqlsrv_rows_affected](../../connect/php/sqlsrv-rows-affected.md)  
  

