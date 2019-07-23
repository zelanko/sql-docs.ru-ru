---
title: Как указать типы данных PHP | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data types
- streaming data
ms.assetid: fee6e6b8-aad9-496b-84a2-18d2950470a4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ae00c01e962da05015a5132608915fc9d70258f4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936398"
---
# <a name="how-to-specify-php-data-types"></a>Практическое руководство. Указание типов данных PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

В случае использования драйвера PDO_SQLSRV можно указать тип данных PHP при извлечении данных с сервера с помощью PDOStatement::bindColumn и PDOStatement::bindParam. Дополнительные сведения см. в разделах [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md) и [PDOStatement::bindParam](../../connect/php/pdostatement-bindparam.md) .  
  
Ниже представлена обобщенная процедура указания типов данных PHP при извлечении данных с сервера с помощью драйвера SQLSRV  
  
1.  Установка и выполнение запроса Transact-SQL с помощью [sqlsrv_query](../../connect/php/sqlsrv-query.md) или сочетания [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)/[sqlsrv_execute](../../connect/php/sqlsrv-execute.md).  
  
2.  Сделайте следующую строку данных доступной для чтения с помощью [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md).  
  
3.  Извлеките данные поля из возвращенной строки с помощью [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) с требуемым типом данных PHP, указанным в качестве необязательного третьего параметра. Если необязательный третий параметр не указан, данные возвращаются в соответствии с типами PHP по умолчанию. Дополнительные сведения о типах возвращаемых данных PHP по умолчанию см. в статье [Default PHP Data Types](../../connect/php/default-php-data-types.md).  
  
    Дополнительные сведения о константах, используемых для указания типа данных PHP, см. в разделе о PHPTYPE статьи [Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
## <a name="example"></a>Пример  
Следующий пример извлекает строки из таблицы *Production.ProductReview* базы данных AdventureWorks. В каждой возвращаемой строке поле *ReviewDate* извлекается в виде строки, а поле *Comments* —в виде потока. Потоковые данные отображаются с помощью функции [fpassthru](https://php.net/manual/en/function.fpassthru.php) PHP.  
  
В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  
В этом примере при извлечении второго поля *ReviewDate* в виде строки сохраняется значение типа данных DATETIME SQL Server с точностью до миллисекунды. По умолчанию тип данных DATETIME SQL Server извлекается в виде объекта DateTime PHP, в котором точность до миллисекунды теряется.  
  
Извлечение четвертого поля (*Comments*) в виде потока осуществляется для демонстрационных целей. По умолчанию тип данных nvarchar(3850) SQL Server извлекается в виде строки, что вполне приемлемо в большинстве ситуаций.  
  
> [!NOTE]  
> Функция [sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md) предоставляет способ получения сведений о поле, включая информацию о типе, перед выполнением запроса.  
  
## <a name="see-also"></a>См. также:  
[Извлечение данных](../../connect/php/retrieving-data.md)

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)

[Практическое руководство. Извлечение параметров вывода с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)

[Практическое руководство. Извлечение параметров ввода и вывода с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver.md)  
  
