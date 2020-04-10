---
title: sqlsrv_send_stream_data | Документация Майкрософт
ms.custom: ''
ms.date: 02/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_send_stream_data
apitype: NA
helpviewer_keywords:
- sqlsrv_send_stream_data
- API Reference, sqlsrv_send_stream_data
- streaming data
ms.assetid: 826c2d45-694f-42b8-b12b-cd4523a31883
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe3207810e44929b392a385f481dbb52da57ae6a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927226"
---
# <a name="sqlsrv_send_stream_data"></a>sqlsrv_send_stream_data
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Отправляет данные из потоков параметров на сервер. С каждым вызовом **sqlsrv_send_stream_data** отправляется до 8 килобайт (8 КБ) данных.  
  
> [!NOTE]  
> По умолчанию все потоковые данные передаются на сервер при выполнении запроса. Если это поведение по умолчанию не изменялось, использовать **sqlsrv_send_stream_data** для отправки потоковых данных на сервер не нужно. Сведения об изменении такого поведения по умолчанию см. разделе "Параметры" статьи [sqlsrv_query](../../connect/php/sqlsrv-query.md) или [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_send_stream_data( resource $stmt)  
```  
  
#### <a name="parameters"></a>Параметры  
*$stmt*: ресурс инструкции, соответствующий выполненной инструкции.  
  
## <a name="return-value"></a>Возвращаемое значение  
Логическое значение: **true** при наличии дополнительных данных для отправки. В противном случае — **false**.  
  
## <a name="example"></a>Пример  
Следующий пример открывает обзор продукта в качестве потока и отправляет его на сервер. Поведение по умолчанию, заключающееся в отправке всех потоковых данных во время выполнения, отключено. В примере предполагается, что SQL Server и базы данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if ($conn === false) {
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Define the query. */  
$tsql = "UPDATE Production.ProductReview   
         SET Comments = (?)   
         WHERE ProductReviewID = 3";  
  
/* Open parameter data as a stream and put it in the $params array. */
$data = 'Insert any lengthy comment here.';
$comment = fopen('data:text/plain,'.urlencode($data), 'r');
$params = array(&$comment);
  
/* Prepare the statement. Use the $options array to turn off the  
default behavior, which is to send all stream data at the time of query  
execution. */  
$options = array("SendStreamParamsAtExec"=>0);  
$stmt = sqlsrv_prepare($conn, $tsql, $params, $options);
  
/* Execute the statement. */  
sqlsrv_execute( $stmt);  
  
/* Send up to 8K of parameter data to the server with each call to  
sqlsrv_send_stream_data. Count the calls. */  
$i = 1;  
while (sqlsrv_send_stream_data($stmt)) {
      echo "$i call(s) made.\n";  
      $i++;  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Обновление данных (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
  
