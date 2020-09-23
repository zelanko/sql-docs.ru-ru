---
title: PDO::setAttribute
description: Справочник по API для функции PDO::setAttribute в драйвере Microsoft PDO_SQLSRV для PHP для SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 56f9ee96-e1d2-46cc-b137-38f06a251863
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fc64e04ee53b6b654974312a8a7050bbb120a804
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645894"
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
|PDO::ATTR_DEFAULT_STR_PARAM|PDO|PDO::PARAM_STR_CHAR<br /><br />PDO::PARAM_STR_NATL|Дополнительные сведения см. в примерах использования класса [PDO::quote](../../connect/php/pdo-quote.md).|
|PDO::ATTR_ERRMODE|PDO|PDO::ERRMODE_SILENT<br /><br />PDO::ERRMODE_WARNING<br /><br />PDO::ERRMODE_EXCEPTION|Указывает, как драйвер сообщает о сбоях.<br /><br />PDO::ERRMODE_SILENT (используется по умолчанию) задает коды ошибок и сведения об ошибках.<br /><br />PDO::ERRMODE_WARNING вызывает E_WARNING.<br /><br />PDO::ERRMODE_EXCEPTION приводит к возникновению исключения.<br /><br />Этот атрибут можно задать с помощью PDO::setAttribute.|  
|PDO::ATTR_ORACLE_NULLS|PDO|Обратитесь к документации по PDO.|Указывает, как следует возвращать значения NULL.<br /><br />PDO::NULL_NATURAL не выполняет преобразование.<br /><br />PDO::NULL_EMPTY_STRING преобразует пустую строку в значение NULL.<br /><br />PDO::NULL_TO_STRING преобразует значение NULL d пустую строку.|  
|PDO::ATTR_STATEMENT_CLASS|PDO|Обратитесь к документации по PDO.|Задает пользовательский класс инструкций, производный от PDOStatement.<br /><br />Требует использования `array(string classname, array(mixed constructor_args))`.<br /><br />Дополнительные сведения см. в документации по PDO.|  
|PDO::ATTR_STRINGIFY_FETCHES|PDO|true или false|Преобразует числовые значения в строки при извлечении данных.|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|От 1 до предела памяти PHP.|Задает размер буфера, который содержит результирующий набор при использовании клиентского курсора.<br /><br />Значение по умолчанию — 10 240 КБ, если не указано в файле php.ini.<br /><br />Число должно быть больше нуля.<br /><br />Дополнительные сведения о запросах, создающих клиентский курсор: [Типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_DECIMAL_PLACES|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|Целое число от 0 до 4 (включительно).|Указывает число десятичных знаков при форматировании полученных денежных значений.<br /><br />Любое отрицательное целое число или значение больше 4 будет игнорироваться.<br /><br />Этот параметр работает, только если для PDO::SQLSRV_ATTR_FORMAT_DECIMALS указано значение true.<br /><br />Этот параметр также можно задать на уровне инструкции. В таком случае этот параметр будет переопределен параметром уровня инструкции.<br /><br />См. подробнее о [форматировании десятичных строк и денежных значений (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).|
|PDO::SQLSRV_ATTR_DIRECT_QUERY|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true или false|Задает выполнение прямого или подготовленного запроса. Дополнительные сведения см. в статье [Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_ENCODING|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PDO::SQLSRV_ENCODING_UTF8<br /><br />PDO::SQLSRV_ENCODING_SYSTEM|Задает кодировку, используемую драйвером для обмена данными с сервером.<br /><br />PDO::SQLSRV_ENCODING_BINARY не поддерживается.<br /><br />По умолчанию используется PDO::SQLSRV_ENCODING_UTF8.|  
|PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true или false|Указывает, нужно ли извлекать типы даты и времени в виде объектов [PHP DateTime](http://php.net/manual/en/class.datetime.php). Если оставить значение false, по умолчанию они будут возвращаться как строки.<br /><br />Этот параметр также можно задать на уровне инструкции. В таком случае этот параметр будет переопределен параметром уровня инструкции.<br /><br />Дополнительные сведения см. в разделе [Как извлечь типы даты и времени в виде объектов даты и времени PHP с помощью драйвера PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true или false|Обрабатывает выборку числовых значений из столбцов с числовыми типами SQL (bit, integer, smallint, tinyint, float или real).<br /><br />Если включен флаг параметра подключения ATTR_STRINGIFY_FETCHES, возвращаемое значение является строкой даже при включении SQLSRV_ATTR_FETCHES_NUMERIC_TYPE.<br /><br />Если возвращаемый тип PDO в столбце привязки представляет PDO_PARAM_INT, возвращаемое значение из столбца с целочисленными значениями имеет тип int даже при отключении SQLSRV_ATTR_FETCHES_NUMERIC_TYPE.|  
|PDO::SQLSRV_ATTR_FORMAT_DECIMALS|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true или false|Указывает, нужно ли при необходимости добавлять начальные нули к десятичным строкам. Если этот параметр задан, включается параметр PDO::SQLSRV_ATTR_DECIMAL_PLACES для форматирования типов валюты. Если задано значение false, по умолчанию будут возвращаться точные числа с пропуском начальных нулей для значений меньше 1.<br /><br />Этот параметр также можно задать на уровне инструкции. В таком случае этот параметр будет переопределен параметром уровня инструкции.<br /><br />См. подробнее о [форматировании десятичных строк и денежных значений (драйвер PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).| 
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|целое число|Задает время ожидания выполнения запроса в секундах.<br /><br />По умолчанию используется значение 0, то есть драйвер ожидает результаты бесконечно долго.<br /><br />Отрицательные значения не допускаются.|  
  
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
  
