---
title: PDO::SetAttribute | Документы Microsoft
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56f9ee96-e1d2-46cc-b137-38f06a251863
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a94273f371b8ed942b945e836e1e6088187276a7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
*$value*: значение (смешанный тип).  
  
## <a name="return-value"></a>Возвращаемое значение  
Возвращает значение true в случае успеха, в противном случае — значение false.  
  
## <a name="remarks"></a>Замечания  
  
|Attribute|Обрабатывается|Поддерживаемые значения|Описание|  
|-------------|----------------|--------------------|---------------|  
|PDO::ATTR_CASE|PDO|PDO::CASE_LOWER<br /><br />PDO::CASE_NATURAL<br /><br />PDO::CASE_UPPER|Указывает регистр имен столбцов.<br /><br />PDO::CASE_LOWER задает имена столбцов в нижнем регистре.<br /><br />PDO::CASE_NATURAL (используется по умолчанию) отображает имена столбцов в том виде, в котором они возвращаются из базы данных.<br /><br />PDO::CASE_UPPER задает имена столбцов в верхнем регистре.<br /><br />Этот атрибут можно задать с помощью PDO::setAttribute.|  
|PDO::ATTR_DEFAULT_FETCH_MODE|PDO|Обратитесь к документации по PDO.|Обратитесь к документации по PDO.|  
|PDO::ATTR_ERRMODE|PDO|PDO::ERRMODE_SILENT<br /><br />PDO::ERRMODE_WARNING<br /><br />PDO::ERRMODE_EXCEPTION|Указывает, как драйвер сообщает сбоев.<br /><br />PDO::ERRMODE_SILENT (используется по умолчанию) задает коды ошибок и сведения об ошибках.<br /><br />PDO::ERRMODE_WARNING вызывает E_WARNING.<br /><br />PDO::ERRMODE_EXCEPTION приводит к возникновению исключения.<br /><br />Этот атрибут можно задать с помощью PDO::setAttribute.|  
|PDO::ATTR_ORACLE_NULLS|PDO|Обратитесь к документации по PDO.|Указывает, как следует возвращать значения NULL.<br /><br />PDO::NULL_NATURAL не выполняет преобразование.<br /><br />PDO::NULL_EMPTY_STRING преобразует пустую строку в значение NULL.<br /><br />PDO::NULL_TO_STRING преобразует значение NULL d пустую строку.|  
|PDO::ATTR_STATEMENT_CLASS|PDO|Обратитесь к документации по PDO.|Задает пользовательский класс инструкций, производный от PDOStatement.<br /><br />Требует использования `array(string classname, array(mixed constructor_args))`.<br /><br />Дополнительные сведения см. в разделе документации по PDO.|  
|PDO::ATTR_STRINGIFY_FETCHES|PDO|true или false|Преобразует числовые значения в строки при извлечении данных.|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|От 1 до предела памяти PHP.|Задает размер буфера, который содержит результирующий набор.<br /><br />Значение по умолчанию — базе 10240 КБ (10 МБ).<br /><br />Дополнительные сведения о запросах, создающих клиентский курсор см. в разделе [типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true<br /><br />false|Задает выполнение прямого или подготовленного запроса. Дополнительные сведения см. в статье [Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_ENCODING|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PDO::SQLSRV_ENCODING_UTF8<br /><br />PDO::SQLSRV_ENCODING_SYSTEM|Задает кодировку, используемую драйвером для обмена данными с сервером.<br /><br />PDO::SQLSRV_ENCODING_BINARY не поддерживается.<br /><br />По умолчанию используется PDO::SQLSRV_ENCODING_UTF8.|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true или false|Обрабатывает числовые выборки из столбцов с числовыми типами SQL (бит, целое число со знаком, smallint, tinyint, float или real).<br /><br />Если включен флаг параметр подключения ATTR_STRINGIFY_FETCHES возвращаемое значение является строкой, даже в том случае, если включен SQLSRV_ATTR_FETCHES_NUMERIC_TYPE.<br /><br />Если возвращаемый тип PDO в столбце привязки PDO_PARAM_INT, возвращаемое значение целочисленного столбца является объектом типа int, даже если SQLSRV_ATTR_FETCHES_NUMERIC_TYPE отключен.|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|integer|Задает время ожидания выполнения запроса в секундах.<br /><br />По умолчанию используется значение 0, то есть драйвер ожидает результаты бесконечно долго.<br /><br />Отрицательные значения не допускаются.|  
|PDO::SQLSRV_CLIENT_BUFFER_MAX_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|integer|Задает размер буфера запроса.<br /><br />По умолчанию используется значение 0, которое соответствует неограниченному размеру буфера.<br /><br />Отрицательные значения не допускаются.<br /><br />Дополнительные сведения о запросах, создающих клиентский курсор см. в разделе [типы курсоров &#40;драйвер PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
  
PDO обрабатывает некоторые предопределенные атрибуты, оставляя обработку остальных драйверу. Все настраиваемые атрибуты и параметры соединения обрабатываются драйвером. Неподдерживаемый атрибут, параметре соединения или неподдерживаемое значение отмечается согласно настройке PDO::ATTR_ERRMODE.  
  
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
  
## <a name="see-also"></a>См. также  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
