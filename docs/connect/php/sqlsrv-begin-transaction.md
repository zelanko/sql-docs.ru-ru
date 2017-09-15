---
title: "sqlsrv_begin_transaction | Документы Microsoft"
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
- sqlsrv_begin_transaction
apitype: NA
helpviewer_keywords:
- sqlsrv_begin_transaction
- transaction support
- API Reference, sqlsrv_begin_transaction
ms.assetid: 0b223bc8-4047-4329-9cbf-d350ab0fb886
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b28185f3e858f30a9ff67c73381b0b9c4f07a028
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvbegintransaction"></a>sqlsrv_begin_transaction
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Начинает транзакцию для указанного подключения. Текущая транзакция включает в себя все инструкции для указанного подключения, выполненные после вызова **sqlsrv_begin_transaction** и до каких-либо вызовов [sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md) или [sqlsrv_commit](../../connect/php/sqlsrv-commit.md).  
  
> [!NOTE]  
> [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Находится в режиме автоматической фиксации по умолчанию. Это означает, что все запросы автоматически фиксируются после успешного выполнения, если только они не были обозначены как часть явной транзакции с помощью **sqlsrv_begin_transaction**.  
  
> [!NOTE]  
> Если **sqlsrv_begin_transaction** вызывается после того, как транзакция была запущена для подключения, но не была завершена путем вызова **sqlsrv_commit** или **sqlsrv_rollback**, вызов возвращает значение **false** , а в коллекцию ошибок добавляется ошибка *Транзакция уже выполняется* .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_begin_transaction( resource $conn)  
```  
  
#### <a name="parameters"></a>Параметры  
*$conn*: подключение, с которым сопоставлена транзакция.  
  
## <a name="return-value"></a>Возвращаемое значение  
Логическое значение: **true** , если транзакция была успешно начата. В противном случае — **false**.  
  
## <a name="example"></a>Пример  
Следующий пример выполняет два запроса как часть транзакции. Если оба запроса выполняются успешно, транзакция фиксируется. В случае сбоя одного (или обоих) запросов транзакция откатывается.  
  
Первый запрос в примере вставляет новый заказ на продажу в таблицу *Sales.SalesOrderDetail* базы данных AdventureWorks. Этот заказ содержит пять единиц продукта с кодом 709. Второй запрос уменьшает количество складского запаса продукта с кодом 709 на пять единиц. Поскольку для точного отражения состояния заказов и доступности продуктов требуется успешное выполнение обоих запросов в базе данных, эти запросы включены в состав транзакции.  
  
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
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initiate transaction. */  
/* Exit script if transaction cannot be initiated. */  
if ( sqlsrv_begin_transaction( $conn ) === false )  
{  
     echo "Could not begin transaction.\n";  
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initialize parameter values. */  
$orderId = 43659; $qty = 5; $productId = 709;  
$offerId = 1; $price = 5.70;  
  
/* Set up and execute the first query. */  
$tsql1 = "INSERT INTO Sales.SalesOrderDetail   
                     (SalesOrderID,   
                      OrderQty,   
                      ProductID,   
                      SpecialOfferID,   
                      UnitPrice)  
          VALUES (?, ?, ?, ?, ?)";  
$params1 = array( $orderId, $qty, $productId, $offerId, $price);  
$stmt1 = sqlsrv_query( $conn, $tsql1, $params1 );  
  
/* Set up and execute the second query. */  
$tsql2 = "UPDATE Production.ProductInventory   
          SET Quantity = (Quantity - ?)   
          WHERE ProductID = ?";  
$params2 = array($qty, $productId);  
$stmt2 = sqlsrv_query( $conn, $tsql2, $params2 );  
  
/* If both queries were successful, commit the transaction. */  
/* Otherwise, rollback the transaction. */  
if( $stmt1 && $stmt2 )  
{  
     sqlsrv_commit( $conn );  
     echo "Transaction was committed.\n";  
}  
else  
{  
     sqlsrv_rollback( $conn );  
     echo "Transaction was rolled back.\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_close( $conn);  
?>  
```  
  
Чтобы уделить основное внимание работе транзакции, в предыдущий пример не включены некоторые рекомендуемые аспекты обработки ошибок. В рабочем приложении рекомендуется проверять каждый вызов функции **sqlsrv** на наличие ошибок и обрабатывать их соответствующим образом.  
  
> [!NOTE]  
> Не используйте внедренный Transact-SQL для выполнения транзакций. Например, не выполняйте инструкцию с BEGIN TRANSACTION в качестве запроса Transact-SQL для начала транзакции. При использовании внедренного Transact-SQL для выполнения транзакций невозможно гарантировать правильную работу транзакций.  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Практическое руководство. Выполнение транзакций](../../connect/php/how-to-perform-transactions.md)  
[Общие сведения о драйвере SQL PHP](../../connect/php/overview-of-the-php-sql-driver.md) 
  

