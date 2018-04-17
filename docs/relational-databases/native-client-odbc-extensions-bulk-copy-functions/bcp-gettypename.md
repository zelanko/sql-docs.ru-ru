---
title: bcp_gettypename | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-extensions-bulk-copy-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_gettypename
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b0f600c2be78f3dde97581073cf0164daa366783
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
 *Маркер*  
 Значение, указывающее токен типа BCP.  
  
 *field*  
 Указывает, запрашивает ли токен тип max.  
  
## <a name="returns"></a>Возвращает  
 Строка, содержащая имя типа SQL, соответствующего типу BCP. Если указывается недопустимый тип BCP, возвращается пустая строка.  
  
## <a name="remarks"></a>Замечания  
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
|**SQLBIGCHAR**|Нет|**char**|  
|**SQLCHARACTER**|Нет|**char**|  
|**SQLBIGVARCHAR**|Нет|**varchar**|  
|**SQLVARCHAR**|Нет|**varchar**|  
|**SQLTEXT**|Допустим любой вариант|**text**|  
|**SQLBIGBINARY**|Нет|**binary**|  
|**SQLBINARY**|Нет|**Двоичный**|  
|**SQLBIGVARBINARY**|Нет|**varbinary**|  
|**SQLVARBINARY**|Нет|**varbinary**|  
|**SQLIMAGE**|Допустим любой вариант|**Изображение**|  
|**SQLINTN**|Допустим любой вариант|**int-null**|  
|**SQLDATETIMN**|Допустим любой вариант|**значение null типа DateTime**|  
|**SQLMONEYN**|Допустим любой вариант|**Money null**|  
|**SQLFLTN**|Допустим любой вариант|**число с плавающей запятой от null**|  
|**SQLAOPSUM**|Допустим любой вариант|**Sum**|  
|**SQLAOPAVG**|Допустим любой вариант|**Avg**|  
|**SQLAOPCNT**|Допустим любой вариант|**Count**|  
|**SQLAOPMIN**|Допустим любой вариант|**Min**|  
|**SQLAOPMAX**|Допустим любой вариант|**Max**|  
|**SQLDATETIM4**|Допустим любой вариант|**smalldatetime**|  
|**SQLMONEY4**|Допустим любой вариант|**smallmoney**|  
|**SQLFLT4**|Допустим любой вариант|**Real**|  
|**SQLUNIQUEID**|Допустим любой вариант|**uniqueidentifier**|  
|**SQLNCHAR**|Нет|**nchar**|  
|**SQLNVARCHAR**|Нет|**Nvarchar**|  
|**SQLNTEXT**|Допустим любой вариант|**ntext**|  
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
|**SQLUDT**|Допустим любой вариант|**определяемый пользователем тип**|  
  
## <a name="bcpgettypename-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_getcolfmt улучшенных возможностей работы с датой и временем  
 В столбце «Тип в файле sqlncli.h» в таблице описаны значения параметра токена для типов даты и времени [изменения массового копирования для улучшенной даты и времени &#40;OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). Возвращенное значение находится в соответствующей строке столбца «Тип хранения файла».  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования & #40; ODBC & #41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
