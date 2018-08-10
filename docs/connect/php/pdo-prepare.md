---
title: PDO::Prepare | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8b16fdc-c748-49be-acf2-a6ac7432d16b
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ac27dbcc186eff263803da714032d532c95d3b4
ms.sourcegitcommit: f9d4f9c1815cff1689a68debdccff5e7ff97ccaf
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/31/2018
ms.locfileid: "39367706"
---
# <a name="pdoprepare"></a>PDO::prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Подготавливает инструкцию для выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PDOStatement PDO::prepare ( $statement [, array(key_pair)] )  
```  
  
#### <a name="parameters"></a>Параметры  
$*statement*: строка, содержащая инструкцию SQL.  
  
*key_pair*: массив, содержащий имя и значение атрибута. Дополнительные сведения см. в разделе «Примечания».  
  
## <a name="return-value"></a>Возвращаемое значение  
В случае успеха возвращает объект PDOStatement. В случае сбоя возвращает объект PDOException или значение false в зависимости от значения PDO::ATTR_ERRMODE.  
  
## <a name="remarks"></a>Remarks  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Не оценивает подготовленную инструкцию до самого выполнения.  
  
Возможные значения *key_pair* перечислены в следующей таблице.  
  
|Key|Описание|  
|-------|---------------|  
|PDO::ATTR_CURSOR|Определяет поведение курсора. Значение по умолчанию — PDO::CURSOR_FWDONLY. PDO::CURSOR_SCROLL является статическим курсором.<br /><br />Например, `array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY )`.<br /><br />При использовании PDO::CURSOR_SCROLL можно использовать описанный ниже PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE.<br /><br />Дополнительные сведения о результирующих наборах и курсорах в драйвере PDO_SQLSRV см. в статье [Типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::ATTR_EMULATE_PREPARES|По умолчанию этот атрибут имеет значение false, который может быть изменен в этом `PDO::ATTR_EMULATE_PREPARES => true`. См. в разделе [эмуляции Подготовка](#emulate-prepare) подробные сведения и пример.|
|PDO::SQLSRV_ATTR_ENCODING|PDO::SQLSRV_ENCODING_UTF8 (по умолчанию)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|При значении true задает выполнение прямого запроса. Значение false указывает на выполнение подготовленной инструкции. Дополнительные сведения о PDO::SQLSRV_ATTR_DIRECT_QUERY см. в статье [Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Дополнительные сведения см. в статье [PDO::setAttribute](../../connect/php/pdo-setattribute.md).|  
  
При использовании PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL можно использовать PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE. Например,  
  
```  
array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_DYNAMIC));  
```  
  
Следующая таблица содержит возможные значения для PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE.  
  
|Значение|Описание|  
|---------|---------------|  
|PDO::SQLSRV_CURSOR_BUFFERED|Создает статический клиентский курсор (буферизованный). Дополнительные сведения о клиентских курсорах см. в статье [Типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_CURSOR_DYNAMIC|Создает серверный (без буферизации) динамический курсор, который позволяет осуществлять доступ к строкам в любом порядке и будет отражать изменения в базе данных.|  
|PDO::SQLSRV_CURSOR_KEYSET_DRIVEN|Создает серверный курсор набора ключей. Курсор набора ключей не обновляет количество строк, если строка удаляется из таблицы (удаленная строка возвращается без значений).|  
|PDO::SQLSRV_CURSOR_STATIC|Создает серверный статический курсор, который позволяет осуществлять доступ к строкам в любом порядке, но не будет отражать изменения в базе данных.<br /><br />PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL подразумевает PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_STATIC.|  
  
Объект PDOStatement можно закрыть, присвоив ему значение NULL.  
  
## <a name="example"></a>Пример  
Этот пример показывает, как использовать метод PDO::prepare с маркерами параметров и курсором последовательного доступа.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table1(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
echo "\n";  
  
$query = "insert into Table1(col1, col2) values(:col1, :col2)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( ':col1' => $col1, ':col2' => $col2 ) );  
print $stmt->rowCount();  
  
$stmt = null  
?>  
```  

