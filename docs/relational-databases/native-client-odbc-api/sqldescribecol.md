---
title: СЗЛООКоКоль Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e0e9a03b2e8635618afbdc615a6f77dfe05c533e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302591"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для выполнения инструкций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйверу Native Client ODBC не нужно запросить сервер для описания столбцов в наборе результатов. В этом **случае, S'LDescribeCol** не вызывает сервер туда и обратно. Как и [s'LColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)и[S'LNumResultCols,](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)вызов **S'LDescribeCol** на подготовленные, но не выполненные операторы генерирует сервер туда и обратно.  
  
 Когда инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] или пакет инструкций возвращает несколько результирующих наборов строк, то столбец, на который ссылается исходный столбец, можно создать в отдельной таблице или сослаться на абсолютно другой столбец результирующего набора. Для каждого набора следует вызывать **s'LDescribeCol.** При изменении результирующего набора приложение должно осуществить повторную привязку значений данных перед выборкой результатов строк. Дополнительные сведения об обработке запросов, возвращающих несколько результирующих наборов, см. в разделе [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Когда несколько результирующих наборов формируется подготовленным пакетом инструкций SQL, атрибуты столбцов сообщаются только для первого результирующего набора.  
  
 Для типов больших значений значения, возвращенные в *DataTypePtr,* SQL_VARCHAR, SQL_VARBINARY или SQL_NVARCHAR. Значение SQL_SS_LENGTH_UNLIMITED в *ColumnSizePtr* указывает на то, что размер является "неограниченным".  
  
 Улучшения в движке [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] базы данных, начиная с позволяют S'LDescribeCol получить более точное описание ожидаемых результатов. Эти более точные результаты могут отличаться от значений, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]возвращенных S'LDescribeCol в предыдущих версиях. Дополнительные сведения см. в разделе [Обнаружение метаданных](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLDescribeCol улучшенных возможностей работы с данными в формате даты-времени  
 Для типов даты-времени возвращаются следующие значения.  
  
||*DataTypePtr*|*ColumnSizePtr*|*ДесятичнаяДияпТр*|  
|-|-------------------|---------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|Дата|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Для получения дополнительной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>Поддержка функцией SQLDescribeCol определяемых пользователем типов больших данных CLR  
 **S'LDescribeCol** поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Функция «СЗЛОописаниекол»](https://go.microsoft.com/fwlink/?LinkID=59338)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
