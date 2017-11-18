---
title: "Как: извлечение двоичных данных в виде потока с помощью драйвера SQLSRV | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retrieving data, as a binary stream
- streaming data
ms.assetid: cd8d6382-abe6-48ee-9d10-4e6c52c0cb9a
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9cfd6c030465016673acc6c81706e88979078629
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-retrieve-binary-data-as-a-stream-using-the-sqlsrv-driver"></a>Практическое руководство. Извлечение двоичных данных в виде потока с помощью драйвера SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлечение данных в виде потока доступно только в драйвере SQLSRV [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]и недоступно в драйвере PDO_SQLSRV.  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] использует преимущества потоков PHP для извлечения больших объемов двоичных данных с сервера. Эта статья описывает, как извлекать двоичные данные в виде потока.  
  
Применение потоков для извлечения двоичных данных, таких как изображения, позволяет избежать использования больших объемов памяти скрипта за счет извлечения блоков данных вместо загрузки в память скрипта всего объекта целиком.  
  
## <a name="example"></a>Пример  
Следующий пример извлекает двоичные данные (в данном случае это изображение) из таблицы *Production.ProductPhoto* базы данных AdventureWorks. Изображение извлекается в виде потока и отображается в браузере.  
  
Извлечение данных изображения в виде потока осуществляется с помощью [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md) и [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) с типом возвращаемого значения, указанным в виде двоичного потока. Тип возвращаемого значения определяется с помощью константы **SQLSRV_PHPTYPE_STREAM**. Сведения о **sqlsrv** константы, в разделе [константы &#40; Драйверы Майкрософт для PHP для SQL Server &#41; ](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
В примере предполагается, что SQL Server и базы данных [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) установлены на локальном компьютере. При выполнении примера в браузере все выходные данные выводятся в браузер.  
  
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
  
/* Set up the Transact-SQL query. */  
$tsql = "SELECT LargePhoto   
         FROM Production.ProductPhoto   
         WHERE ProductPhotoID = ?";  
  
/* Set the parameter values and put them in an array. */  
$productPhotoID = 70;  
$params = array( $productPhotoID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data.  
The return data is retrieved as a binary stream. */  
if ( sqlsrv_fetch( $stmt ) )  
{  
   $image = sqlsrv_get_field( $stmt, 0,   
                      SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_BINARY));  
   header("Content-Type: image/jpg");  
   fpassthru($image);  
}  
else  
{  
     echo "Error in retrieving data.</br>";  
     die(print_r( sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
Процедура указания типа возвращаемого значения в примере показывает, как указать тип возвращаемого значения PHP в виде двоичного потока. Технически это не требуется в примере из-за *LargePhoto* поле имеет тип varbinary(max) SQL Server и таким образом возвращаются в виде двоичного потока по умолчанию. Дополнительные сведения о типах данных PHP по умолчанию см. в статье [Default PHP Data Types](../../connect/php/default-php-data-types.md). Дополнительные сведения об указании типов возвращаемых данных PHP см. в статье [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
## <a name="see-also"></a>См. также:  
[Извлечение данных](../../connect/php/retrieving-data.md)  
[Извлечение данных в виде потока с помощью драйвера SQLSRV](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)  
[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
  

