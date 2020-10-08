---
title: Форматирование десятичных строк и денежных значений (драйвер PDO_SQLSRV)
description: Узнайте, как использовать атрибуты PDO::SQLSRV_ATTR_FORMAT_DECIMALS и SQLSRV_ATTR_DECIMAL_PLACES для форматирования десятичных или денежных значений при использовании драйвера PDO_SQLSRV
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- formatting, decimal types, money values
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db9392b523be8777a96e4d262cfca5acccc8f406
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726845"
---
# <a name="formatting-decimal-strings-and-money-values-pdo_sqlsrv-driver"></a>Форматирование десятичных строк и денежных значений (драйвер PDO_SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Чтобы сохранить точность, [типы decimal или numeric](../../t-sql/data-types/decimal-and-numeric-transact-sql.md) всегда извлекаются как строки с особой точностью и масштабом. Если какое-либо значение меньше 1, начальный ноль отсутствует. Это аналогично полям money и smallmoney, так как они являются десятичными полями с фиксированным масштабом равным 4.

## <a name="add-leading-zeroes-if-missing"></a>Добавление ведущих нулей, если они отсутствуют
Начиная с версии 5.6.0, атрибут подключения или инструкции `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` позволяет пользователю форматировать десятичные строки. Этот атрибут принимает логическое значение (true или false) и влияет только на форматирование десятичных или числовых значений в результатах выборки. Иными словами, этот атрибут не влияет на другие операции, такие как вставка или обновление.

Значение `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` по умолчанию — **false**. Если задано значение true, то начальные нули в десятичных строках будут добавлены для любого десятичного значения меньше 1.

## <a name="configure-number-of-decimal-places"></a>Настройка числа десятичных знаков
Если `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` включен, то атрибут подключения или выписки, `PDO::SQLSRV_ATTR_DECIMAL_PLACES` позволяет пользователям настраивать число десятичных знаков при отображении данных money и smallmoney. Он принимает целочисленные значения в диапазоне [0, 4] и может выполнять округление отображаемого числа. Однако базовые данные money остаются неизменными.

Атрибуты выписки всегда переопределяют соответствующие параметры соединения. Обратите внимание, что параметр `PDO::SQLSRV_ATTR_DECIMAL_PLACES` влияет **только** на данные money, а параметр `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` должен быть со значением true. В противном случае форматирование отключается независимо от параметра `PDO::SQLSRV_ATTR_DECIMAL_PLACES`.

> [!NOTE]
> Так как поля money или smallmoney имеют масштаб 4, то при установке значения `PDO::SQLSRV_ATTR_DECIMAL_PLACES` любое отрицательное число или любое значение больше 4, будет игнорироваться. Не рекомендуется использовать какие-либо отформатированные данные money в качестве входных данных для вычислений.

### <a name="to-set-the-connection-attributes"></a>Установка атрибутов соединения

-   Задайте атрибуты в точке соединения:

    ```php
    $attrs = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => true,
                   PDO::SQLSRV_ATTR_DECIMAL_PLACES => 2);

    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password, $attrs);
    ```

-   Задайте атрибуты после соединения:

    ```php
    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password);
    $conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
    $conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);
    ```

## <a name="example---format-money-data"></a>Пример. Форматирование данных типа money
В следующем примере показано, как извлечь данные о денежных средствах с помощью [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md):

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

## <a name="example---override-connection-attributes"></a>Пример. Переопределение атрибутов соединения
В следующем примере показано, как переопределить атрибуты соединения.

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