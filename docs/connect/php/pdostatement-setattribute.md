---
title: PDOStatement::setAttribute | Документы Microsoft
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbbb53da59f463c8dc601963f02b5b77ef6ec4b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="pdostatementsetattribute"></a>PDOStatement::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Задает значение атрибута — либо предопределенный атрибута PDO, либо пользовательский атрибут драйвера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDOStatement::setAttribute ($attribute, $value );  
```  
  
#### <a name="parameters"></a>Параметры  
$*атрибут*: целое число, одна из констант PDO::ATTR_ * или PDO::SQLSRV_ATTR_\* константы. Список доступных атрибутов см. в разделе "Примечания".  
  
$*значение*: значение (смешанное) должен быть задан для указанного $*атрибут*.  
  
## <a name="return-value"></a>Возвращаемое значение  
Значение TRUE в случае успеха, в противном случае — значение FALSE.  
  
## <a name="remarks"></a>Замечания  
Следующая таблица содержит список доступных атрибутов.  
  
|attribute|Значения|Описание|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|От 1 до предела памяти PHP.|Задает размер буфера, который содержит результирующий набор для клиентского курсора.<br /><br />Значение по умолчанию — базе 10240 КБ (10 МБ).<br /><br />Дополнительные сведения о клиентских курсорах см. в разделе [типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_ENCODING|Целочисленный<br /><br />PDO::SQLSRV_ENCODING_UTF8 (по умолчанию)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|Задает кодировку, используемую драйвером для обмена данными с сервером.|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|true или false|Обрабатывает числовые выборки из столбцов с числовыми типами SQL (бит, целое число со знаком, smallint, tinyint, float или real).<br /><br />Если включен флаг параметр подключения ATTR_STRINGIFY_FETCHES возвращаемое значение является строкой, даже в том случае, если включен SQLSRV_ATTR_FETCHES_NUMERIC_TYPE.<br /><br />Если возвращаемый тип PDO в столбце привязки PDO_PARAM_INT, возвращаемое значение целочисленного столбца является объектом типа int, даже если SQLSRV_ATTR_FETCHES_NUMERIC_TYPE отключен.|  
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
  
## <a name="see-also"></a>См. также  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
