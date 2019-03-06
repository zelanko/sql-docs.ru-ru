---
title: PDO::SetAttribute | Документация Майкрософт
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 56f9ee96-e1d2-46cc-b137-38f06a251863
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b0109eef02bc3649617b4f1f414406665c16ba9
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744654"
---
# <a name="pdosetattribute"></a>PDO::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Задает предопределенный атрибут PDO либо настраиваемый атрибут драйвера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
bool PDO::setAttribute ( $attribute, $value );  
```  
  
#### <a name="parameters"></a>Параметры  
*$attribute*: задаваемый атрибут. Список поддерживаемых атрибутов см. в разделе "Примечания".  
  
*$value*: значение (смешанные типы).  
  
## <a name="return-value"></a>Возвращаемое значение  
Возвращает значение true в случае успеха, в противном случае — значение false.  
  
## <a name="remarks"></a>Remarks  
  
|attribute|Обрабатывается|Поддерживаемые значения|Описание|  
|-------------|----------------|--------------------|---------------|  
|PDO::ATTR_CASE|PDO|PDO::CASE_LOWER<br /><br />PDO::CASE_NATURAL<br /><br />PDO::CASE_UPPER|Указывает регистр имен столбцов.<br /><br />PDO::CASE_LOWER задает имена столбцов в нижнем регистре.<br /><br />PDO::CASE_NATURAL (используется по умолчанию) отображает имена столбцов в том виде, в котором они возвращаются из базы данных.<br /><br />PDO::CASE_UPPER задает имена столбцов в верхнем регистре.<br /><br />Этот атрибут можно задать с помощью PDO::setAttribute.|  
|PDO::ATTR_DEFAULT_FETCH_MODE|PDO|Обратитесь к документации по PDO.|Обратитесь к документации по PDO.|  
|PDO::ATTR_ERRMODE|PDO|PDO::ERRMODE_SILENT<br /><br />PDO::ERRMODE_WARNING<br /><br />PDO::ERRMODE_EXCEPTION|Указывает, как драйвер сообщает об ошибках.<br /><br />PDO::ERRMODE_SILENT (используется по умолчанию) задает коды ошибок и сведения об ошибках.<br /><br />PDO::ERRMODE_WARNING вызывает E_WARNING.<br /><br />PDO::ERRMODE_EXCEPTION приводит к возникновению исключения.<br /><br />Этот атрибут можно задать с помощью PDO::setAttribute.|  
|PDO::ATTR_ORACLE_NULLS|PDO|Обратитесь к документации по PDO.|Указывает, как следует возвращать значения NULL.<br /><br />PDO::NULL_NATURAL не выполняет преобразование.<br /><br />PDO::NULL_EMPTY_STRING преобразует пустую строку в значение NULL.<br /><br />PDO::NULL_TO_STRING преобразует значение NULL d пустую строку.|  
|PDO::ATTR_STATEMENT_CLASS|PDO|Обратитесь к документации по PDO.|Задает пользовательский класс инструкций, производный от PDOStatement.<br /><br />Требует использования `array(string classname, array(mixed constructor_args))`.<br /><br />Дополнительные сведения см. в документации по PDO.|  
|PDO::ATTR_STRINGIFY_FETCHES|PDO|true или false|Преобразует числовые значения в строки при извлечении данных.|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|От 1 до предела памяти PHP.|Задает размер буфера, который содержит результирующий набор при использовании клиентского курсора.<br /><br />Значение по умолчанию — 10 240 КБ, если не указано в файле php.ini.<br /><br />Число должно быть больше нуля.<br /><br />Дополнительные сведения о запросах, создающих клиентский курсор: [Типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_DECIMAL_PLACES|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|Целое число от 0 до 4 (включительно)|Указывает, что число десятичных разрядов, при форматировании извлечь денежных значений.<br /><br />Любое отрицательное целое число или значение больше 4 будет игнорироваться.<br /><br />Этот параметр работает только в том случае, если PDO::SQLSRV_ATTR_FORMAT_DECIMALS имеет значение true.<br /><br />Этот параметр также можно задать на уровне инструкций. Если Да, параметр уровня инструкции переопределяет такой.<br /><br />Дополнительные сведения см. в разделе [форматирование десятичных строк и денежные значения (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).|
|PDO::SQLSRV_ATTR_DIRECT_QUERY|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true или false|Задает выполнение прямого или подготовленного запроса. Дополнительные сведения см. в статье [Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_ENCODING|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PDO::SQLSRV_ENCODING_UTF8<br /><br />PDO::SQLSRV_ENCODING_SYSTEM|Задает кодировку, используемую драйвером для обмена данными с сервером.<br /><br />PDO::SQLSRV_ENCODING_BINARY не поддерживается.<br /><br />По умолчанию используется PDO::SQLSRV_ENCODING_UTF8.|  
|PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true или false|Указывает, следует ли получить типы даты и времени как [PHP DateTime](http://php.net/manual/en/class.datetime.php) объектов. Если оставить это значение false, поведение по умолчанию — вернуть их в виде строки.<br /><br />Этот параметр также можно задать на уровне инструкций. Если Да, параметр уровня инструкции переопределяет такой.<br /><br />Дополнительные сведения см. в разделе [как: получить дату и время типы как объектов DateTime PHP с помощью драйвера PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true или false|Обрабатывает числовых операций выборки из столбцов с числовыми типами SQL (бит, integer, smallint, tinyint, float или real).<br /><br />Если включен флаг параметра подключения ATTR_STRINGIFY_FETCHES, возвращаемое значение является строкой, даже в том случае, если включен SQLSRV_ATTR_FETCHES_NUMERIC_TYPE.<br /><br />Если возвращаемый тип PDO в столбце привязки PDO_PARAM_INT, возвращаемое значение из столбца целое число имеет тип int, даже если SQLSRV_ATTR_FETCHES_NUMERIC_TYPE отключен.|  
|PDO::SQLSRV_ATTR_FORMAT_DECIMALS|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true или false|Указывает, следует ли добавить начальные нули для десятичных строк, когда это необходимо. Если этот параметр задан, включает параметр PDO::SQLSRV_ATTR_DECIMAL_PLACES для форматирования типов money. Если оставить это значение false, используется поведение по умолчанию возврат точного точности и пропуск начальных нулей для значений меньше 1.<br /><br />Этот параметр также можно задать на уровне инструкций. Если Да, параметр уровня инструкции переопределяет такой.<br /><br />Дополнительные сведения см. в разделе [форматирование десятичных строк и денежные значения (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).| 
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|integer|Задает время ожидания выполнения запроса в секундах.<br /><br />По умолчанию используется значение 0, то есть драйвер ожидает результаты бесконечно долго.<br /><br />Отрицательные значения не допускаются.|  
  
PDO обрабатывает некоторые предопределенные атрибуты, оставляя обработку остальных драйверу. Все настраиваемые атрибуты и параметры соединения обрабатываются драйвером. Сведения о неподдерживаемых атрибутах, параметрах соединения и значениях будут выводиться согласно параметрам PDO::ATTR_ERRMODE.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
Этот пример показывает, как задать атрибут PDO::ATTR_ERRMODE.  
  
```  
<?php  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
  
   $attributes1 = array( "ERRMODE" );  
   foreach ( $attributes1 as $val ) {  
      echo "PDO::ATTR_$val: ";  
      var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
   }  
  
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
  
   $attributes1 = array( "ERRMODE" );  
   foreach ( $attributes1 as $val ) {  
      echo "PDO::ATTR_$val: ";  
      var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
   }  
?>  
```  
  
## <a name="see-also"></a>См. также:  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
