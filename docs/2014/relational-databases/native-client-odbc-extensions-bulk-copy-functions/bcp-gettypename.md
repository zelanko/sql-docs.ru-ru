---
title: bcp_gettypename | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_gettypename
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5bc7caa063d14967e576fd009a23110b9647836b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62689031"
---
# <a name="bcpgettypename"></a>bcp_gettypename
  Возвращает имя типа SQL для указанного токена типа BCP.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_gettypename (  
INT   
token  
,  
DBBOOL   
fIsMaxType  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *Маркер*  
 Значение, указывающее токен типа BCP.  
  
 *field*  
 Указывает, запрашивает ли токен тип max.  
  
## <a name="returns"></a>Возвращает  
 Строка, содержащая имя типа SQL, соответствующего типу BCP. Если указывается недопустимый тип BCP, возвращается пустая строка.  
  
## <a name="remarks"></a>Примечания  
 Токены типа BCP определены в файле заголовка sqlncli.h и библиотеке sqlncli11.lib.  
  
 В следующей таблице указаны возможные типы BCP, независимо от того, являются ли они типами max или нет, а также ожидаемые выходные данные.  
  
|Имя типа BCP|MaxType|Вывод|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|Допустим любой вариант|**decimal**|  
|`SQLNUMERIC`|Допустим любой вариант|**numeric**|  
|`SQLINT1`|Допустим любой вариант|**tinyint**|  
|`SQLINT2`|Допустим любой вариант|**smallint**|  
|`SQLINT4`|Допустим любой вариант|**int**|  
|`SQLMONEY`|Допустим любой вариант|**money**|  
|`SQLFLT8`|Допустим любой вариант|**float**|  
|`SQLDATETIME`|Допустим любой вариант|**datetime**|  
|`SQLBITN`|Допустим любой вариант|**bit-null**|  
|`SQLBIT`|Допустим любой вариант|**bit**|  
|`SQLBIGCHAR`|Нет|**char**|  
|`SQLCHARACTER`|Нет|**char**|  
|`SQLBIGVARCHAR`|Нет|**varchar**|  
|`SQLVARCHAR`|Нет|**varchar**|  
|`SQLTEXT`|Допустим любой вариант|**text**|  
|`SQLBIGBINARY`|Нет|**binary**|  
|`SQLBINARY`|Нет|**Двоичный**|  
|`SQLBIGVARBINARY`|Нет|**varbinary**|  
|`SQLVARBINARY`|Нет|**varbinary**|  
|`SQLIMAGE`|Допустим любой вариант|**Изображение**|  
|`SQLINTN`|Допустим любой вариант|**int-null**|  
|`SQLDATETIMN`|Допустим любой вариант|**datetime-null**|  
|`SQLMONEYN`|Допустим любой вариант|**Money null**|  
|`SQLFLTN`|Допустим любой вариант|**число с плавающей запятой от null**|  
|`SQLAOPSUM`|Допустим любой вариант|**Sum**|  
|`SQLAOPAVG`|Допустим любой вариант|**Avg**|  
|`SQLAOPCNT`|Допустим любой вариант|**Count**|  
|`SQLAOPMIN`|Допустим любой вариант|**Min**|  
|`SQLAOPMAX`|Допустим любой вариант|**Max**|  
|`SQLDATETIM4`|Допустим любой вариант|**smalldatetime**|  
|`SQLMONEY4`|Допустим любой вариант|**smallmoney**|  
|`SQLFLT4`|Допустим любой вариант|**real**|  
|`SQLUNIQUEID`|Допустим любой вариант|**uniqueidentifier**|  
|`SQLNCHAR`|Нет|**nchar**|  
|`SQLNVARCHAR`|Нет|**Nvarchar**|  
|`SQLNTEXT`|Допустим любой вариант|**ntext**|  
|`SQLVARIANT`|Допустим любой вариант|**sql_variant**|  
|`SQLINT8`|Допустим любой вариант|**Bigint**|  
|`SQLCHARACTER`|Да|**varchar(max)**|  
|`SQLBIGCHAR`|Да|**varchar(max)**|  
|`SQLBIGVARCHAR`|Да|**varchar(max)**|  
|`SQLVARCHAR`|Да|**varchar(max)**|  
|`SQLBINARY`|Да|**varbinary(max)**|  
|`SQLBIGBINARY`|Да|**varbinary(max)**|  
|`SQLBIGVARBINARY`|Да|**varbinary(max)**|  
|`SQLVARBINARY`|Да|**varbinary(max)**|  
|`SQLNCHAR`|Да|**nvarchar(max)**|  
|`SQLNVARCHAR`|Да|**nvarchar(max)**|  
|`SQLXML`|Да|**Xml**|  
|`SQLUDT`|Допустим любой вариант|**определяемый пользователем тип**|  
  
## <a name="bcpgettypename-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_getcolfmt улучшенных возможностей работы с датой и временем  
 В столбце «Тип в SQLNCLI.h»» в таблице описаны значения параметра токена для типов даты времени [изменения массового копирования для типов усиленной даты и времени &#40;OLE DB и ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). Возвращенное значение находится в соответствующей строке столбца «Тип хранения файла».  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
