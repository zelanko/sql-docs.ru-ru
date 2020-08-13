---
title: sqlsrv_fetch_array
description: Справочник по API для функции sqlsrv_fetch_array в драйвере PHP для SQL Server.
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_fetch_array
apitype: NA
helpviewer_keywords:
- sqlsrv_fetch_array
- retrieving data, as an array
- API Reference, sqlsrv_fetch_array
ms.assetid: 69270b9e-0791-42f4-856d-412da39dea63
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b3c3f296d0fd2ae05c3b88a08428c3ddb8a5f2c
ms.sourcegitcommit: cb620c77fe6bdefb975968837706750c31048d46
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2020
ms.locfileid: "86391809"
---
# <a name="sqlsrv_fetch_array"></a>sqlsrv_fetch_array
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает следующую строку данных в виде массива с числовым индексом и (или) ассоциативного массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_fetch_array( resource $stmt[, int $fetchType [, row[, ]offset]])  
```  
  
#### <a name="parameters"></a>Параметры  
*$stmt*: ресурс инструкции, соответствующий выполненной инструкции.  
  
*$fetchType* [необязательно]: предопределенная константа. Этот параметр может принимать одно из значений, содержащихся в следующей таблице.  
  
|Значение|Описание|  
|---------|---------------|  
|SQLSRV_FETCH_NUMERIC|Следующая строка данных возвращается в виде числового массива.|  
|SQLSRV_FETCH_ASSOC|Следующая строка данных возвращается в виде ассоциативного массива. Ключами массива являются имена столбцов в результирующем наборе.|  
|SQLSRV_FETCH_BOTH|Следующая строка данных возвращается в виде как числового массива, так и ассоциативного массива. Это значение по умолчанию.|  
  
*row* [необязательно]: добавлено в версии 1.1. Одно из следующих значений, определяющее строку, к которой требуется получить доступ в результирующем наборе, использующем прокручиваемый курсор. (Если вы указываете *row*, необходимо явно указать *fetchtype*, даже если вы используете значение по умолчанию.)  
  
-   SQLSRV_SCROLL_NEXT  
-   SQLSRV_SCROLL_PRIOR  
-   SQLSRV_SCROLL_FIRST  
-   SQLSRV_SCROLL_LAST  
-   SQLSRV_SCROLL_ABSOLUTE  
-   SQLSRV_SCROLL_RELATIVE  
  
Дополнительные сведения об этих значениях см. в статье [Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md). Поддержка прокручиваемого курсора была добавлена в версии 1.1 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
*offset* [необязательно]: используется в сочетании с SQLSRV_SCROLL_ABSOLUTE и SQLSRV_SCROLL_RELATIVE для определения извлекаемой строки. Первой записью в результирующем наборе является 0.  
  
## <a name="return-value"></a>Возвращаемое значение  
Если извлечена строка данных, возвращается **массив** . Если больше нет строк для извлечения, возвращается значение **null** . Если произошла ошибка, возвращается значение **false** .  
  
В зависимости от значения параметра *$fetchType* , возвращаемый **массив** может быть **массивом**с числовым индексом и (или) ассоциативным **массивом**. По умолчанию возвращается **массив** с числовыми и ассоциативными ключами. Для значения в возвращенном массиве используется тип данных PHP по умолчанию. Дополнительные сведения о типах данных PHP по умолчанию см. в статье [Default PHP Data Types](../../connect/php/default-php-data-types.md).  
  
## <a name="remarks"></a>Remarks  
Если возвращается столбец без имени, то ассоциативным ключом для данного элемента массива будет пустая строка (""). Например, рассмотрим эту инструкцию Transact-SQL, которая вставляет значение в таблицу базы данных и извлекает созданный сервером первичный ключ:  
  
```
INSERT INTO Production.ProductPhoto (LargePhoto) VALUES (?);  
SELECT SCOPE_IDENTITY()
```
  
Если результирующий набор, возвращаемый частью `SELECT SCOPE_IDENTITY()` этой инструкции, извлекается в виде ассоциативного массива, ключом для возвращенного значения будет пустая строка (""), так как возвращаемый столбец не имеет имени. Чтобы избежать этого, можно извлечь результат в виде числового массива или указать имя возвращаемого столбца в инструкции Transact-SQL. Ниже приведена одна из инструкций для указания имени столбца в Transact-SQL.  
  
```
SELECT SCOPE_IDENTITY() AS PictureID
```
  
Если результирующий набор содержит несколько столбцов без имени, значение последнего столбца без имени присваивается ключу пустой строки ("").  
  
## <a name="example"></a>Пример  
Следующий пример извлекает каждую строку результирующего набора в виде ассоциативного **массива**. В примере предполагается, что SQL Server и база данных [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
  
/* Set up and execute the query. */  
$tsql = "SELECT FirstName, LastName  
         FROM Person.Contact  
         WHERE LastName='Alan'";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false)  
{  
     echo "Error in query preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve each row as an associative array and display the results.*/  
while( $row = sqlsrv_fetch_array( $stmt, SQLSRV_FETCH_ASSOC))  
{  
      echo $row['LastName'].", ".$row['FirstName']."\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Пример  
Следующий пример извлекает каждую строку результирующего набора в виде массива с числовым индексом.  
  
Пример извлекает из таблицы *Purchasing.PurchaseOrderDetail* базы данных AdventureWorks сведения о продуктах с определенной датой и запасом (*StockQty*) меньше указанного значения.  
  
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
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Define the query. */  
$tsql = "SELECT ProductID,  
                UnitPrice,  
                StockedQty   
         FROM Purchasing.PurchaseOrderDetail  
         WHERE StockedQty < 3   
         AND DueDate='2002-01-29'";  
  
/* Execute the query. */  
$stmt = sqlsrv_query( $conn, $tsql);  
if ( $stmt )  
{  
     echo "Statement executed.\n";  
}   
else   
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Iterate through the result set printing a row of data upon each  
iteration.*/  
while( $row = sqlsrv_fetch_array( $stmt, SQLSRV_FETCH_NUMERIC))  
{  
     echo "ProdID: ".$row[0]."\n";  
     echo "UnitPrice: ".$row[1]."\n";  
     echo "StockedQty: ".$row[2]."\n";  
     echo "-----------------\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
Функция **sqlsrv_fetch_array** всегда возвращает данные в соответствии с [Default PHP Data Types](../../connect/php/default-php-data-types.md). Дополнительные сведения об указании типа данных PHP см. в статье [Практическое руководство. Указание типов данных PHP](../../connect/php/how-to-specify-php-data-types.md).  
  
Если извлекается поле без имени, то ассоциативным ключом для данного элемента массива будет пустая строка (""). Дополнительные сведения см. в статье [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md).  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Извлечение данных](../../connect/php/retrieving-data.md)

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)

[Руководство по программированию драйверов Microsoft для PHP для SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  
