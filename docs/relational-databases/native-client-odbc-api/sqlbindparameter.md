---
title: СЗЛБиндпарамспарастом (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74122d531eba1f714e16c168838ee1653a8f1293
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302685"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SLBindParameter** может устранить бремя преобразования данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при использовании для предоставления данных для драйвера Native Client ODBC, что приводит к значительному повышению производительности как для клиентских, так и для серверных компонентов приложений. Другие преимущества — снижение потери точности при вставке или изменении приблизительных числовых типов данных.  
  
> [!NOTE]  
>  При вставке данных **типа char** и **wchar** в столбец изображения используется размер данных, передаваемых в ней, в отличие от размера данных после преобразования в двоичный формат.  
  
 Если ODBC-драйвер для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сталкивается с ошибкой при обработке одного элемента в массиве параметров, драйвер продолжит выполнение инструкции для всех остальных элементов массива.  Если приложение выполнило привязку массива элементов параметров состояния, то строки параметров, которые вызвали ошибку, можно определить по массиву.  
  
 При использовании ODBC-драйвера для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] во время привязки входных параметров задавайте значение SQL_PARAM_INPUT. Значения SQL_PARAM_OUTPUT и SQL_PARAM_INPUT_OUTPUT следует задавать только для привязки параметров хранимой процедуры, для которых указано ключевое слово OUTPUT.  
  
 [SLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md) ненадежен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с драйвером Native Client ODBC, если элемент массива массива ограниченного параметра вызывает ошибку в выполнении оператора. Атрибут инструкции ODBC SQL_ATTR_PARAMS_PROCESSED_PTR возвращает число строк, обработанных до возникновения ошибки. Затем при необходимости приложение может просмотреть массив состояний параметров, чтобы выяснить количество успешно выполненных инструкций.  
  
## <a name="binding-parameters-for-sql-character-types"></a>Привязка параметров для символьных типов SQL  
 Если данный тип S'L, передаваемый в типе *символов,* является размером в символах (не байт). Если длина строки данных в байтах превышает 8000, *columnSize* следует установить, чтобы **SQL_SS_LENGTH_UNLIMITED,** указывая, что нет никаких ограничений на размер типа S'L.  
  
 Например, если тип данных S'L **находится SQL_WVARCHAR,** *columnSize* не должен быть больше 4000. Если фактическая длина данных превышает 4000, то *ColumnSize* следует установить в **SQL_SS_LENGTH_UNLIMITED** так, что **nvarchar (max)** будет использоваться водителем.  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>Параметр SQLBindParameter и возвращающие табличные значения параметры  
 Как и другие типы параметров, параметры, оцениваемые таблицей, связаны СЗЛБиндПарастом.  
  
 После привязки возвращающего табличное значение параметра его столбцы также оказываются привязанными. Чтобы связать столбцы, вы называете [S'LSetStmtAttr,](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) чтобы установить SQL_SOPT_SS_PARAM_FOCUS к облачному параметру, ценившему таблицу. Затем позвоните по каждому столбику в параметре, оцениваемом таблицей, вызовуйте s'LBindParameter. Для возвращения к высокоуровневой привязке параметров задайте для SQL_SOPT_SS_PARAM_FOCUS значение 0.  
  
 Для получения информации о параметрах отображения в дескрипторных полях для параметров, оцениваемых в таблице, [см.](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>Поддержка метода SQLBindParameter для улучшенных функций даты-времени  
 Значения параметров типов дат/времени преобразуются, как описано в [преобразованиях от C до S'L.](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md) Обратите внимание, что параметры **времени** типа и **времени даты** должны иметь *ValueType,* указанный как **SQL_C_DEFAULT** или **SQL_C_BINARY,** если используются соответствующие структуры **(SQL_SS_TIME2_STRUCT** и **SQL_SS_TIMESTAMPOFFSET_STRUCT).**  
  
 Для получения дополнительной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>Поддержка метода SQLBindParameter для больших определяемых пользователем типов в среде CLR  
 **S'LBindParameter** поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Подробная информация о реализации ODBC API](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [Функция SQLBindParameter](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
