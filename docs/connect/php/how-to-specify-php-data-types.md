---
title: 'Как: Указание типов данных PHP | Документы Microsoft'
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
- converting data types
- streaming data
ms.assetid: fee6e6b8-aad9-496b-84a2-18d2950470a4
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b8b80353cc49c37da13b8e8e46ef3b758ed47aef
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-specify-php-data-types"></a>Практическое руководство. Указание типов данных PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В случае использования драйвера PDO_SQLSRV можно указать тип данных PHP при извлечении данных с сервера с помощью PDOStatement::bindColumn и PDOStatement::bindParam. Дополнительные сведения см. в разделах [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md) и [PDOStatement::bindParam](../../connect/php/pdostatement-bindparam.md) .  
  
Ниже представлена обобщенная процедура указания типов данных PHP при извлечении данных с сервера с помощью драйвера SQLSRV  
  
1.  Настройка и выполнение запроса Transact-SQL с [sqlsrv_query](../../connect/php/sqlsrv-query.md) или сочетание [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)/[sqlsrv_execute](../../connect/php/sqlsrv-execute.md).  
  
2.  Сделайте следующую строку данных доступной для чтения с помощью [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md).  
  
3.  Извлеките данные поля из возвращенной строки с помощью [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) с требуемым типом данных PHP, указанным в качестве необязательного третьего параметра. Если необязательный третий параметр не указан, данные возвращаются в соответствии с типами PHP по умолчанию. Дополнительные сведения о типах возвращаемых данных PHP по умолчанию см. в статье [Default PHP Data Types](../../connect/php/default-php-data-types.md).  
  
    Сведения о константах, используемых для указания типа данных PHP см. в разделе о PHPTYPE статьи [константы &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
## <a name="example"></a>Пример  
Следующий пример извлекает строки из таблицы *Production.ProductReview* базы данных AdventureWorks. В каждой возвращаемой строке *ReviewDate* извлекается в виде строки и *комментарии* извлекается в виде потока. Потоковые данные отображаются с помощью функции [fpassthru](http://php.net/manual/en/function.fpassthru.php) PHP.  
  
Предполагается, что SQL Server и [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) базы данных установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. */  
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
                ReviewDate,  
                Rating,   
                Comments   
         FROM Production.ProductReview   
         WHERE ProductID = ?   
         ORDER BY ReviewDate DESC";  
  
/* Set the parameter value. */  
$productID = 709;  
$params = array( $productID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data. The first and third fields are  
retrieved according to their default types, strings. The second field  
is retrieved as a string with 8-bit character encoding. The fourth  
field is retrieved as a stream with 8-bit character encoding.*/  
while ( sqlsrv_fetch( $stmt))  
{  
   echo "Name: ".sqlsrv_get_field( $stmt, 0 )."\n";  
   echo "Date: ".sqlsrv_get_field( $stmt, 1,   
                       SQLSRV_PHPTYPE_STRING( SQLSRV_ENC_CHAR))."\n";  
   echo "Rating: ".sqlsrv_get_field( $stmt, 2 )."\n";  
   echo "Comments: ";  
   $comments = sqlsrv_get_field( $stmt, 3,   
                            SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_CHAR));  
   fpassthru( $comments);  
   echo "\n";   
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
В этом примере извлечение второго поля (*ReviewDate*) в виде строки сохраняет тип данных SQL Server DATETIME с точностью до миллисекунды. По умолчанию тип данных DATETIME SQL Server извлекается в виде объекта DateTime PHP, в котором точность до миллисекунды теряется.  
  
Извлечение четвертого поля (*комментарии*) в виде потока осуществляется для демонстрационных целей. По умолчанию тип данных nvarchar(3850) SQL Server извлекается в виде строки, что вполне приемлемо в большинстве ситуаций.  
  
> [!NOTE]  
> Функция [sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md) предоставляет способ получения сведений о поле, включая информацию о типе, перед выполнением запроса.  
  
## <a name="see-also"></a>См. также  
[Извлечение данных](../../connect/php/retrieving-data.md)

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)

[Практическое руководство. Извлечение параметров вывода с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)

[How to: Retrieve Input and Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver.md)  
  
