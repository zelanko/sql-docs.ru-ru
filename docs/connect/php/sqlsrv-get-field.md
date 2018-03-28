---
title: sqlsrv_get_field | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- sqlsrv_get_field
apitype: NA
helpviewer_keywords:
- sqlsrv_get_field
- API Reference, sqlsrv_get_field
- retrieving data, as a single field
ms.assetid: fa17cc56-fb38-433b-a40d-65642f04dc23
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ff8f669772a8bd2ef0920992e9375c8795a7467b
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="sqlsrvgetfield"></a>sqlsrv_get_field
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает данные из указанного поля текущей строки. Доступ к данным полей должен осуществляться в определенном порядке. Например, данные из первого поля становятся недоступными после доступа к данным из второго поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_get_field( resource $stmt, int $fieldIndex [, int $getAsType])  
```  
  
#### <a name="parameters"></a>Параметры  
*$stmt*: ресурс инструкции, соответствующий выполненной инструкции.  
  
*$fieldIndex*: Индекс поля для извлечения. Индексы отсчитываются с нуля.  
  
*$getAsType* [необязательно]: A **SQLSRV** константы (**SQLSRV_PHPTYPE_\***), определяющая тип данных PHP для возвращаемых данных. Сведения о поддерживаемых типах данных см. в разделе [константы &#40;драйверы Майкрософт для PHP для SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md). Если тип возвращаемого значения не указан, возвращается тип PHP по умолчанию. Дополнительные сведения о типах PHP см. в статье [Default PHP Data Types](../../connect/php/default-php-data-types.md). Дополнительные сведения об указании типов данных PHP см. в статье [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
Данные поля. Можно указать тип данных PHP для возвращаемых данных с помощью параметра *$getAsType* . Если тип возвращаемых данных не указан, возвращается тип данных PHP по умолчанию. Дополнительные сведения о типах PHP см. в статье [Default PHP Data Types](../../connect/php/default-php-data-types.md). Дополнительные сведения об указании типов данных PHP см. в статье [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
## <a name="remarks"></a>Remarks  
Сочетание **sqlsrv_fetch** и **sqlsrv_get_field** предоставляет прямой доступ к данным.  
  
Сочетание **sqlsrv_fetch**/**sqlsrv_get_field** загружает только одно поле результирующего набора строк в память сценария и позволяет PHP тип возвращаемого значения. (Сведения об указании типов возвращаемых данных PHP см. в разделе [как: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).) Это сочетание функций также позволяет извлекать данные в виде потока. (Сведения о получении данных в виде потока см. в разделе [извлечение данных в виде потока с помощью драйвера SQLSRV](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md).)  
  
## <a name="example"></a>Пример  
Следующий пример извлекает строку данных, содержащую обзор продукта и имя автора обзора. Для получения данных из результирующего набора используется **sqlsrv_get_field** . Предполагается, что SQL Server и [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) базы данных установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  
/* Set up and execute the query. Note that both ReviewerName and  
Comments are of the SQL Server nvarchar type. */  
$tsql = "SELECT ReviewerName, Comments   
         FROM Production.ProductReview  
         WHERE ProductReviewID=1";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in statement preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Make the first row of the result set available for reading. */  
if( sqlsrv_fetch( $stmt ) === false )  
{  
     echo "Error in retrieving row.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Note: Fields must be accessed in order.  
Get the first field of the row. Note that no return type is  
specified. Data will be returned as a string, the default for  
a field of type nvarchar.*/  
$name = sqlsrv_get_field( $stmt, 0);  
echo "$name: ";  
  
/*Get the second field of the row as a stream.  
Because the default return type for a nvarchar field is a  
string, the return type must be specified as a stream. */  
$stream = sqlsrv_get_field( $stmt, 1,   
                            SQLSRV_PHPTYPE_STREAM( SQLSRV_ENC_CHAR));  
while( !feof( $stream))  
{   
    $str = fread( $stream, 10000);  
    echo $str;  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Извлечение данных](../../connect/php/retrieving-data.md)  

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
  
