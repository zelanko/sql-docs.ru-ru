---
title: sqlsrv_rows_affected | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_rows_affected
apitype: NA
helpviewer_keywords:
- sqlsrv_rows_affected
- API Reference, sqlsrv_rows_affected
ms.assetid: 6f43fbfc-fc92-449b-82d0-33fa780e8f09
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 93c7ec396d3388a2de6c0d6518fc516de7156f35
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "68014953"
---
# <a name="sqlsrv_rows_affected"></a>sqlsrv_rows_affected
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Возвращает число строк, измененных при выполнении последней инструкции. Эта функция не возвращает число строк, возвращенных инструкцией SELECT.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_rows_affected( resource $stmt)  
```  
  
#### <a name="parameters"></a>Параметры  
*$stmt*: ресурс инструкции, соответствующий выполненной инструкции.  
  
## <a name="return-value"></a>Возвращаемое значение  
Целое число, указывающее количество строк, измененных при выполнении последней инструкции. Если никакие строки не были изменены, возвращается нуль (0). Если данные о количестве измененных строк недоступны, возвращается минус единица (-1). Если при получении количества измененных строк произошла ошибка, возвращается значение **false** .  
  
## <a name="example"></a>Пример  
Следующий пример отображает число строк, измененных инструкцией UPDATE. В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  
/* Set up Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET SpecialOfferID = ?   
         WHERE ProductID = ?";  
  
/* Set parameter values. */  
$params = array(2, 709);  
  
/* Execute the statement. */  
$stmt = sqlsrv_query( $conn, $tsql, $params);  
  
/* Get the number of rows affected and display appropriate message.*/  
$rows_affected = sqlsrv_rows_affected( $stmt);  
if( $rows_affected === false)  
{  
     echo "Error in calling sqlsrv_rows_affected.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
elseif( $rows_affected == -1)  
{  
      echo "No information available.\n";  
}  
else  
{  
      echo $rows_affected." rows were updated.\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  

[Обновление данных (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  

  
