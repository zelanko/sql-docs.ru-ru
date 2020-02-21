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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "68265136"
---
# <a name="formatting-decimal-strings-and-money-values-sqlsrv-driver"></a>Форматирование десятичных строк и денежных значений (драйвер SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Чтобы сохранить точность, [типы decimal или numeric](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) всегда извлекаются как строки с особой точностью и масштабом. Если какое-либо значение меньше 1, начальный ноль отсутствует. Это аналогично полям money и smallmoney, так как они являются десятичными полями с фиксированным масштабом равным 4.

## <a name="add-leading-zeroes-if-missing"></a>Добавление ведущих нулей, если они отсутствуют
Начиная с версии 5.6.0, параметр `FormatDecimals` добавляется на уровнях подключения sqlsrv и инструкции, что позволяет пользователю форматировать десятичные строки. Этот параметр принимает логическое значение (true или false) и влияет только на форматирование десятичных или числовых значений в результатах выборки. Иными словами, параметр `FormatDecimals` не влияет на другие операции, такие как вставка или обновление.

Значение `FormatDecimals` по умолчанию — **false**. Если задано значение true, то начальные нули в десятичных строках будут добавлены для любого десятичного значения меньше 1.

## <a name="configure-number-of-decimal-places"></a>Настройка числа десятичных знаков
Если `FormatDecimals` включен, то параметр `DecimalPlaces` позволяет пользователям настраивать число десятичных знаков при отображении данных money и smallmoney. Он принимает целочисленные значения в диапазоне [0, 4] и может выполнять округление отображаемого числа. Однако базовые данные money остаются неизменными.

Для обоих параметров можно задать уровень подключения или инструкции, а параметр инструкции всегда переопределяет соответствующий параметр подключения. Обратите внимание, что параметр `DecimalPlaces` влияет **только** на данные money, а параметр `FormatDecimals` должен быть со значением true, чтобы параметр `DecimalPlaces` вступил в силу. В противном случае форматирование отключается независимо от параметра `DecimalPlaces`.

> [!NOTE]
> Так как поля money или smallmoney имеют масштаб 4, то при установке значения `DecimalPlaces` любое отрицательное число или любое значение больше 4 будет игнорироваться. Не рекомендуется использовать какие-либо отформатированные данные money в качестве входных данных для вычислений.

## <a name="example---a-simple-fetch"></a>Пример. Простая выборка
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

## <a name="example---format-the-output-parameter"></a>Пример. Форматирование параметра вывода
Если десятичное или числовое поле возвращается в качестве [параметра вывода](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md), то возвращаемое значение будет рассматриваться как обычная строка типа varchar. Однако если указано SQLSRV_SQLTYPE_DECIMAL или SQLSRV_SQLTYPE_NUMERIC, можно задать для `FormatDecimals` значение true, чтобы в начале числового строкового значения не отсутствовал ноль. Дополнительные сведения см. в статье [Практическое руководство. Извлечение параметров вывода с помощью драйвера SQLSRV](../..//connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).

В следующем примере показано, как форматировать параметр вывода хранимой процедуры, возвращающий значение decimal(8,4).

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
