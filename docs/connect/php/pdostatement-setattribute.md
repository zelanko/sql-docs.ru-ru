---
title: PDOStatement::setAttribute | Документация Майкрософт
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ec2ed7275c3580554c385940c5cef134244ae35
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744344"
---
# <a name="pdostatementsetattribute"></a>PDOStatement::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Задает значение атрибута — либо предопределенный атрибута PDO, либо пользовательский атрибут драйвера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDOStatement::setAttribute ($attribute, $value );  
```  
  
#### <a name="parameters"></a>Параметры  
$*attribute*: целое число, одна из констант PDO::ATTR_* или PDO::SQLSRV_ATTR_\*. Список доступных атрибутов см. в разделе "Примечания".  
  
$*value*: значение (смешанное), задаваемое для указанного $*attribute*.  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение TRUE в случае успеха, в противном случае — значение FALSE.  
  
## <a name="remarks"></a>Remarks  
Следующая таблица содержит список доступных атрибутов.  
  
|attribute|Значения|Описание|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|От 1 до предела памяти PHP.|Задает размер буфера, который содержит результирующий набор для клиентского курсора.<br /><br />Значение по умолчанию — 10 240 КБ (10 МБ).<br /><br />Дополнительные сведения о клиентских курсорах см. в статье [Типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_DECIMAL_PLACES|Целое число от 0 до 4 (включительно)|Указывает, что число десятичных разрядов, при форматировании извлечь денежных значений.<br /><br />Любое отрицательное целое число или значение больше 4 будет игнорироваться.<br /><br />Этот параметр работает только в том случае, если PDO::SQLSRV_ATTR_FORMAT_DECIMALS имеет значение true.<br /><br />Этот параметр также можно задать на уровне соединения. Если Да, этот параметр переопределяет параметр уровня подключения.<br /><br />Дополнительные сведения см. в разделе [форматирование десятичных строк и денежные значения (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).|
|PDO::SQLSRV_ATTR_ENCODING|Целочисленный<br /><br />PDO::SQLSRV_ENCODING_UTF8 (по умолчанию)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|Задает кодировку, используемую драйвером для обмена данными с сервером.|  
|PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE|true или false|Указывает, следует ли получить типы даты и времени как [PHP DateTime](http://php.net/manual/en/class.datetime.php) объектов. Если оставить это значение false, поведение по умолчанию — вернуть их в виде строки.<br /><br />Этот параметр также можно задать на уровне соединения. Если Да, этот параметр переопределяет параметр уровня подключения.<br /><br />Дополнительные сведения см. в разделе [как: получить дату и время типы как объектов DateTime PHP с помощью драйвера PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|true или false|Обрабатывает числовых операций выборки из столбцов с числовыми типами SQL (бит, integer, smallint, tinyint, float или real).<br /><br />Если включен флаг параметра подключения ATTR_STRINGIFY_FETCHES, возвращаемое значение является строкой, даже в том случае, если включен SQLSRV_ATTR_FETCHES_NUMERIC_TYPE.<br /><br />Если возвращаемый тип PDO в столбце привязки PDO_PARAM_INT, возвращаемое значение из столбца целое число имеет тип int, даже если SQLSRV_ATTR_FETCHES_NUMERIC_TYPE отключен.|  
|PDO::SQLSRV_ATTR_FORMAT_DECIMALS|true или false|Указывает, следует ли добавить начальные нули для десятичных строк, когда это необходимо. Если этот параметр задан, включает параметр PDO::SQLSRV_ATTR_DECIMAL_PLACES для форматирования типов money. Если оставить это значение false, используется поведение по умолчанию возврат точного точности и пропуск начальных нулей для значений меньше 1.<br /><br />Этот параметр также можно задать на уровне соединения. Если Да, этот параметр переопределяет параметр уровня подключения.<br /><br />Дополнительные сведения см. в разделе [форматирование десятичных строк и денежные значения (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).| 
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Целочисленный|Задает время ожидания выполнения запроса в секундах.<br /><br />По умолчанию драйвер ожидает результаты бесконечно. Отрицательные значения не допускаются.<br /><br />0 означает отсутствие времени ожидания.|  
  
## <a name="example"></a>Пример  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets'=>false )  );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
echo $stmt->getAttribute( constant( "PDO::ATTR_CURSOR" ) );  
  
echo "\n";  
  
$stmt->setAttribute(PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 2);  
echo $stmt->getAttribute( constant( "PDO::SQLSRV_ATTR_QUERY_TIMEOUT" ) );  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
