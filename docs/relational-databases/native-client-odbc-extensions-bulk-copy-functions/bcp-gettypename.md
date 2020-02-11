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
ms.openlocfilehash: d2752a1708c5727567de470b49d4cbcc63f90923
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73782655"
---
# <a name="bcp_gettypename"></a>bcp_gettypename
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

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
  
 *полями*  
 Указывает, запрашивает ли токен тип max.  
  
## <a name="returns"></a>Возвращает  
 Строка, содержащая имя типа SQL, соответствующего типу BCP. Если указывается недопустимый тип BCP, возвращается пустая строка.  
  
## <a name="remarks"></a>Remarks  
 Токены типа BCP определены в файле заголовка sqlncli.h и библиотеке sqlncli11.lib.  
  
 В следующей таблице указаны возможные типы BCP, независимо от того, являются ли они типами max или нет, а также ожидаемые выходные данные.  
  
|Имя типа BCP|MaxType|Выходные данные|  
|-------------------|-------------|------------|  
|**SQLDECIMAL**|Можно использовать|**Decimal**|  
|**SQLNUMERIC**|Можно использовать|**ISNUMERIC**|  
|**SQLINT1**|Можно использовать|**tinyint**|  
|**SQLINT2**|Можно использовать|**smallint**|  
|**SQLINT4**|Можно использовать|**int**|  
|**SQLMONEY**|Можно использовать|**money**|  
|**SQLFLT8**|Можно использовать|**float**|  
|**SQLDATETIME**|Можно использовать|**datetime**|  
|**SQLBITN**|Можно использовать|**bit-null**|  
|**SQLBIT**|Можно использовать|**bit**|  
|**SQLBIGCHAR**|нет|**типа**|  
|**SQLCHARACTER**|нет|**типа**|  
|**SQLBIGVARCHAR**|нет|**varchar**|  
|**SQLVARCHAR**|нет|**varchar**|  
|**SQLTEXT**|Можно использовать|**полнотекстовым**|  
|**SQLBIGBINARY**|нет|**binary**|  
|**SQLBINARY**|нет|**Двоичный**|  
|**SQLBIGVARBINARY**|нет|**Varbinary**|  
|**SQLVARBINARY**|нет|**Varbinary**|  
|**SQLIMAGE**|Можно использовать|**Изображение**|  
|**SQLINTN**|Можно использовать|**int-null**|  
|**SQLDATETIMN**|Можно использовать|**datetime-null**|  
|**SQLMONEYN**|Можно использовать|**money-null**|  
|**SQLFLTN**|Можно использовать|**float-null**|  
|**склаопсум**|Можно использовать|**Функции**|  
|**склаопавг**|Можно использовать|**Обращения**|  
|**склаопкнт**|Можно использовать|**Расчета**|  
|**склаопмин**|Можно использовать|**Минимум**|  
|**склаопмакс**|Можно использовать|**Максимальной**|  
|**SQLDATETIM4**|Можно использовать|**smalldatetime**|  
|**SQLMONEY4**|Можно использовать|**Smallmoney**|  
|**SQLFLT4**|Можно использовать|**Real**|  
|**SQLUNIQUEID**|Можно использовать|**UNIQUEIDENTIFIER**|  
|**SQLNCHAR**|нет|**Nchar**|  
|**SQLNVARCHAR**|нет|**Nvarchar**|  
|**SQLNTEXT**|Можно использовать|**Типы**|  
|**SQLVARIANT**|Можно использовать|**sql_variant**|  
|**SQLINT8**|Можно использовать|**Bigint**|  
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
|**SQLXML**|Да|**Код**|  
|**SQLUDT**|Можно использовать|**Байт**|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a>Поддержка функцией bcp_getcolfmt улучшенных возможностей работы с датой и временем  
 Значения параметров токена для типов даты-времени описаны в столбце "тип в sqlncli. h" таблицы в разделе "изменения при [операции копирования для расширенных типов даты и времени" &#40;OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). Возвращенное значение находится в соответствующей строке столбца «Тип хранения файла».  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
