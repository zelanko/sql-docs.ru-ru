---
title: СЗЛООперепарам (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: efe1fdccbef4f5c4a393083f6eb81efee759be5c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302595"
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Чтобы описать параметры любого оператора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] S'L, драйвер Native Client [!INCLUDE[tsql](../../includes/tsql-md.md)] ODBC создает и выполняет заявление SELECT, когда s'LDescribeParam вызывается на подготовленную ручку оператора ODBC. Метаданные результирующего набора определяют характеристики параметров в подготовленной инструкции. СЗЛОСтерипарам может вернуть любой код ошибки, который может вернуться s'LLExecute' или S'LExecDirect.  
  
 Улучшения в движке [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] базы данных, начиная с позволяют S'LDescribeParam получить более точное описание ожидаемых результатов. Эти более точные результаты могут отличаться от значений, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]возвращенных S'LDescribeParam в предыдущих версиях . Дополнительные сведения см. в разделе [Обнаружение метаданных](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Также новое [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]в , *ParameterSizePtr* теперь возвращает значение, которое соответствует определению для размера, в символах, столбца или выражения соответствующего маркера параметра, как это определено в [спецификации ODBC.](https://go.microsoft.com/fwlink/?LinkId=207044) В предыдущих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версиях Native *Client, ParameterSizePtr* может быть соответствующим значением **SQL_DESC_OCTET_LENGTH** для типа, или нерелевантным значением размера столбца, которое было поставлено в S'LBindParameter для типа, значение которого должно быть проигнорировано **(SQL_INTEGER,** например).  
  
 Водитель не поддерживает вызов S'LDescribeParam в следующих ситуациях:  
  
-   После S'LExecDirect [!INCLUDE[tsql](../../includes/tsql-md.md)] для любых обновлений или DELETE заявлений, содержащих оговорку FROM.  
  
-   Для любой инструкции ODBC или [!INCLUDE[tsql](../../includes/tsql-md.md)], содержащей параметр в предложении HAVING, или сравниваемой с результатом функции SUM.  
  
-   Для любой инструкции ODBC или [!INCLUDE[tsql](../../includes/tsql-md.md)], зависящей от вложенного запроса, который содержит параметры.  
  
-   Для инструкций ODBC SQL, содержащих маркеры параметров в обоих сравниваемых выражениях или содержащих предикат с квантором.  
  
-   Для любых запросов, в которых один из параметров является параметром функции.  
  
-   При наличии комментариев \*(//)в [!INCLUDE[tsql](../../includes/tsql-md.md)] команде.  
  
 При обработке [!INCLUDE[tsql](../../includes/tsql-md.md)] партии выписок драйвер также не поддерживает вызов S'LDescribeParam для маркеров параметров в операторах после первого оператора в пакете.  
  
 При описании параметров подготовленных сохраненных процедур, SLDescribeParam использует сохраненную систему процедуры [sp_sproc_columns](../../relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql.md) для получения параметрических характеристик. sp_sproc_columns могут сообщать данные для сохраненных процедур в текущей базе данных пользователей. Подготовка полностью квалифицированного сохраненного названия процедур ы позволяет S'LDescribeParam выполняться в базах данных. Например, процедура хранения системы [sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) может быть подготовлена и выполнена в любой базе данных, как:  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 Выполнение S'LDescribeParam после успешной подготовки возвращает набор пустой строки при подключении к любой базе данных, кроме **мастера.** Тот же вызов, подготовленный следующим образом, приводит к успеху S'LDescribeParam независимо от текущей базы данных пользователей:  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 Для типов больших значений значения, возвращенные в *DataTypePtr,* SQL_VARCHAR, SQL_VARBINARY или SQL_NVARCHAR. Чтобы указать, что размер параметра типа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] большого значения является "неограниченным", драйвер Native Client ODBC устанавливает *ParameterSizePtr* до 0. Фактические значения размера возвращаются для стандартных параметров **varchar.**  
  
> [!NOTE]  
>  Если параметр уже был привязан к максимальному размеру (для параметров типа SQL_VARCHAR, SQL_VARBINARY или SQL_WVARCHAR), возвращается привязанный размер параметра, а не «unlimited».  
  
 Чтобы привязать входной параметр размера «unlimited», необходимо использовать данные времени выполнения. Связать параметр вывода "неограниченного" размера невозможно (нет метода потоковой передачи данных из параметра вывода, как это делает [s'LGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) для наборов результатов).  
  
 Для выходных параметров буфер должен быть привязан, и, если значение слишком длинное, буфер заполняется, и возвращается сообщение SQL_SUCCESS_WITH_INFO с предупреждением «строковые данные; усечение справа». Данные, которые были усечены, затем отбрасываются.  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>Функция SQLDescribeParam и возвращающие табличные значения параметры  
 Приложение может получить информацию о параметрах, оцениваемых в таблице, для подготовленного заявления с помощью S'LDescribeParam. Для получения дополнительной [Table-Valued Parameter Metadata for Prepared Statements](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md)информации см.  
  
 Для получения дополнительной информации о параметрах, ценных на таблицу в целом, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>Поддержка в функции SQLDescribeParam улучшенных возможностей даты-времени  
 Для типов даты-времени возвращаются следующие значения.  
  
||*DataTypePtr*|*ParameterSizePtr*|*ДесятичнаяДияпТр*|  
|-|-------------------|------------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|Дата|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Для получения дополнительной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>Поддержка в функции SQLDescribeParam определяемых пользователем типов больших данных CLR  
 **S'LDescribeParam** поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Функция «СЗЛОописаниеПарам»](https://go.microsoft.com/fwlink/?LinkId=59339)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
