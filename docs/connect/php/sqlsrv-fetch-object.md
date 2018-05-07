---
title: sqlsrv_fetch_object | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_fetch_object
apitype: NA
helpviewer_keywords:
- sqlsrv_fetch_object
- API Reference, sqlsrv_fetch_object
- retrieving data, as an object
ms.assetid: 4ce2df2c-083a-4a4d-a1e2-e866e63707d5
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b753000c255d6c07777c94e8fb61c847ab10d0c5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvfetchobject"></a>sqlsrv_fetch_object
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает следующую строку данных в качестве объекта PHP.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_fetch_object( resource $stmt [, string $className [, array $ctorParams[, row[, ]offset]]])  
```  
  
#### <a name="parameters"></a>Параметры  
*$stmt*: ресурс инструкции, соответствующий выполненной инструкции.  
  
*$className* [необязательно]: строка, задающая имя класса для создания экземпляра. Если значение параметра *$className* не указано, создается экземпляр **stdClass** PHP.  
  
*$ctorParams* [необязательно]: массив, содержащий значения, переданного в конструктор класса, указанного с *$className* параметра. Если конструктор указанного класса принимает значения параметров, при вызове *$ctorParams* object **sqlsrv_fetch_object**.  
  
*Строка* [необязательно]: одно из следующих значений, определяющее строку, чтобы получить доступ в результирующем наборе, использующем Прокручиваемый курсор. (Если *строки* указано, *$className* и *$ctorParams* должно быть указано явным образом, даже если необходимо указать значение null для *$className*и *$ctorParams*.)  
  
-   SQLSRV_SCROLL_NEXT  
  
-   SQLSRV_SCROLL_PRIOR  
  
-   SQLSRV_SCROLL_FIRST  
  
-   SQLSRV_SCROLL_LAST  
  
-   SQLSRV_SCROLL_ABSOLUTE  
  
-   SQLSRV_SCROLL_RELATIVE  
  
Дополнительные сведения об этих значениях см. в статье [Указание типа курсора и выбор строк](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).  
  
*Смещение* [необязательно]: используется с SQLSRV_SCROLL_ABSOLUTE и SQLSRV_SCROLL_RELATIVE для указания извлекаемой строки. Первой записью в результирующем наборе является 0.  
  
## <a name="return-value"></a>Возвращаемое значение  
Объект PHP со свойствами, соответствующими именам полей результирующего набора. Значения свойств заполняются соответствующими значениями полей результирующего набора. Если класс, указанный с помощью необязательного параметра *$className* , не существует или отсутствует активный результирующий набор, сопоставленный с указанной инструкцией, возвращается значение **false** . Если больше нет строк для извлечения, возвращается значение **null** .  
  
Для значения в возвращенном объекте используется тип данных PHP по умолчанию. Дополнительные сведения о типах данных PHP по умолчанию см. в статье [Default PHP Data Types](../../connect/php/default-php-data-types.md).  
  
## <a name="remarks"></a>Замечания  
Если имя класса указано с помощью необязательного параметра *$className* , создается экземпляр объекта этого типа класса. Если класс имеет свойства, имена которых совпадают с именами полей результирующего набора, к свойствам применяются соответствующие значения результирующего набора. Если имя поля результирующего набора не соответствует свойству класса, к объекту добавляется свойство с именем поля результирующего набора, а к этому свойству применяется значение результирующего набора.  
  
При указании класса с помощью параметра *$className* применяются следующие правила:  
  
-   Сравнение осуществляется с учетом регистра. Например, имя свойства CustomerId не соответствует имени поля CustomerID. В этом случае к объекту добавляется свойство CustomerID, а значение поля CustomerID присваивается свойству CustomerID.  
  
-   Сравнение осуществляется независимо от модификаторов доступа. Например, если указанный класс имеет закрытое свойство, имя которого соответствует имени поля результирующего набора, к свойству применяется значение из этого поля результирующего набора.  
  
-   Типы данных свойств класса не учитываются. Если поле "CustomerID" результирующего набора является строкой, а свойство "CustomerID" класса является целым числом, в свойство "CustomerID" записывается строковое значение из результирующего набора.  
  
-   Если указанный класс не существует, функция возвращает значение **false** и добавляет ошибку в коллекцию ошибок. Информацию об извлечении сведений об ошибках см. в статье [sqlsrv_errors](../../connect/php/sqlsrv-errors.md).  
  
Если возвращается поле без имени, **sqlsrv_fetch_object** отменяет значение поля и выдает предупреждение. Например, рассмотрим эту инструкцию Transact-SQL, которая вставляет значение в таблицу базы данных и извлекает созданный сервером первичный ключ:  
  
<pre>INSERT INTO Production.ProductPhoto (LargePhoto) VALUES (?);  
SELECT SCOPE_IDENTITY()</pre>  
  
Если результаты, возвращаемые этим запросом, извлекаются с помощью **sqlsrv_fetch_object**, значение, возвращаемое `SELECT SCOPE_IDENTITY()` , отменяется и выдается предупреждение. Чтобы избежать этого, можно указать имя возвращаемого поля в инструкции Transact-SQL. Ниже приведен один из способов указания имени столбца в Transact-SQL.  
  
`SELECT SCOPE_IDENTITY() AS PictureID`  
  
## <a name="example"></a>Пример  
Следующий пример извлекает каждую строку результирующего набора в виде объекта PHP. Предполагается, что SQL Server и [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) базы данных установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
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
if( $stmt === false )  
{  
     echo "Error in query preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve each row as a PHP object and display the results.*/  
while( $obj = sqlsrv_fetch_object( $stmt))  
{  
      echo $obj->LastName.", ".$obj->FirstName."\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Пример  
Следующий пример извлекает каждую строку результирующего набора в виде экземпляра класса *Product* , определенного в скрипте. В примере извлекаются сведения о продукте из *Purchasing.PurchaseOrderDetail* и *Production.Product* таблиц базы данных AdventureWorks для продуктов, имеющих указанный срок ( *DueDate*) и количество запасов (*StockQty*) меньше указанного значения. В примере представлены некоторые правила, применяемые при указании класса в вызове **sqlsrv_fetch_object**:  
  
-   Переменная *$product* является экземпляром класса *Product* , так как "Product" был указан с параметром *$className* , а класс *Product* существует.  
  
-   Свойство *Name* добавляется в экземпляр *$product* , так как существующее свойство *name* не совпадает.  
  
-   Свойство *Color* добавляется в экземпляр *$product* , так как отсутствует совпадающее свойство.  
  
-   Закрытое свойство *UnitPrice* заполняется значением поля *UnitPrice* .  
  
Предполагается, что SQL Server и [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) базы данных установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
```  
<?php  
/* Define the Product class. */  
class Product  
{  
     /* Constructor */  
     public function Product($ID)  
     {  
          $this->objID = $ID;  
     }  
     public $objID;  
     public $name;  
     public $StockedQty;  
     public $SafetyStockLevel;  
     private $UnitPrice;  
     function getPrice()  
     {  
          return $this->UnitPrice;  
     }  
}  
  
