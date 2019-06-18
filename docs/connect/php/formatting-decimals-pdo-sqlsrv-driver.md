---
title: Форматирование десятичных строк и денежных значений (драйвер PDO_SQLSRV) | Документация Майкрософт
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- formatting, decimal types, money values
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.openlocfilehash: 35626c192c3d74ad0201cee3c5e97adbce92a3aa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62669699"
---
# <a name="formatting-decimal-strings-and-money-values-pdosqlsrv-driver"></a>Форматирование десятичных строк и денежных значений (драйвер PDO_SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Чтобы сохранить точность, [десятичным или числовым типам](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) всегда обрабатываются как строки с помощью точного представления точности и шкалы. Если любое значение меньше 1, отсутствует начальный ноль. Это то же самое с money и smallmoney полей, так как это десятичное поля с фиксированным масштабом, равным 4.

## <a name="add-leading-zeroes-if-missing"></a>Добавить начальные нули при отсутствии
Начиная с версии 5.6.0, соединение или атрибут инструкции `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` позволяет пользователю производить форматирование десятичных строк. Этот атрибут принимает только логическое значение (true или false) и влияет только на форматирование десятичных или числовых значений в выбранных результатов. Другими словами этот атрибут не влияет на другие операции, такие как обновления и вставки.

Значение `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` по умолчанию — **false**. Если задано значение true, ведущие нули для десятичных строк будут добавляться для десятичного значения меньше 1.

## <a name="configure-number-of-decimal-places"></a>Настройте число десятичных разрядов
С помощью `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` отключен, еще один атрибут соединение или оператор, `PDO::SQLSRV_ATTR_DECIMAL_PLACES`, пользователи могут настраивать количество десятичных разрядов, при отображении данных money и smallmoney. Он принимает целочисленные значения в диапазоне [0, 4], и округление может произойти при отображении. Тем не менее базовые данные деньги не изменяются.

Атрибуты инструкции всегда переопределяют соответствующие параметры подключения. Обратите внимание, что `PDO::SQLSRV_ATTR_DECIMAL_PLACES` параметр **только** влияет на данных money и `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` необходимо задать значение true. В противном случае форматирование находится в отключенном состоянии вне зависимости от `PDO::SQLSRV_ATTR_DECIMAL_PLACES` параметр.

> [!NOTE]
> Поскольку поля типа money и smallmoney масштаб 4, установка `PDO::SQLSRV_ATTR_DECIMAL_PLACES` любое отрицательное значение или любое значение размером более 4 будет игнорироваться. Не рекомендуется использовать все данные, форматированные деньги в качестве входных данных, чтобы любые вычисления.

### <a name="to-set-the-connection-attributes"></a>Чтобы задать атрибуты соединения

-   Задать атрибуты точке подключения:

    ```php
    $attrs = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => true,
                   PDO::SQLSRV_ATTR_DECIMAL_PLACES => 2);

    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password, $attrs);
    ```

-   Задать атрибуты подключение post:

    ```php
    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password);
    $conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
    $conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);
    ```

## <a name="example---format-money-data"></a>Пример — формат данных типа money
Приведенный ниже показано, как получить деньги данных с помощью [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md):

```php
<?php
$database = "myDB";
$server = "(local)";
$conn = new PDO( "sqlsrv:server=$server; Database = $database", "", "");
$conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);

$numDigits = 3;
$query = "SELECT smallmoney1 FROM aTable";
$options = array(PDO::SQLSRV_ATTR_DECIMAL_PLACES => $numDigits);
$stmt = $conn->prepare($query, $options);
$stmt->execute();

$stmt->bindColumn('smallmoney1', $field);
$result = $stmt->fetch(PDO::FETCH_BOUND);
echo $field;    // expect a number string with 3 decimal places

unset($stmt);
unset($conn);
?>
```

## <a name="example---override-connection-attributes"></a>Пример — переопределение атрибуты соединения
Следующий пример показывает переопределение атрибутов соединения:

```php
<?php
$database = 'myDatabase';
$server = 'myServer';
$username = 'myuser';
$password = 'mypassword'

$conn = new PDO("sqlsrv:server=$server; Database = $database", $username, $password);
$conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
$conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);

$query = 'SELECT smallmoney1 FROM testTable1';
$options = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => false);
$stmt = $conn->prepare($query, $options);
$stmt->execute();

$stmt->bindColumn('smallmoney1', $field);
$result = $stmt->fetch(PDO::FETCH_BOUND);  
echo $field;   // expect a number string showing the original scale -- 4 decimal places

unset($stmt);
unset($conn);
?>
```

## <a name="see-also"></a>См. также:
[Форматирование десятичных строк и денежных значений (драйвер SQLSRV)](../../connect/php/formatting-decimals-sqlsrv-driver.md)

[Извлечение данных](../../connect/php/retrieving-data.md)
