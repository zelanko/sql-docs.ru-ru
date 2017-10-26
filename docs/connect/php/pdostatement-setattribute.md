---
title: "PDOStatement::setAttribute | Документы Microsoft"
ms.custom: 
ms.date: 07/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 31e760b44469df1e1f3a0d1c285b731d87155bcf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
|attribute|Значения|Description|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|От 1 до предела памяти PHP.|Задает размер буфера, который содержит результирующий набор для клиентского курсора.<br /><br />Значение по умолчанию — базе 10240 КБ (10 МБ).<br /><br />Дополнительные сведения о клиентских курсорах см. в разделе [типы курсоров &#40; Драйвер PDO_SQLSRV &#41; ](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
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
  
## <a name="see-also"></a>См. также:  
[Класс PDOStatement](../../connect/php/pdostatement-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

