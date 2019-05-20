---
title: PDOStatement::setAttribute | Документация Майкрософт
ms.custom: ''
ms.date: 04/22/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46b6c9be6566b3b4857f58d779838356fe3b689e
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774984"
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
|PDO::SQLSRV_ATTR_DECIMAL_PLACES|Целое число от 0 до 4 (включительно).|Указывает число десятичных знаков при форматировании полученных денежных значений.<br /><br />Любое отрицательное целое число или значение больше 4 будет игнорироваться.<br /><br />Этот параметр работает, только если для PDO::SQLSRV_ATTR_FORMAT_DECIMALS указано значение true.<br /><br />Этот параметр также можно задать на уровне подключения. Если этот параметр указан, он переопределяет параметр на уровне подключения.<br /><br />См. подробнее о [форматировании десятичных строк и денежных значений (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).|
|PDO::SQLSRV_ATTR_ENCODING|Целочисленный<br /><br />PDO::SQLSRV_ENCODING_UTF8 (по умолчанию)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|Задает кодировку, используемую драйвером для обмена данными с сервером.|  
|PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE|true или false|Указывает, нужно ли извлекать типы даты и времени в виде объектов [PHP DateTime](http://php.net/manual/en/class.datetime.php). Если оставить значение false, по умолчанию они будут возвращаться как строки.<br /><br />Этот параметр также можно задать на уровне подключения. Если этот параметр указан, он переопределяет параметр на уровне подключения.<br /><br />См. подробнее об [извлечении типов даты и времени в виде объектов PHP DateTime с помощью драйвера PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|true или false|Обрабатывает выборку числовых значений из столбцов с числовыми типами SQL (bit, integer, smallint, tinyint, float или real).<br /><br />Если включен флаг параметра подключения ATTR_STRINGIFY_FETCHES, возвращаемое значение является строкой даже при включении SQLSRV_ATTR_FETCHES_NUMERIC_TYPE.<br /><br />Если возвращаемый тип PDO в столбце привязки представляет PDO_PARAM_INT, возвращаемое значение из столбца с целочисленными значениями имеет тип int даже при отключении SQLSRV_ATTR_FETCHES_NUMERIC_TYPE.|  
|PDO::SQLSRV_ATTR_FORMAT_DECIMALS|true или false|Указывает, нужно ли при необходимости добавлять начальные нули к десятичным строкам. Если этот параметр задан, включается параметр PDO::SQLSRV_ATTR_DECIMAL_PLACES для форматирования типов валюты. Если задано значение false, по умолчанию будут возвращаться точные числа с пропуском начальных нулей для значений меньше 1.<br /><br />Этот параметр также можно задать на уровне подключения. Если этот параметр указан, он переопределяет параметр на уровне подключения.<br /><br />См. подробнее о [форматировании десятичных строк и денежных значений (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).| 
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
  
