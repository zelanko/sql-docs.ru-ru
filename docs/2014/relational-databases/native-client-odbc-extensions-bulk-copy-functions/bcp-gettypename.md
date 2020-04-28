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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62689031"
---
# <a name="bcp_gettypename"></a>bcp_gettypename
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
 *token*  
 Значение, указывающее токен типа BCP.  
  
 *поле*  
 Указывает, запрашивает ли токен тип max.  
  
## <a name="returns"></a>Результаты  
 Строка, содержащая имя типа SQL, соответствующего типу BCP. Если указывается недопустимый тип BCP, возвращается пустая строка.  
  
## <a name="remarks"></a>Remarks  
 Токены типа BCP определены в файле заголовка sqlncli.h и библиотеке sqlncli11.lib.  
  
 В следующей таблице указаны возможные типы BCP, независимо от того, являются ли они типами max или нет, а также ожидаемые выходные данные.  
  
|Имя типа BCP|MaxType|Выходные данные|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|Можно использовать|**decimal**|  
|`SQLNUMERIC`|Можно использовать|**numeric**|  
|`SQLINT1`|Можно использовать|**tinyint**|  
|`SQLINT2`|Можно использовать|**smallint**|  
|`SQLINT4`|Можно использовать|**int**|  
|`SQLMONEY`|Можно использовать|**money**|  
|`SQLFLT8`|Можно использовать|**float**|  
|`SQLDATETIME`|Можно использовать|**datetime**|  
|`SQLBITN`|Можно использовать|**bit-null**|  
|`SQLBIT`|Можно использовать|**bit**|  
|`SQLBIGCHAR`|Нет|**char**|  
|`SQLCHARACTER`|Нет|**char**|  
|`SQLBIGVARCHAR`|Нет|**varchar**|  
|`SQLVARCHAR`|Нет|**varchar**|  
|`SQLTEXT`|Можно использовать|**text**|  
|`SQLBIGBINARY`|Нет|**binary**|  
|`SQLBINARY`|Нет|**Двоичный**|  
|`SQLBIGVARBINARY`|Нет|**Varbinary**|  
|`SQLVARBINARY`|Нет|**Varbinary**|  
|`SQLIMAGE`|Можно использовать|**ОС контейнера**|  
|`SQLINTN`|Можно использовать|**int-null**|  
|`SQLDATETIMN`|Можно использовать|**datetime-null**|  
|`SQLMONEYN`|Можно использовать|**money-null**|  
|`SQLFLTN`|Можно использовать|**float-null**|  
|`SQLAOPSUM`|Можно использовать|**Функции**|  
|`SQLAOPAVG`|Можно использовать|**Обращения**|  
|`SQLAOPCNT`|Можно использовать|**Count**|  
|`SQLAOPMIN`|Можно использовать|**Минимум**|  
|`SQLAOPMAX`|Можно использовать|**Максимальной**|  
|`SQLDATETIM4`|Можно использовать|**smalldatetime**|  
|`SQLMONEY4`|Можно использовать|**Smallmoney**|  
|`SQLFLT4`|Можно использовать|**Real**|  
|`SQLUNIQUEID`|Можно использовать|**uniqueidentifier**|  
|`SQLNCHAR`|Нет|**Nchar**|  
|`SQLNVARCHAR`|Нет|**Nvarchar**|  
|`SQLNTEXT`|Можно использовать|**Типы**|  
|`SQLVARIANT`|Можно использовать|**sql_variant**|  
|`SQLINT8`|Можно использовать|**Bigint**|  
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
|`SQLXML`|Да|**Код**|  
|`SQLUDT`|Можно использовать|**Байт**|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_getcolfmt улучшенных возможностей работы с датой и временем  
 Значения параметров токена для типов даты-времени описаны в столбце "тип в sqlncli. h" таблицы в разделе "изменения при [операции копирования для расширенных типов даты и времени" &#40;OLE DB и ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). Возвращенное значение находится в соответствующей строке столбца «Тип хранения файла».  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
