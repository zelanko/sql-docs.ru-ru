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
manager: v-mabarw
ms.openlocfilehash: 76c314159faf15e63bf77b17a8a45abf217b205c
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265155"
---
# <a name="formatting-decimal-strings-and-money-values-pdosqlsrv-driver"></a>Форматирование десятичных строк и денежных значений (драйвер PDO_SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Чтобы сохранить точность, [десятичные или числовые типы](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) всегда извлекаться как строки с точной точностью и масштабом. Если какое-либо значение меньше 1, начальный ноль отсутствует. Он аналогичен полям Money и smallmoney, так как они являются десятичными полями с фиксированным масштабом, равным 4.

## <a name="add-leading-zeroes-if-missing"></a>Добавлять ведущие нули, если они отсутствуют
Начиная с версии 5.6.0, атрибут `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` Connection или Statement позволяет пользователю форматировать десятичные строки. Этот атрибут принимает логическое значение (true или false) и влияет только на форматирование десятичных или числовых значений в выбранных результатах. Иными словами, этот атрибут не влияет на другие операции, такие как вставка или обновление.

Значение `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` по умолчанию — **false**. Если задано значение true, то начальные нули в десятичных строках будут добавлены для любого десятичного значения меньше 1.

## <a name="configure-number-of-decimal-places"></a>Настройка числа десятичных разрядов
С `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` включенным другим `PDO::SQLSRV_ATTR_DECIMAL_PLACES`атрибутом соединения или оператора, позволяет пользователям настраивать количество десятичных разрядов при отображении данных money и smallmoney. Он принимает целочисленные значения в диапазоне [0, 4], а округление может произойти при отображении. Однако базовые данные Money остаются неизменными.

Атрибуты инструкции всегда переопределяют соответствующие параметры соединения. Обратите внимание `PDO::SQLSRV_ATTR_DECIMAL_PLACES` , что параметр влияет **только** на данные `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` денег и должен иметь значение true. В противном случае форматирование будет отключено независимо `PDO::SQLSRV_ATTR_DECIMAL_PLACES` от параметра.

> [!NOTE]
> Так как поля Money или smallmoney имеют масштаб 4, `PDO::SQLSRV_ATTR_DECIMAL_PLACES` значение любого отрицательного числа или любое значение больше 4 будут игнорироваться. Не рекомендуется использовать какие-либо отформатированные данные денег в качестве входных данных для любого вычисления.

### <a name="to-set-the-connection-attributes"></a>Установка атрибутов соединения

-   Задать атрибуты в точке соединения:

    ```php
    $attrs = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => true,
                   PDO::SQLSRV_ATTR_DECIMAL_PLACES => 2);

    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password, $attrs);
    ```

-   Установить атрибуты после подключения:

    ```php
    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password);
    $conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
    $conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);
    ```

## <a name="example---format-money-data"></a>Пример. Форматирование данных money
В следующем примере показано, как извлечь данные о денежных средствах с помощью [PDOStatement:: bindColumn](../../connect/php/pdostatement-bindcolumn.md):

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

## <a name="example---override-connection-attributes"></a>Пример. переопределение атрибутов соединения
В следующем примере показано, как переопределить атрибуты соединения:

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
