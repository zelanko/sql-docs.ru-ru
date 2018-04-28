---
title: sqlsrv_field_metadata | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
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
apiname:
- sqlsrv_field_metadata
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_field_metadata
- sqlsrv_field_metadata
ms.assetid: c02f6942-0484-4567-a78e-fe8aa2053536
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8b20b394beebd80b65a3a4f33b64242047d1c317
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlsrvfieldmetadata"></a>sqlsrv_field_metadata
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Извлекает метаданные для полей подготовленной инструкции. Дополнительные сведения о подготовке инструкции см. в статье [sqlsrv_query](../../connect/php/sqlsrv-query.md) или [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md). Обратите внимание, что **sqlsrv_field_metadata** можно вызвать для любой подготовленной инструкции до или после выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_field_metadata( resource $stmt)  
```  
  
#### <a name="parameters"></a>Параметры  
*$stmt*: ресурс инструкции, для полей которого выполняется поиск метаданных.  
  
## <a name="return-value"></a>Возвращаемое значение  
**Массив** массивов или значение **false**. Массив содержит один массив для каждого поля в результирующем наборе. Каждый подмассив имеет ключи, как описано в следующей таблице. Если при извлечении метаданных полей возникает ошибка, возвращается значение **false** .  
  
|Key|Описание|  
|-------|---------------|  
|Название|Имя столбца, которому соответствует поле.|  
|Тип|Числовое значение, соответствующее типу SQL.|  
|Размер|Число символов для полей символьного типа (char(n), varchar(n), nchar(n), nvarchar(n), XML). Число байтов для полей двоичного типа (binary(n), varbinary(n), UDT). Значение**NULL** для других типов данных SQL Server.|  
|Точность|Точность для типов переменной точности (real, numeric, decimal, datetime2, datetimeoffset и time). Значение**NULL** для других типов данных SQL Server.|  
|Масштаб|Масштаб для типов переменного масштаба (numeric, decimal, datetime2, datetimeoffset и time). Значение**NULL** для других типов данных SQL Server.|  
|Допускает значения NULL|Перечислимое значение, указывающее, является ли столбец значение NULL (**SQLSRV_NULLABLE_YES**), столбец не допускает значения NULL (**SQLSRV_NULLABLE_NO**), или оно неизвестно, допускает ли столбец значение NULL ( **SQLSRV_NULLABLE_UNKNOWN**).|  
  
Следующая таблица содержит дополнительные сведения о ключах для каждого подмассива (дополнительные сведения об этих типах см. в документации по SQL Server):  
  
|Тип данных SQL Server 2008|Тип|Минимальная/максимальная точность|Минимальный/максимальный масштаб|Размер|  
|-----------------------------|--------|----------------------|------------------|--------|  
|bigint|SQL_BIGINT (-5)|||8|  
|BINARY|SQL_BINARY (-2)|||0 < *n* < 8000 <sup>1</sup>|  
|bit|SQL_BIT (-7)||||  
|char;|SQL_CHAR (1)|||0 < *n* < 8000 <sup>1</sup>|  
|date|SQL_TYPE_DATE (91)|10/10|0/0||  
|datetime|SQL_TYPE_TIMESTAMP (93)|23/23|3/3||  
|datetime2|SQL_TYPE_TIMESTAMP (93)|19/27|0/7||  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET (-155)|26/34|0/7||  
|Decimal|SQL_DECIMAL (3)|1/38|0/значение точности||  
|float|SQL_FLOAT (6)|4/8|||  
|image|SQL_LONGVARBINARY (-4)|||2 GB|  
|int|SQL_INTEGER (4)||||  
|money|SQL_DECIMAL (3)|19/19|4/4||  
|NCHAR|SQL_WCHAR (-8)|||0 < *n* < 4000 <sup>1</sup>|  
|ntext|SQL_WLONGVARCHAR (-10)|||1 ГБ|  
|numeric|SQL_NUMERIC (2)|1/38|0/значение точности||  
|nvarchar|SQL_WVARCHAR (-9)|||0 < *n* < 4000 <sup>1</sup>|  
|real|SQL_REAL (7)|4/4|||  
|smalldatetime|SQL_TYPE_TIMESTAMP (93)|16/16|0/0||  
|smallint|SQL_SMALLINT (5)|||2 байта|  
|Smallmoney|SQL_DECIMAL (3)|10/10|4/4||  
|text|SQL_LONGVARCHAR (-1)|||2 GB|  
|time|SQL_SS_TIME2 (-154)|8/16|0/7||  
|TIMESTAMP|SQL_BINARY (-2)|||8 байт|  
|tinyint|SQL_TINYINT (-6)|||1 байт|  
|определяемый пользователем тип|SQL_SS_UDT (-151)|||переменная|  
|uniqueidentifier|SQL_GUID (-11)|||16|  
|varbinary|SQL_VARBINARY (-3)|||0 < *n* < 8000 <sup>1</sup>|  
|varchar|SQL_VARCHAR (12)|||0 < *n* < 8000 <sup>1</sup>|  
|xml|SQL_SS_XML (-152)|||0|  
  
(1) Нуль (0) указывает, что разрешен максимальный размер.  
  
Ключ Nullable может иметь значение yes или no.  
  
## <a name="example"></a>Пример  
Следующий пример создает ресурс инструкции, а затем извлекает и отображает метаданные полей. Предполагается, что SQL Server и [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) базы данных установлены на локальном компьютере. При выполнении примера из командной строки все выходные данные выводятся в консоль.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Prepare the statement. */  
$tsql = "SELECT ReviewerName, Comments FROM Production.ProductReview";  
$stmt = sqlsrv_prepare( $conn, $tsql);  
  
/* Get and display field metadata. */  
foreach( sqlsrv_field_metadata( $stmt) as $fieldMetadata)  
{  
      foreach( $fieldMetadata as $name => $value)  
      {  
           echo "$name: $value\n";  
      }  
      echo "\n";  
}  
  
/* Note: sqlsrv_field_metadata can be called on any statement  
resource, pre- or post-execution. */  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>См. также  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Константы (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  

[Информация о примерах кода в документации](../../connect/php/about-code-examples-in-the-documentation.md)  
  
