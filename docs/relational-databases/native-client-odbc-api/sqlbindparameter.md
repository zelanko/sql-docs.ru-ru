---
title: "SQLBindParameter | Документы Microsoft"
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
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6eceb24668a73eb94224f2c4d6f09f272595a92a
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="sqlbindparameter"></a>SQLBindParameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLBindParameter** могут исключить необходимость преобразования данных при использовании для предоставления данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента, что приводит к значительному выигрышу в производительности для компонентов клиента и сервера приложений. Другие преимущества — снижение потери точности при вставке или изменении приблизительных числовых типов данных.  
  
> [!NOTE]  
>  При вставке **char** и **wchar** используется тип данных в столбец типа image, объем данных, передаваемых в отличие от объема данных после преобразования в двоичный формат.  
  
 Если ODBC-драйвер для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сталкивается с ошибкой при обработке одного элемента в массиве параметров, драйвер продолжит выполнение инструкции для всех остальных элементов массива.  Если приложение выполнило привязку массива элементов параметров состояния, то строки параметров, которые вызвали ошибку, можно определить по массиву.  
  
 При использовании ODBC-драйвера для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время привязки входных параметров задавайте значение SQL_PARAM_INPUT. Значения SQL_PARAM_OUTPUT и SQL_PARAM_INPUT_OUTPUT следует задавать только для привязки параметров хранимой процедуры, для которых указано ключевое слово OUTPUT.  
  
 [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md) ненадежный с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента, если элемент массива в массиве привязанных параметров вызывает ошибку при выполнении инструкции. Атрибут инструкции ODBC SQL_ATTR_PARAMS_PROCESSED_PTR возвращает число строк, обработанных до возникновения ошибки. Затем при необходимости приложение может просмотреть массив состояний параметров, чтобы выяснить количество успешно выполненных инструкций.  
  
## <a name="binding-parameters-for-sql-character-types"></a>Привязка параметров для символьных типов SQL  
 Если тип данных SQL, переданный в символьный тип *ColumnSize* — это размер в символах (не байтов). Если длина строки данных в байтах превышает 8000, *ColumnSize* должно быть присвоено **SQL_SS_LENGTH_UNLIMITED**, указывающее на отсутствие ограничений на размер типа SQL.  
  
 Например если тип данных SQL **SQL_WVARCHAR**, *ColumnSize* не должно быть больше 4000. Если фактическая длина данных превышает 4000, затем *ColumnSize* должно быть присвоено **SQL_SS_LENGTH_UNLIMITED** , чтобы **nvarchar(max)** будет использоваться драйвером.  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>Параметр SQLBindParameter и возвращающие табличные значения параметры  
 Как другие типы параметров возвращающих табличные значения параметров привязываются по SQLBindParameter.  
  
 После привязки возвращающего табличное значение параметра его столбцы также оказываются привязанными. Для привязки столбцов необходимо вызвать [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) присваивающий параметру SQL_SOPT_SS_PARAM_FOCUS порядковый номер возвращающего табличное значение параметра. Затем вызовите метод SQLBindParameter для каждого столбца в возвращающих табличные значения параметра. Для возвращения к высокоуровневой привязке параметров задайте для SQL_SOPT_SS_PARAM_FOCUS значение 0.  
  
 Сведения о сопоставлении параметров с дескрипторами полей для возвращающих табличные значения параметров см. в разделе [привязки и Data Transfer of Table-Valued параметры и значения столбцов](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>Поддержка метода SQLBindParameter для улучшенных функций даты-времени  
 Значения параметров типов даты времени преобразуются, как описано в [преобразования из C в SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md). Обратите внимание, параметры типа **время** и **datetimeoffset** должен иметь *ValueType* указанный в виде **SQL_C_DEFAULT** или **SQL_C_BINARY** если их соответствующие структуры (**SQL_SS_TIME2_STRUCT** и **SQL_SS_TIMESTAMPOFFSET_STRUCT**) используются.  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>Поддержка метода SQLBindParameter для больших определяемых пользователем типов в среде CLR  
 **SQLBindParameter** поддерживает большие определяемые пользователем типы (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [Функция SQLBindParameter](http://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
