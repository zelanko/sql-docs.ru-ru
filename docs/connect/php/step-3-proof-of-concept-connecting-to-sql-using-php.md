---
title: 'Шаг 3. Подтверждение концепции: подключение к SQL с помощью PHP | Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a7451a85-18e5-4fd0-bbcb-2f15a1117290
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d685c15b4cc30dc093a47b37e6bfc29368e91f0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "68014800"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-php"></a>Шаг 3. Подтверждение концепции: подключение к SQL с помощью PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="step-1--connect"></a>Шаг 1.  Подключение  
  
  
Эта функция **OpenConnection** вызывается перед выполнением всех последующих функций.  
  
  
```php 
    function OpenConnection()  
    {  
        try  
        {  
            $serverName = "tcp:myserver.database.windows.net,1433";  
            $connectionOptions = array("Database"=>"AdventureWorks",  
                "Uid"=>"MyUser", "PWD"=>"MyPassword");  
            $conn = sqlsrv_connect($serverName, $connectionOptions);  
            if($conn == false)  
                die(FormatErrors(sqlsrv_errors()));  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="step-2--execute-query"></a>Шаг 2.  Выполнение запроса  
  
Функция [sqlsrv_query()](https://php.net/manual/en/function.sqlsrv-query.php) может использоваться для извлечения результирующего набора из запроса к Базе данных SQL. Эта функция фактически принимает любой запрос и объект подключения, а затем возвращает результирующий набор для итеративного перебора с помощью [sqlsrv_fetch_array()](https://php.net/manual/en/function.sqlsrv-fetch-array.php).  
  
```php  
    function ReadData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
            $tsql = "SELECT [CompanyName] FROM SalesLT.Customer";  
            $getProducts = sqlsrv_query($conn, $tsql);  
            if ($getProducts == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
            $productCount = 0;  
            while($row = sqlsrv_fetch_array($getProducts, SQLSRV_FETCH_ASSOC))  
            {  
                echo($row['CompanyName']);  
                echo("<br/>");  
                $productCount++;  
            }  
            sqlsrv_free_stmt($getProducts);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
  
## <a name="step-3--insert-a-row"></a>Шаг 3.  Вставка строки  
  
В этом примере вы увидите, как безопасно выполнить инструкцию [INSERT](../../t-sql/statements/insert-transact-sql.md) и передать параметры для защиты от [внедрения кода SQL](../../relational-databases/tables/primary-and-foreign-key-constraints.md).    
  
  
```php 
    function InsertData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
  
            $tsql = "INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT            INSERTED.ProductID VALUES ('SQL Server 1', 'SQL Server 2', 0, 0, getdate())";  
            //Insert query  
            $insertReview = sqlsrv_query($conn, $tsql);  
            if($insertReview == FALSE)  
                die(FormatErrors( sqlsrv_errors()));  
            echo "Product Key inserted is :";  
            while($row = sqlsrv_fetch_array($insertReview, SQLSRV_FETCH_ASSOC))  
            {     
                echo($row['ProductID']);  
            }  
            sqlsrv_free_stmt($insertReview);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="step-4--rollback-a-transaction"></a>Шаг 4.  Откат транзакции  
  
  
Этот пример кода демонстрирует использование транзакций, в которых можно:  
  
— начать транзакцию;  
  
— вставить строку данных, обновить другую строку данных;  
  
— зафиксировать транзакцию, если запросы на вставку и обновление выполнены успешно, или откатить транзакцию, если один из них вызвал ошибку.  
  
  
```php 
    function Transactions()  
    {  
        try  
        {  
            $conn = OpenConnection();  
  
            if (sqlsrv_begin_transaction($conn) == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
  
            $tsql1 = "INSERT INTO SalesLT.SalesOrderDetail (SalesOrderID,OrderQty,ProductID,UnitPrice)  
            VALUES (71774, 22, 709, 33)";  
            $stmt1 = sqlsrv_query($conn, $tsql1);  
  
            /* Set up and execute the second query. */  
            $tsql2 = "UPDATE SalesLT.SalesOrderDetail SET OrderQty = (OrderQty + 1) WHERE ProductID = 709";  
            $stmt2 = sqlsrv_query( $conn, $tsql2);  
  
            /* If both queries were successful, commit the transaction. */  
            /* Otherwise, rollback the transaction. */  
            if($stmt1 && $stmt2)  
            {  
                   sqlsrv_commit($conn);  
                   echo("Transaction was commited");  
            }  
            else  
            {  
                sqlsrv_rollback($conn);  
                echo "Transaction was rolled back.\n";  
            }  
            /* Free statement and connection resources. */  
            sqlsrv_free_stmt( $stmt1);  
            sqlsrv_free_stmt( $stmt2);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="additional-examples"></a>Дополнительные примеры  
  
[Пример приложения (драйвер SQLSRV)](../../connect/php/example-application-sqlsrv-driver.md)  

[Пример приложения (драйвер PDO_SQLSRV)](../../connect/php/example-application-pdo-sqlsrv-driver.md)
