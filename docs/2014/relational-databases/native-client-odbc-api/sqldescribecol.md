---
title: SQLDescribeCol | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4def24dac95db8cf86d0a23bd1e0f7a951d4e9e0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054994"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
  Для выполненных инструкций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не требуется опрашивать сервер для описания столбцов результирующего набора. В этом случае `SQLDescribeCol` не вызывает обращения к серверу. Как и [SQLColAttribute](sqlnumresultcols.md), вызов `SQLDescribeCol` для подготовленных, но не выполненных инструкций приводит к обращению к серверу.  
  
 Когда инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] или пакет инструкций возвращает несколько результирующих наборов строк, то столбец, на который ссылается исходный столбец, можно создать в отдельной таблице или сослаться на абсолютно другой столбец результирующего набора. `SQLDescribeCol` должен вызываться для каждого набора. При изменении результирующего набора приложение должно осуществить повторную привязку значений данных перед выборкой результатов строк. Дополнительные сведения об обработке несколько результирующих наборов возвращает, см. в разделе [SQLMoreResults](sqlmoreresults.md).  
  
 Когда несколько результирующих наборов формируется подготовленным пакетом инструкций SQL, атрибуты столбцов сообщаются только для первого результирующего набора.  
  
 Для типов данных больших значений, значение, возвращаемое в *DataTypePtr* SQL_VARCHAR, SQL_VARBINARY или SQL_NVARCHAR. Значение SQL_SS_LENGTH_UNLIMITED в *ColumnSizePtr* указывает, что размер «unlimited».  
  
 Улучшения в ядро базы данных, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] разрешить SQLDescribeCol получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значения, возвращаемые методом SQLDescribeCol в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Обнаружение метаданных](../native-client/features/metadata-discovery.md).  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLDescribeCol улучшенных возможностей работы с данными в формате даты-времени  
 Для типов даты-времени возвращаются следующие значения.  
  
||*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|Дата|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>Поддержка функцией SQLDescribeCol определяемых пользователем типов больших данных CLR  
 Функция `SQLDescribeCol` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLDescribeCol, функция](http://go.microsoft.com/fwlink/?LinkID=59338)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
