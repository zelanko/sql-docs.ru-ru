---
title: "Как: выполнение транзакций | Документы Microsoft"
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
- transaction support
ms.assetid: f4643b85-f929-4919-8951-23394bc5bfa7
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e24f0580fc79ab07043be419a866b19a47b80f73
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-perform-transactions"></a>Практическое руководство. Выполнение транзакций
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Драйвер SQLSRV [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] предоставляет три функции для выполнения транзакций:  
  
-   [sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md)  
  
-   [sqlsrv_commit](../../connect/php/sqlsrv-commit.md)  
  
-   [sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md)  
  
Драйвер PDO_SQLSRV предоставляет три метода для выполнения транзакций.  
  
-   [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md)  
  
-   [PDO::commit](../../connect/php/pdo-commit.md)  
  
-   [PDO::rollback](../../connect/php/pdo-rollback.md)  
  
Пример см. в статье [PDO::beginTransaction](../../connect/php/pdo-begintransaction.md) .  
  
В оставшейся части этой статьи объясняется и демонстрируется, как использовать драйвер SQLSRV для выполнения транзакций.  
  
## <a name="remarks"></a>Замечания  
Шаги по выполнению транзакции можно обобщить следующим образом.  
  
1.  Начните транзакцию с помощью **sqlsrv_begin_transaction**.  
  
2.  Проверьте состояние выполнения каждого запроса, входящего в состав транзакции.  
  
3.  При необходимости зафиксируйте транзакцию с помощью **sqlsrv_commit**. В противном случае выполните откат транзакции с помощью **sqlsrv_rollback**. После вызова метода **sqlsrv_commit** или **sqlsrv_rollback**, драйвер возвращается в режим автоматической фиксации.  
  
    По умолчанию [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] находится в режиме автоматической фиксации. Это означает, что все запросы автоматически фиксируются после успешного выполнения, если только они не были обозначены как часть явной транзакции с помощью **sqlsrv_begin_transaction**.  
  
    Если явная транзакция не фиксируется с помощью **sqlsrv_commit**, при закрытии соединения или прерывании работы сценария выполняется ее откат.  
  
    Не используйте внедренный Transact-SQL для выполнения транзакций. Например, не выполняйте инструкцию с BEGIN TRANSACTION в качестве запроса Transact-SQL для начала транзакции. При использовании внедренного Transact-SQL для выполнения транзакций невозможно гарантировать правильную работу транзакций.  
  
    Для выполнения транзакций следует использовать перечисленные выше функции **sqlsrv** .  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
Следующий пример выполняет несколько запросов как часть транзакции. Если все запросы выполняются успешно, транзакция фиксируется. В случае сбоя одного из запросов транзакция откатывается.  
  
Пример пытается удалить заказы на продажу из таблицы *Sales.SalesOrderDetail* и скорректировать уровни запасов в таблице *Product.ProductInventory* для каждого продукта в заказе на продажу. Поскольку для точного отражения состояния заказов и доступности продуктов требуется успешное выполнение всех запросов в базе данных, эти запросы включены в состав транзакции.  
  
Первый запрос в примере извлекает коды и количество продуктов для идентификатора указанного заказа на продажу. Этот запрос не является частью транзакции. Однако в случае сбоя этого запроса скрипт завершается, так как для выполнения запросов, которые являются частью последующей транзакции, требуются коды и количество продуктов.  
  
Следующие запросы (удаление заказа на продажу и обновление складских запасов продуктов) являются частью транзакции.  
  
В примере предполагается, что SQL Server и базы данных [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
### <a name="code"></a>код  
  
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
  
/* Begin transaction. */  
if( sqlsrv_begin_transaction($conn) === false )   
{   
     echo "Could not begin transaction.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set the Order ID.  */  
$orderId = 43667;  
  
/* Execute operations that are part of the transaction. Commit on  
success, roll back on failure. */  
if (perform_trans_ops($conn, $orderId))  
{  
     //If commit fails, roll back the transaction.  
     if(sqlsrv_commit($conn))  
     {  
         echo "Transaction committed.\n";  
     }  
     else  
     {  
         echo "Commit failed - rolling back.\n";  
         sqlsrv_rollback($conn);  
     }  
}  
else  
{  
     "Error in transaction operation - rolling back.\n";  
     sqlsrv_rollback($conn);  
}  
  
/*Free connection resources*/  
sqlsrv_close( $conn);  
  
/*----------------  FUNCTION: perform_trans_ops  -----------------*/  
function perform_trans_ops($conn, $orderId)  
{  
    /* Define query to update inventory based on sales order info. */  
    $tsql1 = "UPDATE Production.ProductInventory   
              SET Quantity = Quantity + s.OrderQty   
              FROM Production.ProductInventory p   
              JOIN Sales.SalesOrderDetail s   
              ON s.ProductID = p.ProductID   
              WHERE s.SalesOrderID = ?";  
  
    /* Define the parameters array. */  
    $params = array($orderId);  
  
    /* Execute the UPDATE statement. Return false on failure. */  
    if( sqlsrv_query( $conn, $tsql1, $params) === false ) return false;  
  
    /* Delete the sales order. Return false on failure */  
    $tsql2 = "DELETE FROM Sales.SalesOrderDetail   
              WHERE SalesOrderID = ?";  
    if(sqlsrv_query( $conn, $tsql2, $params) === false ) return false;  
  
    /* Return true because all operations were successful. */  
    return true;  
}  
?>  
```  
  
### <a name="comments"></a>Комментарии  
Чтобы уделить основное внимание работе транзакции, в предыдущий пример не включены некоторые рекомендуемые аспекты обработки ошибок. В рабочем приложении рекомендуется проверять каждый вызов функции **sqlsrv** на наличие ошибок и обрабатывать их соответствующим образом.  
  
## <a name="see-also"></a>См. также:  
[Обновление данных (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
[Транзакции (компонент Database Engine)](http://go.microsoft.com/fwlink/?LinkId=105862)  
[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
  

