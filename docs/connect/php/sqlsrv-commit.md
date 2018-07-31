---
title: sqlsrv_commit | Документация Майкрософт
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_commit
apitype: NA
helpviewer_keywords:
- transaction support
- API Reference, sqlsrv_commit
- sqlsrv_commit
ms.assetid: bad67571-61ad-45b5-b4ff-677e3544f809
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d543667f15e3fcb1bf049bb595140098f303837e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37991196"
---
# <a name="sqlsrvcommit"></a>sqlsrv_commit
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Фиксирует текущую транзакцию для указанного подключения и возвращает подключение в режим автофиксации. Текущая транзакция включает в себя все инструкции для указанного подключения, выполненные после вызова [sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md) и до каких-либо вызовов [sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md) или **sqlsrv_commit**.  
  
> [!NOTE]  
> По умолчанию [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] находится в режиме автофиксации. Это означает, что все запросы автоматически фиксируются после успешного выполнения, если только они не были обозначены как часть явной транзакции с помощью **sqlsrv_begin_transaction**.  
  
> [!NOTE]  
> Если **sqlsrv_commit** вызывается для подключения, которое не находится в активной транзакции, инициированной с помощью **sqlsrv_begin_transaction**, вызов возвращает значение **false** , а в коллекцию ошибок добавляется ошибка *нет транзакции* .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_commit( resource $conn )  
```  
  
#### <a name="parameters"></a>Параметры  
*$conn*: подключение, для которого транзакция активна.  
  
## <a name="return-value"></a>Возвращаемое значение  
Логическое значение: **true** , если транзакция была успешно зафиксирована. В противном случае — **false**.  
  
## <a name="example"></a>Пример  
Следующий пример выполняет два запроса как часть транзакции. Если оба запроса выполняются успешно, транзакция фиксируется. В случае сбоя одного (или обоих) запросов транзакция откатывается.  
  
Первый запрос в примере вставляет новый заказ на продажу в таблицу *Sales.SalesOrderDetail* базы данных AdventureWorks. Этот заказ содержит пять единиц продукта с кодом 709. Второй запрос уменьшает количество складского запаса продукта с кодом 709 на пять единиц. Поскольку для точного отражения состояния заказов и доступности продуктов требуется успешное выполнение обоих запросов в базе данных, эти запросы включены в состав транзакции.  
  
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
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initiate transaction. */  
/* Exit script if transaction cannot be initiated. */  
if (sqlsrv_begin_transaction( $conn) === false)  
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

[Обзор драйверов Майкрософт для PHP для SQL Server](../../connect/php/overview-of-the-php-sql-driver.md)
  
