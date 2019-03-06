---
title: Как извлечь типы даты и времени в виде объектов даты и времени PHP с помощью драйвера PDO_SQLSRV | Документация Майкрософт
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
manager: mbarwin
ms.openlocfilehash: 54e5b5c9c1ba59ed64db740fbbb1a643e7cb1b2c
ms.sourcegitcommit: c1105ce638078d2c941cd656b34f78486e6b2d89
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676540"
---
# <a name="how-to-retrieve-date-and-time-types-as-php-datetime-objects-using-the-pdosqlsrv-driver"></a>Как извлечь типы даты и времени в виде объектов даты и времени PHP с помощью драйвера PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Эта функция, добавленных в версии 5.6.0, допустим только в том случае, при использовании драйвера PDO_SQLSRV для [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].

### <a name="to-retrieve-date-and-time-types-as-datetime-objects"></a>Чтобы получить типы даты и времени в виде объектов DateTime

При использовании PDO_SQLSRV, типы даты и времени (**smalldatetime**, **datetime**, **даты**, **время**, **datetime2**, и **datetimeoffset**) по умолчанию возвращается в виде строк. Атрибут PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE ни PDO::ATTR_STRINGIFY_FETCHES оказывает никакого действия. Чтобы получить типы даты и времени, как [PHP DateTime](http://php.net/manual/en/class.datetime.php) объектов, установите для атрибута соединения или инструкции `PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE` для **true** (это **false** по умолчанию).

> [!NOTE]
> Это соединение или атрибут инструкции применяется только к регулярных получение типов даты и времени, так как объекты DateTime нельзя указать в качестве выходных параметров.

## <a name="example---use-the-connection-attribute"></a>Пример: используйте атрибут соединения
Следующие примеры опустить произошла ошибка при проверке для ясности. Это показано, как задать атрибут соединения:

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

## <a name="example---use-the-statement-attribute"></a>Пример - использовать атрибут инструкции
В этом примере показано, как присвоить атрибуту инструкции:

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

## <a name="example---use-the-statement-option"></a>Пример — использования параметра инструкции
Кроме того атрибут инструкции можно задать в качестве параметра:

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

## <a name="example---retrieve-datetime-types-as-strings"></a>Пример: извлечение типов даты и времени в виде строк
Приведенный ниже показано, как реализовать обратное (который будет действительно необходимо, так как это значение по умолчанию: false):

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