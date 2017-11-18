---
title: "sqlsrv_fetch | Документы Microsoft"
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
apiname:
- sqlsrv_fetch
apitype: NA
helpviewer_keywords:
- sqlsrv_fetch
- API Reference, sqlsrv_fetch
- retrieving data, as a single field
ms.assetid: a5a640a1-6e7d-452e-8b66-850a4dc2ce89
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 81d325d8a1546bc7169deff6874341385a1b527a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvfetch"></a>sqlsrv_fetch
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Делает следующую строку результирующего набора доступной для чтения. Используйте [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) для чтения полей строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_fetch( resource $stmt[, row[, ]offset])  
```  
  
#### <a name="parameters"></a>Параметры  
*$stmt*: ресурс инструкции, соответствующий выполненной инструкции.  
  
> [!NOTE]  
> Перед извлечением результатов необходимо выполнить инструкцию. Сведения о выполнении инструкции см. в статьях [sqlsrv_query](../../connect/php/sqlsrv-query.md) и [sqlsrv_execute](../../connect/php/sqlsrv-execute.md).  
  
*Строка* [необязательно]: одно из следующих значений, определяющее строку, чтобы получить доступ в результирующем наборе, использующем Прокручиваемый курсор:  
  
-   SQLSRV_SCROLL_NEXT  
  
-   SQLSRV_SCROLL_PRIOR  
  
-   SQLSRV_SCROLL_FIRST  
  
-   SQLSRV_SCROLL_LAST  
  
-   SQLSRV_SCROLL_ABSOLUTE  
  
-   SQLSRV_SCROLL_RELATIVE  
  
Дополнительные сведения об этих значениях см. в статье [Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).  
  
*Смещение* [необязательно]: используется с SQLSRV_SCROLL_ABSOLUTE и SQLSRV_SCROLL_RELATIVE для указания извлекаемой строки. Первой записью в результирующем наборе является 0.  
  
## <a name="return-value"></a>Возвращаемое значение  
Если следующая строка результирующего набора успешно извлечена, возвращается значение **true** . Если других результатов в результирующем наборе нет, возвращается значение **null** . Если произошла ошибка, возвращается значение **false** .  
  
## <a name="example"></a>Пример  
Следующий пример использует **sqlsrv_fetch** для извлечения строки данных, содержащей обзор продукта и имя автора обзора. Для получения данных из результирующего набора, [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) используется. В примере предполагается, что SQL Server и базы данных [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
Comments are of SQL Server type nvarchar. */  
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
if( sqlsrv_fetch( $stmt ) === false)  
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
while( !feof( $stream ))  
{   
    $str = fread( $stream, 10000);  
    echo $str;  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Извлечение данных](../../connect/php/retrieving-data.md)  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
  

