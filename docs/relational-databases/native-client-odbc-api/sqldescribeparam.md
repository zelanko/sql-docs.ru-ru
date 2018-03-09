---
title: "SQLDescribeParam | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1e1f4ce5630728cb33e98f389dd1e65a02f6178c
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="sqldescribeparam"></a>SQLDescribeParam
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Для описания параметров любой инструкции SQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента строит и выполняет [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции SELECT при вызове SQLDescribeParam на дескрипторе подготовленной инструкции ODBC. Метаданные результирующего набора определяют характеристики параметров в подготовленной инструкции. SQLDescribeParam может возвращать любой код ошибки, которая может возвращать SQLExecute или SQLExecDirect.  
  
 Усовершенствования в компоненте database engine, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] разрешить SQLDescribeParam получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значения, возвращаемые методом SQLDescribeParam в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Metadata Discovery](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Кроме того, новые возможности [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *ParameterSizePtr* теперь возвращает значение, которое выравнивает с определением размера, в символах, столбца или выражения соответствующего маркера параметра, как определено в [ODBC Спецификация](http://go.microsoft.com/fwlink/?LinkId=207044). В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client *ParameterSizePtr* может быть соответствующим значением **SQL_DESC_OCTET_LENGTH** для типа или несоответствующее значение размера столбца, предоставленным в SQLBindParameter для типа, значение которого следует игнорировать (**SQL_INTEGER**, например).  
  
 Драйвер не поддерживает вызывающий SQLDescribeParam в следующих ситуациях:  
  
-   После SQLExecDirect для любого [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций UPDATE или DELETE, содержащих предложение FROM.  
  
-   Для любой инструкции ODBC или [!INCLUDE[tsql](../../includes/tsql-md.md)], содержащей параметр в предложении HAVING, или сравниваемой с результатом функции SUM.  
  
-   Для любой инструкции ODBC или [!INCLUDE[tsql](../../includes/tsql-md.md)], зависящей от вложенного запроса, который содержит параметры.  
  
-   Для инструкций ODBC SQL, содержащих маркеры параметров в обоих сравниваемых выражениях или содержащих предикат с квантором.  
  
-   Для любых запросов, в которых один из параметров является параметром функции.  
  
-   Если есть комментарии (/ * \*/) в [!INCLUDE[tsql](../../includes/tsql-md.md)] команды.  
  
 При обработке пакета [!INCLUDE[tsql](../../includes/tsql-md.md)] операторы, драйвер также не поддерживает вызов функции SQLDescribeParam для маркеров параметров в инструкциях после первой инструкцией в пакете.  
  
 При описании параметров подготовленных хранимых процедур, SQLDescribeParam использует системную хранимую процедуру [sp_sproc_columns](../../relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql.md) для получения характеристик параметра. sp_sproc_columns может передать данные для хранимых процедур внутри текущей базы данных пользователя. Подготовка имя полного имени хранимой процедуры позволяет SQLDescribeParam выполняться в нескольких базах данных. Например, системная хранимая процедура [sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) может быть подготовлена и выполнена в любой базе данных, как:  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 Выполнение SQLDescribeParam после удачной подготовки возвращает пустой набор строк при подключении к любой базе данных, но **master**. Тот же вызов, подготовленный следующим образом, в результате SQLDescribeParam для успешного выполнения независимо от текущей базы данных пользователя:  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 Для типов данных больших значений, значение, возвращаемое в *DataTypePtr* SQL_VARCHAR, SQL_VARBINARY или SQL_NVARCHAR. Чтобы указать, что размер параметра типа данных больших значений является «unlimited» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задает драйвер ODBC для собственного клиента *ParameterSizePtr* значение 0. Значения фактического размера возвращаются для стандартных **varchar** параметров.  
  
> [!NOTE]  
>  Если параметр уже был привязан к максимальному размеру (для параметров типа SQL_VARCHAR, SQL_VARBINARY или SQL_WVARCHAR), возвращается привязанный размер параметра, а не «unlimited».  
  
 Чтобы привязать входной параметр размера «unlimited», необходимо использовать данные времени выполнения. Не удается привязать выходной параметр размера «unlimited» (нет метода для потоковой передачи данных из выходного параметра, как [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) происходит результирующими наборами).  
  
 Для выходных параметров буфер должен быть привязан, и, если значение слишком длинное, буфер заполняется, и возвращается сообщение SQL_SUCCESS_WITH_INFO с предупреждением «строковые данные; усечение справа». Данные, которые были усечены, затем отбрасываются.  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a>Функция SQLDescribeParam и возвращающие табличные значения параметры  
 Приложение может получать сведения о возвращающих табличные значения параметров для подготовленной инструкции с SQLDescribeParam. Дополнительные сведения см. в разделе [метаданные возвращающего табличное значение параметра для подготовленных инструкций](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров в целом. в разделе [табличное значение параметры &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a>Поддержка в функции SQLDescribeParam улучшенных возможностей даты-времени  
 Для типов даты-времени возвращаются следующие значения.  
  
||*DataTypePtr*|*ParameterSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|------------------------|------------------------|  
|datetime|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|date|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a>Поддержка в функции SQLDescribeParam определяемых пользователем типов больших данных CLR  
 **SQLDescribeParam** поддерживает большие определяемые пользователем типы (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLDescribeParam](http://go.microsoft.com/fwlink/?LinkId=59339)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
