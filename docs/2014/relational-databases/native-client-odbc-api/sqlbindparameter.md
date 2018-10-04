---
title: SQLBindParameter | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3bea7e5bac71c3e4fdd90253f30a503dc44f44d2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209004"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
  `SQLBindParameter` может, это снижает нагрузку преобразования данных при использовании для предоставления данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента, приводит к значительный прирост производительности для компонентов клиента и сервера приложений. Другие преимущества — снижение потери точности при вставке или изменении приблизительных числовых типов данных.  
  
> [!NOTE]  
>  При вставке данных типов `char` и `wchar` в столбец изображения используется размер передаваемых данных, а не размер данных после их преобразования в двоичный формат.  
  
 Если ODBC-драйвер для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сталкивается с ошибкой при обработке одного элемента в массиве параметров, драйвер продолжит выполнение инструкции для всех остальных элементов массива.  Если приложение выполнило привязку массива элементов параметров состояния, то строки параметров, которые вызвали ошибку, можно определить по массиву.  
  
 При использовании ODBC-драйвера для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время привязки входных параметров задавайте значение SQL_PARAM_INPUT. Значения SQL_PARAM_OUTPUT и SQL_PARAM_INPUT_OUTPUT следует задавать только для привязки параметров хранимой процедуры, для которых указано ключевое слово OUTPUT.  
  
 [SQLRowCount](sqlrowcount.md) ненадежный с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента, если элемент массива массива привязанных параметров вызывает ошибку при выполнении инструкции. Атрибут инструкции ODBC SQL_ATTR_PARAMS_PROCESSED_PTR возвращает число строк, обработанных до возникновения ошибки. Затем при необходимости приложение может просмотреть массив состояний параметров, чтобы выяснить количество успешно выполненных инструкций.  
  
## <a name="binding-parameters-for-sql-character-types"></a>Привязка параметров для символьных типов SQL  
 Если тип данных SQL, переданной в символьный тип *ColumnSize* — это размер в символах (не байтов). Если длина строки данных в байтах превышает 8000, *ColumnSize* должно быть присвоено `SQL_SS_LENGTH_UNLIMITED`, указывающее, что нет ограничений на размер типа SQL.  
  
 Например если тип данных SQL является `SQL_WVARCHAR`, *ColumnSize* не должно быть больше 4000. Если фактическая длина данных превышает 4000, затем *ColumnSize* должно быть присвоено `SQL_SS_LENGTH_UNLIMITED` таким образом, чтобы `nvarchar(max)` будет использоваться драйвером.  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>Параметр SQLBindParameter и возвращающие табличные значения параметры  
 Как и других типов параметров возвращающих табличные значения параметров доступен SQLBindParameter.  
  
 После привязки возвращающего табличное значение параметра его столбцы также оказываются привязанными. Чтобы привязать столбцы, вызовите [SQLSetStmtAttr](sqlsetstmtattr.md) для присвоения параметру SQL_SOPT_SS_PARAM_FOCUS порядковый номер возвращающего табличное значение параметра. Затем вызовите метод SQLBindParameter для каждого столбца в возвращающих табличные значения параметра. Для возвращения к высокоуровневой привязке параметров задайте для SQL_SOPT_SS_PARAM_FOCUS значение 0.  
  
 Сведения о сопоставлении параметров с дескрипторами полей для возвращающих табличные значения параметров, см. в разделе [привязки и Data Transfer of Table-Valued параметры и значения столбцов](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>Поддержка метода SQLBindParameter для улучшенных функций даты-времени  
 Значения параметров, типов даты времени преобразуются в том случае, как описано в разделе [преобразования из C в SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md). Обратите внимание что параметры типа `time` и `datetimeoffset` должен иметь *ValueType* указанный в виде `SQL_C_DEFAULT` или `SQL_C_BINARY` если их соответствующие структуры (`SQL_SS_TIME2_STRUCT` и `SQL_SS_TIMESTAMPOFFSET_STRUCT`) используются.  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>Поддержка метода SQLBindParameter для больших определяемых пользователем типов в среде CLR  
 Функция `SQLBindParameter` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Сведения о реализации API ODBC](odbc-api-implementation-details.md)   
 [Функция SQLBindParameter](http://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
