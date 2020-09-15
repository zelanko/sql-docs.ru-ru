---
description: sqlsrv_execute
title: sqlsrv_execute | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_execute
apitype: NA
helpviewer_keywords:
- sqlsrv_exclude
- executing queries
- API Reference, sqlsrv_execute
ms.assetid: 38331bc2-4391-4f9f-aa83-9873dad605a0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6daa3c227735f99d258590fbd281e306b7b84344
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413760"
---
# <a name="sqlsrv_execute"></a>sqlsrv_execute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Выполняет ранее подготовленную инструкцию. Сведения о подготовке инструкции к выполнению см. в статье [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) .  
  
> [!NOTE]  
> Эта функция оптимально подходит для многократного выполнения подготовленной инструкции с различными значениями параметров.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_execute( resource $stmt)  
```  
  
#### <a name="parameters"></a>Параметры  
*$stmt*: ресурс, указывающий инструкцию для выполнения. Дополнительные сведения о создании ресурса инструкции см. в статье [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
Логическое значение: **true** , если инструкция была выполнена успешно. В противном случае — **false**.  
  
## <a name="example"></a>Пример  
Следующий пример выполняет инструкцию, которая обновляет поле в таблице *Sales.SalesOrderDetail* базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works). В примере предполагается, что SQL Server и базы данных AdventureWorks установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ( ?)   
         WHERE SalesOrderDetailID = ( ?)";  
  
/* Set up the parameters array. Parameters correspond, in order, to  
question marks in $tsql. */  
$params = array( 5, 10);  
  
/* Create the statement. */  
$stmt = sqlsrv_prepare( $conn, $tsql, $params);  
if( $stmt )  
{  
     echo "Statement prepared.\n";  
}  
else  
{  
     echo "Error in preparing statement.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Execute the statement. Display any errors that occur. */  
if( sqlsrv_execute( $stmt))  
{  
      echo "Statement executed.\n";  
}  
else  
{  
     echo "Error in executing statement.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  

[sqlsrv_query](../../connect/php/sqlsrv-query.md)  
  
