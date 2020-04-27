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
ms.openlocfilehash: cba973be9b4dc2ec0da286b2d01b636f0ca4e2b4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63067832"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
  `SQLBindParameter`может устранять нагрузку при преобразовании данных при использовании для предоставления данных драйверу ODBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента, что приводит к значительному повышению производительности для клиентских и серверных компонентов приложений. Другие преимущества — снижение потери точности при вставке или изменении приблизительных числовых типов данных.  
  
> [!NOTE]  
>  При вставке данных типов `char` и `wchar` в столбец изображения используется размер передаваемых данных, а не размер данных после их преобразования в двоичный формат.  
  
 Если ODBC-драйвер для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сталкивается с ошибкой при обработке одного элемента в массиве параметров, драйвер продолжит выполнение инструкции для всех остальных элементов массива.  Если приложение выполнило привязку массива элементов параметров состояния, то строки параметров, которые вызвали ошибку, можно определить по массиву.  
  
 При использовании ODBC-драйвера для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время привязки входных параметров задавайте значение SQL_PARAM_INPUT. Значения SQL_PARAM_OUTPUT и SQL_PARAM_INPUT_OUTPUT следует задавать только для привязки параметров хранимой процедуры, для которых указано ключевое слово OUTPUT.  
  
 [SQLRowCount](sqlrowcount.md) является ненадежным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с драйвером ODBC для собственного клиента, если элемент массива массива с привязанным параметром вызывает ошибку при выполнении инструкции. Атрибут инструкции ODBC SQL_ATTR_PARAMS_PROCESSED_PTR возвращает число строк, обработанных до возникновения ошибки. Затем при необходимости приложение может просмотреть массив состояний параметров, чтобы выяснить количество успешно выполненных инструкций.  
  
## <a name="binding-parameters-for-sql-character-types"></a>Привязка параметров для символьных типов SQL  
 Если переданный тип данных SQL имеет символьный тип, *ColumnSize* имеет размер в символах (а не байтах). Если длина строки данных в байтах больше 8000, то для *ColumnSize* должно быть установлено значение `SQL_SS_LENGTH_UNLIMITED`, указывающее на отсутствие ограничения на размер типа SQL.  
  
 Например, если тип данных SQL — `SQL_WVARCHAR`, *ColumnSize* не должен превышать 4000. Если фактическая длина данных превышает 4000, то для `SQL_SS_LENGTH_UNLIMITED` `nvarchar(max)` *ColumnSize* должно быть установлено значение, которое будет использоваться драйвером.  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>Параметр SQLBindParameter и возвращающие табличные значения параметры  
 Как и другие типы параметров, возвращающие табличные значения параметры связаны с помощью SQLBindParameter.  
  
 После привязки возвращающего табличное значение параметра его столбцы также оказываются привязанными. Чтобы привязать столбцы, вызовите [SQLSetStmtAttr](sqlsetstmtattr.md) , чтобы задать SQL_SOPT_SS_PARAM_FOCUS порядковому номеру возвращающего табличное значение параметра. Затем вызовите SQLBindParameter для каждого столбца в возвращающем табличное значение параметре. Для возвращения к высокоуровневой привязке параметров задайте для SQL_SOPT_SS_PARAM_FOCUS значение 0.  
  
 Сведения о сопоставлении параметров с полями дескрипторов для возвращающих табличное значение параметров см. в разделе [Binding and передача данных a Values-valued Parameters и Columns](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>Поддержка метода SQLBindParameter для улучшенных функций даты-времени  
 Значения параметров типов даты-времени преобразуются, как описано в статье [преобразования из C в SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md). Обратите внимание, что `time` параметры `datetimeoffset` типа и *ValueType* должны иметь значение `SQL_C_DEFAULT` ValueType `SQL_C_BINARY` , заданное как,`SQL_SS_TIME2_STRUCT` или `SQL_SS_TIMESTAMPOFFSET_STRUCT`, если используются соответствующие структуры (и).  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>Поддержка метода SQLBindParameter для больших определяемых пользователем типов в среде CLR  
 Функция `SQLBindParameter` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Сведения о реализации API ODBC](odbc-api-implementation-details.md)   
 [Функция SQLBindParameter](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
