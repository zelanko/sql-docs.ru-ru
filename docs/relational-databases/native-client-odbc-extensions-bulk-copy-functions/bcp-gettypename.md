---
title: bcp_gettypename | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_gettypename
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4e80c1703ece500e849a8c107d858222eea45f6f
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71707468"
---
# <a name="bcp_gettypename"></a>bcp_gettypename
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
 *Лекс*  
 Значение, указывающее токен типа BCP.  
  
 *field*  
 Указывает, запрашивает ли токен тип max.  
  
## <a name="returns"></a>Возвращает  
 Строка, содержащая имя типа SQL, соответствующего типу BCP. Если указывается недопустимый тип BCP, возвращается пустая строка.  
  
## <a name="remarks"></a>Примечания  
 Токены типа BCP определены в файле заголовка sqlncli.h и библиотеке sqlncli11.lib.  
  
 В следующей таблице указаны возможные типы BCP, независимо от того, являются ли они типами max или нет, а также ожидаемые выходные данные.  
  
|Имя типа BCP|MaxType|Output|  
|-------------------|-------------|------------|  
|**SQLDECIMAL**|Допустим любой вариант|**decimal**|  
|**SQLNUMERIC**|Допустим любой вариант|**numeric**|  
|**SQLINT1**|Допустим любой вариант|**tinyint**|  
|**SQLINT2**|Допустим любой вариант|**smallint**|  
|**SQLINT4**|Допустим любой вариант|**int**|  
|**SQLMONEY**|Допустим любой вариант|**money**|  
|**SQLFLT8**|Допустим любой вариант|**float**|  
|**SQLDATETIME**|Допустим любой вариант|**datetime**|  
|**СКЛБИТН**|Допустим любой вариант|**bit-null**|  
|**SQLBIT**|Допустим любой вариант|**bit**|  
|**SQLBIGCHAR**|Нет|**char**|  
|**SQLCHARACTER**|Нет|**char**|  
|**SQLBIGVARCHAR**|Нет|**varchar**|  
|**SQLVARCHAR**|Нет|**varchar**|  
|**SQLTEXT**|Допустим любой вариант|**text**|  
|**СКЛБИГБИНАРИ**|Нет|**binary**|  
|**SQLBINARY**|Нет|**Двоичный**|  
|**СКЛБИГВАРБИНАРИ**|Нет|**Varbinary**|  
|**SQLVARBINARY**|Нет|**Varbinary**|  
|**SQLIMAGE**|Допустим любой вариант|**Изображение**|  
|**СКЛИНТН**|Допустим любой вариант|**int-null**|  
|**СКЛДАТЕТИМН**|Допустим любой вариант|**DateTime — null**|  
|**СКЛМОНЭЙН**|Допустим любой вариант|**деньги — null**|  
|**SQLFLTN**|Допустим любой вариант|**float — null**|  
|**SQLAOPSUM**|Допустим любой вариант|**Sum**|  
|**SQLAOPAVG**|Допустим любой вариант|**Avg**|  
|**СКЛАОПКНТ**|Допустим любой вариант|**Count**|  
|**SQLAOPMIN**|Допустим любой вариант|**Min**|  
|**SQLAOPMAX**|Допустим любой вариант|**Max**|  
|**SQLDATETIM4**|Допустим любой вариант|**smalldatetime**|  
|**SQLMONEY4**|Допустим любой вариант|**Smallmoney**|  
|**SQLFLT4**|Допустим любой вариант|**Real**|  
|**SQLUNIQUEID**|Допустим любой вариант|**uniqueidentifier**|  
|**SQLNCHAR**|Нет|**Nchar**|  
|**SQLNVARCHAR**|Нет|**Nvarchar**|  
|**SQLNTEXT**|Допустим любой вариант|**Типы**|  
|**SQLVARIANT**|Допустим любой вариант|**sql_variant**|  
|**SQLINT8**|Допустим любой вариант|**Bigint**|  
|**SQLCHARACTER**|Да|**varchar(max)**|  
|**SQLBIGCHAR**|Да|**varchar(max)**|  
|**SQLBIGVARCHAR**|Да|**varchar(max)**|  
|**SQLVARCHAR**|Да|**varchar(max)**|  
|**SQLBINARY**|Да|**varbinary(max)**|  
|**СКЛБИГБИНАРИ**|Да|**varbinary(max)**|  
|**СКЛБИГВАРБИНАРИ**|Да|**varbinary(max)**|  
|**SQLVARBINARY**|Да|**varbinary(max)**|  
|**SQLNCHAR**|Да|**nvarchar(max)**|  
|**SQLNVARCHAR**|Да|**nvarchar(max)**|  
|**SQLXML**|Да|**Xml**|  
|**SQLUDT**|Допустим любой вариант|**Байт**|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_getcolfmt улучшенных возможностей работы с датой и временем  
 Значения параметров токена для типов даты-времени описаны в столбце "тип в sqlncli. h" таблицы в разделе "изменения при [операции копирования" для расширенных типов &#40;даты и времени OLE DB и&#41;ODBC](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). Возвращенное значение находится в соответствующей строке столбца «Тип хранения файла».  
  
 Дополнительные сведения см. в разделе [улучшения &#40;даты и времени&#41;ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