## <a name="example"></a>Пример  
Этот пример показывает, как использовать метод PDO::prepare с клиентским курсором. Пример использования серверного курсора см. в статье [Типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  

<a name="emulate-prepare" />

## <a name="example"></a>Пример 

В этом примере показано, как использовать метод PDO::prepare с `PDO::ATTR_EMULATE_PREPARES`, имеющим значение "true" (истина). 

```
<?php
$serverName = "yourservername";
$username = "yourusername";
$password = "yourpassword";
$database = "tempdb";
$conn = new PDO("sqlsrv:server = $serverName; Database = $database", $username, $password);

$pdo_options = array();
$pdo_options[PDO::ATTR_EMULATE_PREPARES] = true;
$pdo_options[PDO::SQLSRV_ATTR_ENCODING] = PDO::SQLSRV_ENCODING_UTF8;

$stmt = $conn->prepare("CREATE TABLE TEST([id] [int] IDENTITY(1,1) NOT NULL, 
                                          [name] nvarchar(max))", 
                                          $pdo_options);
$stmt->execute();

$prefix = '가각';
$name = '가각ácasa';
$name2 = '가각sample2';

$stmt = $conn->prepare("INSERT INTO TEST(name) VALUES(:p0)", $pdo_options);
$stmt->execute(['p0' => $name]);
unset($stmt);

$stmt = $conn->prepare("SELECT * FROM TEST WHERE NAME LIKE :p0", $pdo_options);
$stmt->execute(['p0' => "$prefix%"]);
foreach ($stmt as $row) {
    echo "\n" . 'FOUND: ' . $row['name'];
}

unset($stmt);
unset($conn);
?>
```

Драйвер PDO_SQLSRV выполняет внутреннюю замену все заполнители с параметрами, привязанных к [PDOStatement::bindParam()](../../connect/php/pdostatement-bindparam.md). Таким образом строка запроса SQL с заполнителями не отправляется на сервер. Рассмотрим следующий пример

```
$statement = $PDO->prepare("INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)");
$statement->bindParam(:cus_name, "Cardinal");
$statement->bindParam(:con_name, "Tom B. Erichsen");
$statement->execute();
```

С помощью `PDO::ATTR_EMULATE_PREPARES` имеет значение false (по умолчанию случай), данные, отправляемые в базу данных:

```
"INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)"
Information on :cus_name parameter
Information on :con_name parameter
```

Сервер выполнит запрос, с помощью компонента параметризованного запроса для привязки параметров. С другой стороны, `PDO::ATTR_EMULATE_PREPARES` задано значение true, запроса, отправленного на сервер, по сути является:

```
"INSERT into Customers (CustomerName, ContactName) VALUES ('Cardinal', 'Tom B. Erichsen')"
```

Параметр `PDO::ATTR_EMULATE_PREPARES` для true может обойти некоторые ограничения в SQL Server. Например SQL Server не поддерживает именованные или позиционные параметры в некоторых предложениях Transact-SQL. Кроме того SQL Server имеет ограничение в 2100 параметров привязки.

> [!NOTE]
> С помощью emulate подготавливает задано значение true, обеспечения безопасности параметризованных запросов не действует. Следовательно, приложение должно проверить, что привязанные к параметрам данные не содержат вредоносный код Transact-SQL.

### <a name="encoding"></a>Кодировка

Если пользователь хочет привязать параметры с разными кодировками (например, UTF-8 или двоичный файл), пользователь должен четко указать кодировка в скрипте PHP.

Драйвер PDO_SQLSRV сначала проверяет, кодировку, заданную в `PDO::bindParam()` (например, `$statement->bindParam(:cus_name, "Cardinal", PDO::PARAM_STR, 10, PDO::SQLSRV_ENCODING_UTF8)`). 

Если не найден, драйвер проверяет Если какого-либо кодирования задается в `PDO::prepare()` или `PDOStatement::setAttribute()`. В противном случае драйвер будет использовать кодировку, заданную в `PDO::__construct()` или `PDO::setAttribute()`.

### <a name="limitations"></a>Ограничения

Как вы видите, привязка выполняется внутренне драйвером. Допустимый запрос отправляется на сервер для выполнения без какой-либо параметр. Результат по сравнению с в обычном случае, некоторые ограничения при включенной функции параметризованного запроса не используется.

- Он не работает для параметров, которые связываются как `PDO::PARAM_INPUT_OUTPUT`.
    - При указании пользователем `PDO::PARAM_INPUT_OUTPUT` в `PDO::bindParam()`, создается исключение PDO.
- Он не работает для параметров, которые связываются как выходные параметры.
    - Когда пользователь создает подготовленной инструкции с заполнителями, предназначены для выходных параметров (то есть наличие знака равенства сразу же после заполнителя, такие как `SELECT ? = COUNT(*) FROM Table1`), создается исключение PDO.
    - Когда подготовленной инструкции вызывает хранимую процедуру с заполнителем как аргумент для выходного параметра, исключение не создается, так как драйвер не может обнаружить выходной параметр. Тем не менее переменную, которая предоставляет пользователю для параметра вывода не изменится.
- Повторяющиеся заполнители для двоичного параметра кодировке не будет работать

## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
