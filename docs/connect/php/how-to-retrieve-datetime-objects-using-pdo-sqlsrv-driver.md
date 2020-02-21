---
title: Руководство. Извлечение типов даты и времени в виде объектов даты и времени PHP с помощью драйвера PDO_SQLSRV | Документация Майкрософт
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as datetime objects
author: yitam
ms.author: v-yitam
manager: v-mabarw
ms.openlocfilehash: 165e91cee3b0b4592f9b746f8b35b46bc73bce50
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "68264569"
---
# <a name="how-to-retrieve-date-and-time-types-as-php-datetime-objects-using-the-pdo_sqlsrv-driver"></a>Руководство. Извлечение типов даты и времени в виде объектов даты и времени PHP с помощью драйвера PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта функция, добавленная в версии 5.6.0, работает только при использовании драйвера PDO_SQLSRV для [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].

### <a name="to-retrieve-date-and-time-types-as-datetime-objects"></a>Порядок извлечения типов даты и времени в виде объектов DateTime

При использовании PDO_SQLSRV типы даты и времени (**smalldatetime**, **datetime**, **date**, **time**, **datetime2** и **datetimeoffset**) по умолчанию возвращаются в виде строк. Ни PDO::ATTR_STRINGIFY_FETCHES, ни атрибут PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE не оказывает никакого влияния. Чтобы получить типы даты и времени в виде объектов [PHP DateTime](http://php.net/manual/en/class.datetime.php), установите атрибут connection или statement на `PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE` **true** (по умолчанию **false**).

> [!NOTE]
> Эти атрибуты connection или statement применяются только к обычной выборке типов даты и времени, так как объекты DateTime нельзя указать в качестве параметров вывода.

## <a name="example---use-the-connection-attribute"></a>Пример. Использование атрибута connection
В следующих примерах не выполняется проверка ошибок для ясности. В этом примере показано, как задать атрибут connection.

```php
<?php
$server = 'myserver';
$databaseName = 'mydatabase';
$username = 'myusername';
$passwd = 'mypasword';
$tableName = 'mytable';

$conn = new PDO("sqlsrv:Server = $server; Database = $databaseName", $username, $passwd);

// To set the connection attribute
$conn->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
$query = "SELECT DateTimeCol FROM $tableName";
$stmt = $conn->prepare($query);
$stmt->execute();

// Expect a DateTimeCol value as a PHP DateTime type
$row = $stmt->fetch(PDO::FETCH_ASSOC);
var_dump($row);

unset($stmt);
unset($conn);
?>
```

## <a name="example---use-the-statement-attribute"></a>Пример. Использование атрибута statement
В этом примере показано, как задать атрибут statement.

```php
<?php
$database = "test";
$server = "(local)";
$conn = new PDO("sqlsrv:server = $server; Database = $database", "", "");
$query = "SELECT DateTimeCol FROM myTable";
$stmt = $conn->prepare($query);
$stmt->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
$stmt->execute();

// Expect a DateTimeCol value as a PHP DateTime type
$row = $stmt->fetch(PDO::FETCH_NUM);
var_dump($row);

unset($stmt);
unset($conn);
?>
```

## <a name="example---use-the-statement-option"></a>Пример. Использование statement в качестве параметра
Кроме того, атрибут statement можно использовать в качестве параметра.

```php
<?php
$database = "test";
$server = "(local)";
$conn = new PDO("sqlsrv:server = $server; Database = $database", "", "");

$dateObj = null;
$query = "SELECT DateTimeCol FROM aTable";
$options = array(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE => true);
$stmt = $conn->prepare($query, $options);
$stmt->execute();
$stmt->bindColumn(1, $dateObj, PDO::PARAM_LOB);
$row = $stmt->fetch(PDO::FETCH_BOUND);
var_dump($dateObj);

unset($stmt);
unset($conn);
?>
```

## <a name="example---retrieve-datetime-types-as-strings"></a>Пример. Извлечение типов datetime в виде строк
Следующий пример показывает, как достичь противоположного (что на самом деле не обязательно, так как по умолчанию задано false):

```php
<?php
$database = "MyData";
$conn = new PDO("sqlsrv:server = (local); Database = $database");

$dateStr = null;
$query = 'SELECT DateTimeCol FROM table1';
$options = array(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE => false);
$stmt = $conn->prepare($query, $options);
$stmt->execute();
$stmt->bindColumn(1, $dateStr);
$row = $stmt->fetch(PDO::FETCH_BOUND);
echo $dateStr . PHP_EOL;

unset($stmt);
unset($conn);
?>
```

## <a name="see-also"></a>См. также:
[Извлечение данных](../../connect/php/retrieving-data.md)

[Извлечение типов даты и времени в виде строк с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)