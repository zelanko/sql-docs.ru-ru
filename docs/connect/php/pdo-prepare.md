---
title: PDO::prepare | Документация Майкрософт
ms.custom: ''
ms.date: 04/25/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a8b16fdc-c748-49be-acf2-a6ac7432d16b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7eac30ff1391ba5c56099cf7c59fa89b1368f115
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105878"
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
В случае успеха возвращает объект PDOStatement. В случае сбоя возвращает объект PDOException или значение false в зависимости от значения `PDO::ATTR_ERRMODE`.

## <a name="remarks"></a>Remarks
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Не оценивает подготовленную инструкцию до самого выполнения.

Возможные значения *key_pair* перечислены в следующей таблице.

|Key|Описание|
|-------|---------------|
|PDO::ATTR_CURSOR|Определяет поведение курсора. По умолчанию используется `PDO::CURSOR_FWDONLY`, непрокручиваемый однонаправленный курсор. `PDO::CURSOR_SCROLL` является прокручиваемым курсором.<br /><br />Например, `array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY )`.<br /><br />Если задано значение `PDO::CURSOR_SCROLL`, вы можете с помощью `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE` установить тип прокручиваемого курсора, который описан ниже.<br /><br />Дополнительные сведения о результирующих наборах и курсорах в драйвере PDO_SQLSRV см. в статье [Типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|
|PDO::ATTR_EMULATE_PREPARES|По умолчанию этот атрибут имеет значение false, но вы можете изменить его с помощью `PDO::ATTR_EMULATE_PREPARES => true`. В статье [о подготовке эмуляции](#emulate-prepare) приводятся подробные сведения и пример.|
|PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE|Задает тип прокручиваемого курсора. Действует, только если `PDO::ATTR_CURSOR` имеет значение `PDO::CURSOR_SCROLL`. Ниже перечислены значения, которые может принимать этот атрибут.|
|PDO::SQLSRV_ATTR_DECIMAL_PLACES|Указывает число десятичных знаков при форматировании полученных денежных значений. Этот параметр работает только в том случае, если `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` имеет значение true. См. подробнее о [форматировании десятичных строк и денежных значений (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).|
|PDO::SQLSRV_ATTR_DIRECT_QUERY|При значении true задает выполнение прямого запроса. Значение false указывает на выполнение подготовленной инструкции. Дополнительные сведения о `PDO::SQLSRV_ATTR_DIRECT_QUERY` см. в статье [Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|
|PDO::SQLSRV_ATTR_ENCODING|PDO::SQLSRV_ENCODING_UTF8 (по умолчанию)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|
|PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE|Указывает, нужно ли извлекать типы даты и времени в виде объектов [PHP DateTime](http://php.net/manual/en/class.datetime.php). См. подробнее об [извлечении типов даты и времени в виде объектов PHP DateTime с помощью драйвера PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|Обрабатывает выборку числовых значений из столбцов с числовыми типами SQL. Дополнительные сведения см. в статье [PDO::setAttribute](../../connect/php/pdo-setattribute.md).|
|PDO::SQLSRV_ATTR_FORMAT_DECIMALS|Указывает, нужно ли при необходимости добавлять начальные нули к десятичным строкам. Если задан этот параметр, включается параметр `PDO::SQLSRV_ATTR_DECIMAL_PLACES` для форматирования денежных типов. См. подробнее о [форматировании десятичных строк и денежных значений (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).| 
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Дополнительные сведения см. в статье [PDO::setAttribute](../../connect/php/pdo-setattribute.md).|

При использовании `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL` вы можете применить `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE` для указания типа курсора. Например, передайте следующий массив в PDO::prepare, чтобы задать динамический курсор:
```
array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_DYNAMIC));
```
В следующей таблице приводятся возможные значения `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE`. Дополнительные сведения о прокручиваемых курсорах см. в статье [Типы курсоров (драйвер PDO_SQLSRV)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).

|Значение|Описание|
|---------|---------------|
|PDO::SQLSRV_CURSOR_BUFFERED|Создает клиентский (буферизованный) статический курсор, который помещает результирующий набор в память на клиентском компьютере.|
|PDO::SQLSRV_CURSOR_DYNAMIC|Создает серверный (без буферизации) динамический курсор, который позволяет осуществлять доступ к строкам в любом порядке и будет отражать изменения в базе данных.|
|PDO::SQLSRV_CURSOR_KEYSET|Создает серверный курсор набора ключей. Курсор набора ключей не обновляет количество строк, если строка удаляется из таблицы (удаленная строка возвращается без значений).|
|PDO::SQLSRV_CURSOR_STATIC|Создает серверный статический курсор, который позволяет осуществлять доступ к строкам в любом порядке, но не будет отражать изменения в базе данных.<br /><br />`PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL` подразумевает `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_STATIC`.|

Объект PDOStatement можно закрыть, вызвав `unset`.
```
unset($stmt);
```

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

unset($stmt);
?>
```

## <a name="example"></a>Пример
Этот пример показывает, как использовать метод PDO::prepare с маркерами параметров и статическим курсором на стороне сервера. Пример использования курсора на стороне клиента см. в статье [Типы курсоров (драйвера PDO_SQLSRV)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).

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

В этом примере показано, как использовать PDO::prepare с `PDO::ATTR_EMULATE_PREPARES`, имеющим значение true.

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

Драйвер PDO_SQLSRV выполняет внутреннюю замену всех заполнителей на параметры, которые привязаны к ним с помощью [PDOStatement::bindParam()](../../connect/php/pdostatement-bindparam.md). Таким образом, на сервер отправляется строка запроса SQL уже без заполнителей. Рассмотрим следующий запрос:

```
$statement = $PDO->prepare("INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)");
$statement->bindParam(:cus_name, "Cardinal");
$statement->bindParam(:con_name, "Tom B. Erichsen");
$statement->execute();
```

Когда `PDO::ATTR_EMULATE_PREPARES` имеет значение false (вариант по умолчанию), в базу данных отправляются следующие данные:

```
"INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)"
Information on :cus_name parameter
Information on :con_name parameter
```

Сервер выполнит этот запрос, применяя функцию параметризованного запроса для привязки параметров. Если же `PDO::ATTR_EMULATE_PREPARES` имеет значение true, на сервер по сути отправляется такой запрос:

```
"INSERT into Customers (CustomerName, ContactName) VALUES ('Cardinal', 'Tom B. Erichsen')"
```

Присвоив параметру `PDO::ATTR_EMULATE_PREPARES` значение true, вы можете обойти некоторые ограничения SQL Server. Например, SQL Server не поддерживает именованные или позиционные параметры в некоторых предложениях Transact-SQL. Кроме того, SQL Server имеет ограничение в 2100 параметров привязки.

> [!NOTE]
> Если параметр подготовки эмуляции имеет значение true, механизм защиты параметризованных запросов не применяется. Следовательно, приложение должно проверить, что привязанные к параметрам данные не содержат вредоносный код Transact-SQL.

### <a name="encoding"></a>Кодировка

Если пользователь хочет привязать параметры с другими кодировками (например UTF-8 или двоичный файл), пользователь должен явно указать кодировку в скрипте PHP.

Драйвер PDO_SQLSRV сначала проверяет кодировку, которая задана в `PDO::bindParam()` (например `$statement->bindParam(:cus_name, "Cardinal", PDO::PARAM_STR, 10, PDO::SQLSRV_ENCODING_UTF8)`).

Если ее там нет, драйвер проверяет наличие кодировки в `PDO::prepare()` или `PDOStatement::setAttribute()`. В противном случае драйвер будет использовать кодировку, заданную в `PDO::__construct()` или `PDO::setAttribute()`.

### <a name="limitations"></a>Ограничения

Как вы видите, привязка выполняется внутри драйвера. Запрос отправляется на сервер для выполнения уже без параметров. По сравнению с обычным режимом, возникает ряд ограничений при отключении функции параметризованного запроса.

- Он не работает для параметров, привязка которых настроена как `PDO::PARAM_INPUT_OUTPUT`.
    - Если пользователь указал `PDO::PARAM_INPUT_OUTPUT` в `PDO::bindParam()`, создается исключение PDO.
- Он не работает для параметров, привязка которых настроена как внешний параметр.
    - Когда пользователь создает подготовленную инструкцию с заполнителями для выходных параметров (то есть со знаком равенства сразу же после заполнителя, например `SELECT ? = COUNT(*) FROM Table1`), создается исключение PDO.
    - Если подготовленная инструкция вызывает хранимую процедуру с заполнителем в качестве аргумента для выходного параметра, исключение не создается, так как драйвер не может обнаружить такой выходной параметр. Но при этом переменная, предоставленная пользователем для выходного параметра, не изменится.
- Повторяющиеся заполнители для параметра в двоичной кодировке работать не будут.

## <a name="see-also"></a>См. также:
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)

