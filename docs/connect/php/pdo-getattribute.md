---
title: PDO::getAttribute | Документы Microsoft
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c81833ea-8b8a-459d-8f24-920098da994d
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b9930a752a9347a2d5a72e9e1871eac42be3800
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="pdogetattribute"></a>PDO::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает значение предварительно заданного атрибута PDO или атрибута драйвера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
mixed PDO::getAttribute ( $attribute )  
```  
  
#### <a name="parameters"></a>Параметры  
*$attribute*: один из поддерживаемых атрибутов. Список поддерживаемых атрибутов см. в разделе "Примечания".  
  
## <a name="return-value"></a>Возвращаемое значение  
В случае успешного выполнения возвращает значение параметра соединения, предварительно заданного атрибута PDO или настраиваемого атрибута драйвера. В случае неудачи возвращает значение NULL.  
  
## <a name="remarks"></a>Remarks  
Следующая таблица содержит список поддерживаемых атрибутов.  
  
|Attribute|Обрабатывается|Поддерживаемые значения|Описание|  
|-------------|----------------|--------------------|---------------|  
|PDO::ATTR_CASE|PDO|PDO::CASE_LOWER<br /><br />PDO::CASE_NATURAL<br /><br />PDO::CASE_UPPER|Указывает, должны ли имена столбцов иметь определенный регистр. PDO::CASE_LOWER принудительно отображает имена столбцов в нижнем регистре, PDO::CASE_NATURA оставляет имена столбцов в том виде, в котором они возвращаются из базы данных, а PDO::CASE_UPPER принудительно отображает имена столбцов в верхнем регистре.<br /><br />Значение по умолчанию — PDO::CASE_NATURAL.<br /><br />Этот атрибут также можно задать с помощью PDO::setAttribute.|  
|PDO::ATTR_CLIENT_VERSION|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|Массив строк|Описывает версии драйвера и связанные с ними библиотеки. Возвращает массив со следующими элементами: версия ODBC (*MajorVer*. *MinorVer*), [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] имя DLL-ФАЙЛ собственного клиента и версия [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] версии (*MajorVer*. *MinorVer*. *BuildNumber*. *Версия*)|  
|PDO::ATTR_DRIVER_NAME|PDO|Строковые значения|Всегда возвращает "sqlsrv".|  
|PDO::ATTR_DRIVER_VERSION|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|Строковые значения|Указывает [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] версии (*MajorVer*. *MinorVer*. *BuildNumber*. *Версия*)|  
|PDO::ATTR_ERRMODE|PDO|PDO::ERRMODE_SILENT<br /><br />PDO::ERRMODE_WARNING<br /><br />PDO::ERRMODE_EXCEPTION|Указывает способ обработки ошибок драйвером.<br /><br />PDO::ERRMODE_SILENT (используется по умолчанию) задает коды ошибок и сведения об ошибках.<br /><br />PDO::ERRMODE_WARNING вызывает E_WARNING.<br /><br />PDO::ERRMODE_EXCEPTION вызывает исключение.<br /><br />Этот атрибут также можно задать с помощью PDO::setAttribute.|  
|PDO::ATTR_ORACLE_NULLS|PDO|Обратитесь к документации по PDO.|Обратитесь к документации по PDO.|  
|PDO::ATTR_SERVER_INFO|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|Массив из 3 элементов|Возвращает текущую базу данных, версию SQL Server и экземпляр SQL Server.|  
|PDO::ATTR_SERVER_VERSION|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|Строковые значения|Указывает версию SQL Server (*основных*. *Дополнительный номер*. *BuildNumber*)|  
|PDO::ATTR_STRINGIFY_FETCHES|PDO|Обратитесь к документации по PDO.|Обратитесь к документации по PDO.|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|От 1 до предела памяти PHP.|Задает размер буфера, который содержит результирующий набор для клиентского курсора.<br /><br />Значение по умолчанию — базе 10240 КБ (10 МБ).<br /><br />Дополнительные сведения о клиентских курсорах см. в разделе [типы курсоров &#40;драйвер SQLSRV&#41;](../../connect/php/cursor-types-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true<br /><br />false|Задает выполнение прямого или подготовленного запроса. Дополнительные сведения см. в статье [Выполнение прямых и подготовленных инструкций в драйвере PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_ENCODING|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PDO::SQLSRV_ENCODING_UTF8<br /><br />PDO::SQLSRV_ENCODING_SYSTEM|Указывает кодировку, используемую драйвером для обмена данными с сервером.<br /><br />По умолчанию используется PDO::SQLSRV_ENCODING_UTF8.|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true или false|Обрабатывает числовые выборки из столбцов с числовыми типами SQL (бит, целое число со знаком, smallint, tinyint, float или real).<br /><br />Если включен флаг параметр подключения ATTR_STRINGIFY_FETCHES даже в том случае, если SQLSRV_ATTR_FETCHES_NUMERIC_TYPE имеет значение on, возвращаемое значение является строкой.<br /><br />Если возвращаемый тип PDO в столбце привязки PDO_PARAM_INT, возвращаемое значение целочисленного столбца является объектом типа int, даже если SQLSRV_ATTR_FETCHES_NUMERIC_TYPE отключен.|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|integer|Задает время ожидания выполнения запроса в секундах.<br /><br />По умолчанию используется значение 0, то есть драйвер ожидает результаты бесконечно долго.<br /><br />Отрицательные значения не допускаются.|  

  
PDO обрабатывает некоторые предопределенные атрибуты, оставляя обработку остальных драйверу. Все настраиваемые атрибуты и параметры соединения обрабатываются драйвером, неподдерживаемый атрибут или параметр соединения возвращает значение null.  
  
Поддержка PDO была добавлена в версии 2.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Пример  
Этот пример показывает значение атрибута PDO::ATTR_ERRMODE до и после изменения его значения.  
  
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
  
// An example using PDO::ATTR_CLIENT_VERSION  
print_r($conn->getAttribute( PDO::ATTR_CLIENT_VERSION ));  
?>  
```  
  
## <a name="see-also"></a>См. также  
[Класс PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
