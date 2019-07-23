---
title: Форматирование десятичных строк и денежных значений (драйвер SQLSRV) | Документация Майкрософт
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
ms.openlocfilehash: 4a5ac641a98077c09bb38a5fc8fbd3fb1a4bf73d
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265136"
---
# <a name="formatting-decimal-strings-and-money-values-sqlsrv-driver"></a>Форматирование десятичных строк и денежных значений (драйвер SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Чтобы сохранить точность, [десятичные или числовые типы](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) всегда извлекаться как строки с точной точностью и масштабом. Если какое-либо значение меньше 1, начальный ноль отсутствует. Он аналогичен полям Money и smallmoney, так как они являются десятичными полями с фиксированным масштабом, равным 4.

## <a name="add-leading-zeroes-if-missing"></a>Добавлять ведущие нули, если они отсутствуют
Начиная с версии 5.6.0, параметр `FormatDecimals` добавляется для соединения sqlsrv и уровней инструкций, что позволяет пользователю форматировать десятичные строки. Этот параметр принимает логическое значение (true или false) и влияет только на форматирование десятичных или числовых значений в выбранных результатах. Иными словами, `FormatDecimals` параметр не влияет на другие операции, такие как вставка или обновление.

Значение `FormatDecimals` по умолчанию — **false**. Если задано значение true, то начальные нули в десятичных строках будут добавлены для любого десятичного значения меньше 1.

## <a name="configure-number-of-decimal-places"></a>Настройка числа десятичных разрядов
Если включен, другой параметр позволяет пользователям настраивать количество десятичных разрядов при отображении данных money и smallmoney. `DecimalPlaces` `FormatDecimals` Он принимает целочисленные значения в диапазоне [0, 4], а округление может произойти при отображении. Однако базовые данные Money остаются неизменными.

Для обоих параметров можно задать соединение или уровень инструкций, а параметр инструкции всегда переопределяет соответствующий параметр соединения. Обратите внимание `DecimalPlaces` , что параметр влияет **только** на данные `FormatDecimals` денег и должен иметь значение true `DecimalPlaces` для вступления в силу. В противном случае форматирование будет отключено независимо `DecimalPlaces` от параметра.

> [!NOTE]
> Так как поля Money или smallmoney имеют масштаб 4, `DecimalPlaces` установка значения любого отрицательного числа или любого значения, превышающего 4, будет игнорироваться. Не рекомендуется использовать какие-либо отформатированные данные денег в качестве входных данных для любого вычисления.

## <a name="example---a-simple-fetch"></a>Пример. простая выборка
В следующем примере показано, как использовать новые параметры в простой выборке.

```php
<?php
$username = 'myusername';
$password = 'mypasword';
$tableName = 'mytable';

$connectionInfo = array("UID" => $username, "PWD" => $password, "Database" => "myDB", "FormatDecimals" => true);  
$server = "myServer";  // IP address also works
$conn = sqlsrv_connect( $server, $connectionInfo);  

$numDigits = 2;
$query = "SELECT money1 FROM $tableName";
$options = array("DecimalPlaces" => $numDigits);
$stmt = sqlsrv_prepare($conn, $query, array(), $options);
sqlsrv_execute($stmt);

if (sqlsrv_fetch($stmt)) {
    $field = sqlsrv_get_field($stmt, 0);  
    echo $field;   // expect a numeric value string with 2 decimal places
}

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);
?>
```

## <a name="example---format-the-output-parameter"></a>Пример. форматирование выходного параметра
Если в качестве [выходного параметра](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)возвращается десятичное или числовое поле, возвращаемое значение будет рассматриваться как обычная строка типа varchar. Однако если указано значение SQLSRV_SQLTYPE_DECIMAL или SQLSRV_SQLTYPE_NUMERIC, можно задать `FormatDecimals` значение true, чтобы гарантировать отсутствие недостающего нуля для числового строкового значения. Дополнительные сведения см. в [практическом руководстве по извлечению параметров вывода с помощью драйвера SQLSRV](../..//connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).

В следующем примере показано, как форматировать выходной параметр хранимой процедуры, возвращающей значение Decimal (8, 4).

```php
$outString = '';
$outSql = '{CALL myStoredProc(?)}';
$stmt = sqlsrv_prepare($conn, 
                       $outSql, 
                       array(array(&$outString, SQLSRV_PARAM_OUT, null, SQLSRV_SQLTYPE_DECIMAL(8, 4))),
                       array('FormatDecimals' => true));

if (sqlsrv_execute($stmt)) {
    echo $outString;  // expect a numeric value string with no missing leading zero
}
```

## <a name="see-also"></a>См. также:
[Форматирование десятичных строк и денежных значений (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)

[Извлечение данных](../../connect/php/retrieving-data.md)
