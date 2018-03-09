---
title: "bcp_gettypename | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: bcp_gettypename
apilocation: sqlncli11.dll
apitype: DLLExport
helpviewer_keywords: bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
caps.latest.revision: "31"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ccb5d8652421aa0d52fd941e99cbcd01a0cfb6b2
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="bcpgettypename"></a>bcp_gettypename
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Возвращает имя типа SQL для указанного токена типа BCP.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_gettypename (  
        INT token,  
        DBBOOL fIsMaxType);  
```  
  
## <a name="arguments"></a>Аргументы  
 *token*  
 Значение, указывающее токен типа BCP.  
  
 *field*  
 Указывает, запрашивает ли токен тип max.  
  
## <a name="returns"></a>Возвращает  
 Строка, содержащая имя типа SQL, соответствующего типу BCP. Если указывается недопустимый тип BCP, возвращается пустая строка.  
  
## <a name="remarks"></a>Remarks  
 Токены типа BCP определены в файле заголовка sqlncli.h и библиотеке sqlncli11.lib.  
  
 В следующей таблице указаны возможные типы BCP, независимо от того, являются ли они типами max или нет, а также ожидаемые выходные данные.  
  
|Имя типа BCP|MaxType|Вывод|  
|-------------------|-------------|------------|  
|**SQLDECIMAL**|Допустим любой вариант|**decimal**|  
|**SQLNUMERIC**|Допустим любой вариант|**numeric**|  
|**SQLINT1**|Допустим любой вариант|**tinyint**|  
|**SQLINT2**|Допустим любой вариант|**smallint**|  
|**SQLINT4**|Допустим любой вариант|**int**|  
|**SQLMONEY**|Допустим любой вариант|**money**|  
|**SQLFLT8**|Допустим любой вариант|**float**|  
|**SQLDATETIME**|Допустим любой вариант|**datetime**|  
|**SQLBITN**|Допустим любой вариант|**bit-null**|  
|**SQLBIT**|Допустим любой вариант|**бит**|  
|**SQLBIGCHAR**|нет|**char**|  
|**SQLCHARACTER**|нет|**char**|  
|**SQLBIGVARCHAR**|нет|**varchar**|  
|**SQLVARCHAR**|нет|**varchar**|  
|**SQLTEXT**|Допустим любой вариант|**text**|  
|**SQLBIGBINARY**|нет|**binary**|  
|**SQLBINARY**|нет|**Двоичный**|  
|**SQLBIGVARBINARY**|нет|**Varbinary**|  
|**SQLVARBINARY**|нет|**Varbinary**|  
|**SQLIMAGE**|Допустим любой вариант|**Изображение**|  
|**SQLINTN**|Допустим любой вариант|**int-null**|  
|**SQLDATETIMN**|Допустим любой вариант|**datetime-null**|  
|**SQLMONEYN**|Допустим любой вариант|**money-null**|  
|**SQLFLTN**|Допустим любой вариант|**float-null**|  
|**SQLAOPSUM**|Допустим любой вариант|**Sum**|  
|**SQLAOPAVG**|Допустим любой вариант|**Avg**|  
|**SQLAOPCNT**|Допустим любой вариант|**Count**|  
|**SQLAOPMIN**|Допустим любой вариант|**Min**|  
|**SQLAOPMAX**|Допустим любой вариант|**Max**|  
|**SQLDATETIM4**|Допустим любой вариант|**smalldatetime**|  
|**SQLMONEY4**|Допустим любой вариант|**Smallmoney**|  
|**SQLFLT4**|Допустим любой вариант|**Real**|  
|**SQLUNIQUEID**|Допустим любой вариант|**uniqueidentifier**|  
|**SQLNCHAR**|нет|**Nchar**|  
|**SQLNVARCHAR**|нет|**Nvarchar**|  
|**SQLNTEXT**|Допустим любой вариант|**Ntext**|  
|**SQLVARIANT**|Допустим любой вариант|**sql_variant**|  
|**SQLINT8**|Допустим любой вариант|**Bigint**|  
|**SQLCHARACTER**|Да|**varchar(max)**|  
|**SQLBIGCHAR**|Да|**varchar(max)**|  
|**SQLBIGVARCHAR**|Да|**varchar(max)**|  
|**SQLVARCHAR**|Да|**varchar(max)**|  
|**SQLBINARY**|Да|**varbinary(max)**|  
|**SQLBIGBINARY**|Да|**varbinary(max)**|  
|**SQLBIGVARBINARY**|Да|**varbinary(max)**|  
|**SQLVARBINARY**|Да|**varbinary(max)**|  
|**SQLNCHAR**|Да|**nvarchar(max)**|  
|**SQLNVARCHAR**|Да|**nvarchar(max)**|  
|**SQLXML**|Да|**Xml**|  
|**SQLUDT**|Допустим любой вариант|**Определяемый пользователем тип**|  
  
## <a name="bcpgettypename-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_getcolfmt улучшенных возможностей работы с датой и временем  
 В столбце «Тип в файле sqlncli.h» в таблице описаны значения параметра токена для типов даты и времени [изменения массового копирования для улучшенной даты и времени типы &#40; OLE DB и ODBC &#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). Возвращенное значение находится в соответствующей строке столбца «Тип хранения файла».  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