/* Connect to the local server using Windows Authentication, and  
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
$tsql = "SELECT Name,  
                SafetyStockLevel,  
                StockedQty,  
                UnitPrice,  
                Color  
         FROM Purchasing.PurchaseOrderDetail AS pdo  
         JOIN Production.Product AS p  
         ON pdo.ProductID = p.ProductID  
         WHERE pdo.StockedQty < ?  
         AND pdo.DueDate= ?";  
  
/* Set the parameter values. */  
$params = array(3, '2002-01-29');  
  
/* Execute the query. */  
$stmt = sqlsrv_query( $conn, $tsql, $params);  
if ( $stmt )  
{  
     echo "Statement executed.\n";  
}   
else   
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Iterate through the result set, printing a row of data upon each  
 iteration. Note the following:  
     1) $product is an instance of the Product class.  
     2) The $ctorParams parameter is required in the call to  
        sqlsrv_fetch_object, because the Product class constructor is  
        explicity defined and requires parameter values.  
     3) The "Name" property is added to the $product instance because  
        the existing "name" property does not match.  
     4) The "Color" property is added to the $product instance  
        because there is no matching property.  
     5) The private property "UnitPrice" is populated with the value  
        of the "UnitPrice" field.*/  
$i=0; //Used as the $objID in the Product class constructor.  
while( $product = sqlsrv_fetch_object( $stmt, "Product", array($i)))  
{  
     echo "Object ID: ".$product->objID."\n";  
     echo "Product Name: ".$product->Name."\n";  
     echo "Stocked Qty: ".$product->StockedQty."\n";  
     echo "Safety Stock Level: ".$product->SafetyStockLevel."\n";  
     echo "Product Color: ".$product->Color."\n";  
     echo "Unit Price: ".$product->getPrice()."\n";  
     echo "-----------------\n";  
     $i++;  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
Переменная **sqlsrv_fetch_object** всегда возвращает данные в соответствии с [Default PHP Data Types](../../connect/php/default-php-data-types.md). (Дополнительные сведения об указании типа данных PHP см. в статье [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).)  
  
Если возвращается поле без имени, **sqlsrv_fetch_object** отменяет значение поля и выдает предупреждение. Например, рассмотрим эту инструкцию Transact-SQL, которая вставляет значение в таблицу базы данных и извлекает созданный сервером первичный ключ:  
  
<pre>INSERT INTO Production.ProductPhoto (LargePhoto) VALUES (?);  
SELECT SCOPE_IDENTITY()</pre>  
  
Если результаты, возвращаемые этим запросом, извлекаются с помощью **sqlsrv_fetch_object**, значение, возвращаемое `SELECT SCOPE_IDENTITY()` , отменяется и выдается предупреждение. Чтобы избежать этого, можно указать имя возвращаемого поля в инструкции Transact-SQL. Ниже приведен один из способов указания имени столбца в Transact-SQL.  
  
`SELECT SCOPE_IDENTITY() AS PictureID`  
  
## <a name="see-also"></a>См. также  
[Извлечение данных](../../connect/php/retrieving-data.md)  

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  

[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  
