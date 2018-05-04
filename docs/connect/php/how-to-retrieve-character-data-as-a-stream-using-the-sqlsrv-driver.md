---
title: Извлечение символьных данных в виде потока с помощью драйвера SQLSRV | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, as a character stream
- streaming data
ms.assetid: 3c0dbca4-abfc-4449-b133-66c819681840
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49f445be8a25bdef8aa32a07e0b8b6880bdde726
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-retrieve-character-data-as-a-stream-using-the-sqlsrv-driver"></a>Практическое руководство. Извлечение символьных данных в виде потока с помощью драйвера SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлечение данных в виде потока доступно только в драйвере SQLSRV [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]и недоступно в драйвере PDO_SQLSRV.  
  
Драйвер SQLSRV использует преимущества потоков PHP для извлечения больших объемов данных с сервера. Пример в этой статье показывает, как извлекать символьные данные в виде потока.  
  
## <a name="example"></a>Пример  
Следующий пример извлекает строку из таблицы *Production.ProductReview* базы данных AdventureWorks. *Комментарии* поля из возвращенной строки извлекается в виде потока и отображается с помощью PHP [fpassthru](http://php.net/manual/function.fpassthru.php) функции.  
  
Извлечение данных в виде потока осуществляется с помощью [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md) и [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) с типом возвращаемого значения, указанным в виде потока символов. Тип возвращаемого значения определяется с помощью константы **SQLSRV_PHPTYPE_STREAM**. Сведения о **sqlsrv** константы, в разделе [константы &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
Предполагается, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) базы данных установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "SELECT ReviewerName,   
               CONVERT(varchar(32), ReviewDate, 107) AS [ReviewDate],  
               Rating,   
               Comments   
         FROM Production.ProductReview   
         WHERE ProductReviewID = ? ";  
  
/* Set the parameter value. */  
$productReviewID = 1;  
$params = array( $productReviewID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data. The first three fields are retrieved  
as strings and the fourth as a stream with character encoding. */  
if(sqlsrv_fetch( $stmt ) === false )  
{  
     echo "Error in retrieving row.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
echo "Name: ".sqlsrv_get_field( $stmt, 0 )."\n";  
echo "Date: ".sqlsrv_get_field( $stmt, 1 )."\n";  
echo "Rating: ".sqlsrv_get_field( $stmt, 2 )."\n";  
echo "Comments: ";  
$comments = sqlsrv_get_field( $stmt, 3,   
                             SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_CHAR));  
fpassthru($comments);  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
Поскольку тип возвращаемых данных PHP для первых трех полей не задан, каждое поле возвращается в соответствии с его типом PHP по умолчанию. Дополнительные сведения о типах данных PHP по умолчанию см. в статье [Default PHP Data Types](../../connect/php/default-php-data-types.md). Дополнительные сведения об указании типов возвращаемых данных PHP см. в статье [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
## <a name="see-also"></a>См. также  
[Извлечение данных](../../connect/php/retrieving-data.md)

[Извлечение данных в виде потока с помощью драйвера SQLSRV](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
  
