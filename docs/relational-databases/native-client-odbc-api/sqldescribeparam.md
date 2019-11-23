---
title: SQLDescribeParam | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: aa74f982a5ff1894651d68f06689cba476a16452
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73787103"
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Чтобы описать параметры любой инструкции SQL, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает и выполняет инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT при вызове SQLDescribeParam для подготовленного обработчика инструкции ODBC. Метаданные результирующего набора определяют характеристики параметров в подготовленной инструкции. SQLDescribeParam может возвращать любой код ошибки, который может возвращать SQLExecute или SQLExecDirect.  
  
 Улучшения в ядре СУБД, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] позволяют SQLDescribeParam получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значений, возвращаемых функцией SQLDescribeParam в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Metadata Discovery](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Кроме того, в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]*параметерсизептр* теперь возвращает значение, которое соответствует определению размера (в символах) столбца или выражения соответствующего маркера параметра, как определено в [спецификации ODBC](https://go.microsoft.com/fwlink/?LinkId=207044). В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client *параметерсизептр* может быть соответствующим значением **SQL_DESC_OCTET_LENGTH** для типа или неопределенного значения размера столбца, переданного SQLBindParameter для типа, значение, которое следует игнорировать (например,**SQL_INTEGER**).  
  
 Драйвер не поддерживает вызов SQLDescribeParam в следующих ситуациях:  
  
-   После SQLExecDirect для всех инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE или DELETE, содержащих предложение FROM.  
  
-   Для любой инструкции ODBC или [!INCLUDE[tsql](../../includes/tsql-md.md)], содержащей параметр в предложении HAVING, или сравниваемой с результатом функции SUM.  
  
-   Для любой инструкции ODBC или [!INCLUDE[tsql](../../includes/tsql-md.md)], зависящей от вложенного запроса, который содержит параметры.  
  
-   Для инструкций ODBC SQL, содержащих маркеры параметров в обоих сравниваемых выражениях или содержащих предикат с квантором.  
  
-   Для любых запросов, в которых один из параметров является параметром функции.  
  
-   При наличии комментариев (/* \*/) в команде [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 При обработке пакета [!INCLUDE[tsql](../../includes/tsql-md.md)]ных инструкций драйвер также не поддерживает вызов SQLDescribeParam для маркеров параметров в инструкциях после первой инструкции в пакете.  
  
 При описании параметров подготовленных хранимых процедур SQLDescribeParam использует системную хранимую процедуру [sp_sproc_columns](../../relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql.md) для получения характеристик параметров. sp_sproc_columns может сообщать данные о хранимых процедурах в текущей пользовательской базе данных. Подготовка полного имени хранимой процедуры позволяет выполнять SQLDescribeParam между базами данных. Например, системная хранимая процедура [sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) может быть подготовлена и выполнена в любой базе данных следующим образом:  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 Выполнение SQLDescribeParam после успешной подготовки возвращает пустой набор строк при подключении к любой базе данных, но **master**. Тот же вызов, подготовленный следующим образом, приводит к тому, что SQLDescribeParam будет выполнен, независимо от текущей пользовательской базы данных:  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 Для типов данных больших значений значение, возвращаемое в *дататипептр* , SQL_VARCHAR, SQL_VARBINARY или SQL_NVARCHAR. Чтобы указать, что для параметра типа данных больших значений задано значение "unlimited", [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента устанавливает *параметерсизептр* в значение 0. Фактические значения размера возвращаются для стандартных параметров **varchar** .  
  
> [!NOTE]  
>  Если параметр уже был привязан к максимальному размеру (для параметров типа SQL_VARCHAR, SQL_VARBINARY или SQL_WVARCHAR), возвращается привязанный размер параметра, а не «unlimited».  
  
 Чтобы привязать входной параметр размера «unlimited», необходимо использовать данные времени выполнения. Невозможно привязать выходной параметр "неограниченный" размер (нет метода для потоковой передачи данных из выходного параметра, например [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) для результирующих наборов).  
  
 Для выходных параметров буфер должен быть привязан, и, если значение слишком длинное, буфер заполняется, и возвращается сообщение SQL_SUCCESS_WITH_INFO с предупреждением «строковые данные; усечение справа». Данные, которые были усечены, затем отбрасываются.  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>Функция SQLDescribeParam и возвращающие табличные значения параметры  
 Приложение может получить сведения о возвращающем табличное значение параметре для подготовленной инструкции с помощью SQLDescribeParam. Дополнительные сведения см. в разделе [метаданные возвращающего табличное значение параметра для подготовленных инструкций](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметрах см. в разделе табличные [Параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>Поддержка в функции SQLDescribeParam улучшенных возможностей даты-времени  
 Для типов даты-времени возвращаются следующие значения.  
  
||*дататипептр*|*параметерсизептр*|*DecimalDigitsPtr*|  
|-|-------------------|------------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|DATE|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Дополнительные сведения см. в разделе [улучшения &#40;даты и времени&#41;ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>Поддержка в функции SQLDescribeParam определяемых пользователем типов больших данных CLR  
 **SQLDescribeParam** поддерживает большие определяемые пользователем типы данных CLR (UDT). Дополнительные сведения см. в разделе [типы больших определяемых пользователем &#40;типов&#41;данных CLR ODBC](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также статью  
   [функции SQLDescribeParam](https://go.microsoft.com/fwlink/?LinkId=59339)  
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
