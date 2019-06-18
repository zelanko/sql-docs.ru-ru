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
manager: mbarwin
ms.openlocfilehash: 76b6d27acedcfe2ec462a764559237a1a2218f78
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62669606"
---
# <a name="formatting-decimal-strings-and-money-values-sqlsrv-driver"></a>Форматирование десятичных строк и денежных значений (драйвер SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Чтобы сохранить точность, [десятичным или числовым типам](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) всегда обрабатываются как строки с помощью точного представления точности и шкалы. Если любое значение меньше 1, отсутствует начальный ноль. Это то же самое с money и smallmoney полей, так как это десятичное поля с фиксированным масштабом, равным 4.

## <a name="add-leading-zeroes-if-missing"></a>Добавить начальные нули при отсутствии
Начиная с версии 5.6.0, параметр `FormatDecimals` добавляется уровни sqlsrv соединений и инструкций, что позволяет пользователю производить форматирование десятичных строк. Этот параметр ожидает значение типа boolean (true или false) и влияет только на форматирование десятичных или числовых значений в выбранных результатов. Другими словами `FormatDecimals` параметр не оказывает влияния на другие операции, такие как обновления и вставки.

Значение `FormatDecimals` по умолчанию — **false**. Если задано значение true, ведущие нули для десятичных строк будут добавляться для десятичного значения меньше 1.

## <a name="configure-number-of-decimal-places"></a>Настройте число десятичных разрядов
С помощью `FormatDecimals` отключен, еще один вариант, `DecimalPlaces`, пользователи могут настраивать количество десятичных разрядов, при отображении данных money и smallmoney. Он принимает целочисленные значения в диапазоне [0, 4], и округление может произойти при отображении. Тем не менее базовые данные деньги не изменяются.

Оба варианта можно присвоить подключения или уровне инструкций, а параметр всегда инструкции переопределяет параметр соответствующего подключения. Обратите внимание, что `DecimalPlaces` параметр **только** влияет на данных money и `FormatDecimals` должно быть присвоено значение true для `DecimalPlaces` вступили в силу. В противном случае форматирование находится в отключенном состоянии вне зависимости от `DecimalPlaces` параметр.

> [!NOTE]
> Поскольку поля типа money и smallmoney масштаб 4, установка `DecimalPlaces` значение любое отрицательное значение или любое значение размером более 4 будет игнорироваться. Не рекомендуется использовать все данные, форматированные деньги в качестве входных данных, чтобы любые вычисления.

## <a name="example---a-simple-fetch"></a>Пример - простой выборки
Приведенный ниже показано, как использовать новые параметры в простой fetch.

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

## <a name="example---format-the-output-parameter"></a>Пример — формат выходного параметра
Если возвращается значение decimal или numeric поле [выходной параметр](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md), возвращаемое значение будет рассматриваться как строка регулярного varchar. Тем не менее, если указан SQLSRV_SQLTYPE_DECIMAL или SQLSRV_SQLTYPE_NUMERIC, можно задать `FormatDecimals` в значение true, чтобы убедитесь что нет отсутствующих нулем в начале для числовых строкового значения. Дополнительные сведения см. в [практическом руководстве по извлечению параметров вывода с помощью драйвера SQLSRV](../..//connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).

Следующий пример показывает способ форматирования выходной параметр хранимой процедуры, возвращающей значение decimal(8,4).

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
