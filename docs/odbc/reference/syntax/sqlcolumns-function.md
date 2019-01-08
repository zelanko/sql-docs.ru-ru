---
title: Функция SQLColumns | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumns
helpviewer_keywords:
- SQLColumns function [ODBC]
ms.assetid: 4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 51b14014853e0ccb91293097fd3aa81c1edcb2ae
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53207743"
---
# <a name="sqlcolumns-function"></a>SQLColumns, функция
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: Open Group  
  
 **Сводка**  
 **SQLColumns** возвращает список имен столбцов в указанных таблицах. Драйвер возвращает эту информацию в виде результирующего набора на указанном *StatementHandle*.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLColumns(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      ColumnName,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *CatalogName*  
 [Вход] Имя каталога. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, когда драйвер извлекает данные из разных СУБД, пустая строка ("») указывает, эти таблицы, у которых нет каталогов. *CatalogName* не может содержать шаблон поиска строки.  
  
> [!NOTE]  
>  Если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_TRUE, *CatalogName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *CatalogName* обычный аргумент; интерпретируется буквально, а также его регистр имеет значения. Дополнительные сведения см. в разделе [аргументов в функции работы с каталогами](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Вход] Длина в символах **CatalogName*.  
  
 *SchemaName*  
 [Вход] Строка шаблона поиска для имен схемы. Если драйвер поддерживает схемы, для некоторых таблиц, но не для других пользователей, например, когда драйвер извлекает данные из разных СУБД, пустая строка ("») указывает, эти таблицы, у которых нет схемы.  
  
> [!NOTE]  
>  Если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_TRUE, *SchemaName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *SchemaName* — это аргумент значения шаблона; интерпретируется буквально, а также его регистр имеет значения.  
  
 *NameLength2*  
 [Вход] Длина в символах **SchemaName*.  
  
 *TableName*  
 [Вход] Строка, шаблон поиска для имен таблиц.  
  
> [!NOTE]  
>  Если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_TRUE, *TableName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *TableName* — это аргумент значения шаблона; интерпретируется буквально, а также его регистр имеет значения.  
  
 *NameLength3*  
 [Вход] Длина в символах **TableName*.  
  
 *ColumnName*  
 [Вход] Строка шаблона поиска для имен столбцов.  
  
> [!NOTE]  
>  Если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_TRUE, *ColumnName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *ColumnName* — это аргумент значения шаблона; интерпретируется буквально, а также его регистр имеет значения.  
  
 *NameLength4*  
 [Вход] Длина в символах **ColumnName*.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLColumns** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые при помощи **SQLColumns** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|24000|Недопустимое состояние курсора|Курсор был открыт на *StatementHandle*, и **SQLFetch** или **SQLFetchScroll** бы вызывалась. Если эта ошибка возвращается диспетчером драйверов **SQLFetch** или **SQLFetchScroll** не вернула значение SQL_NO_DATA и возвращается с помощью драйвера, если **SQLFetch** или **SQLFetchScroll** вернула значение SQL_NO_DATA.<br /><br /> Курсор был открыт на *StatementHandle* , но **SQLFetch** или **SQLFetchScroll** не был вызван.|  
|40001|Сбой сериализации|Выполнен откат транзакции из-за взаимоблокировки ресурсов с другой транзакцией.|  
|40003|Состояние транзакции неизвестно|Не удалось выполнить связанное соединение во время выполнения этой функции и не удается определить состояние транзакции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимая для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция был снова вызван для *StatementHandle*.<br /><br /> Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY009|Недопустимое использование пустого указателя|Атрибут инструкции SQL_ATTR_METADATA_ID было установлено значение SQL_TRUE, *CatalogName* аргумент был пустым указателем, а также SQL_CATALOG_NAME *InfoType* возвращает этот каталога имена поддерживаются.<br /><br /> (DM) атрибут инструкции SQL_ATTR_METADATA_ID было установлено значение SQL_TRUE и *SchemaName*, *TableName*, или *ColumnName* аргумент был пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. Если по-прежнему выполнении асинхронной функции **SQLColumns** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.<br /><br /> (DM) асинхронно выполняемой функции (не такой) был вызван для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение одного из аргументов длина имени меньше 0, но не равно SQL_NTS.|  
|||Значение одного из аргументов длина имени превышает значение максимальной длины для соответствующего каталога или имени. Максимальная длина каждого каталога или имя можно получить, вызвав **SQLGetInfo** с *InfoType* значения. (См. в разделе «Комментарии».)|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Было указано имя каталога, а драйверу или источнику данных не поддерживает каталоги.<br /><br /> Было указано имя схемы, а драйверу или источнику данных не поддерживает схемы.<br /><br /> Шаблон поиска строки было указано имя схемы, имя таблицы или имя столбца, а источник данных не поддерживает шаблоны поиска для одного или нескольких из этих аргументов.<br /><br /> Сочетание текущие значения атрибутов инструкции SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE не поддерживается драйвером или источником данных.<br /><br /> Атрибут инструкции SQL_ATTR_USE_BOOKMARKS было присвоено SQL_UB_VARIABLE и атрибут инструкции SQL_ATTR_CURSOR_TYPE было присвоено тип курсора, для которого драйвер не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Время ожидания запроса истекло раньше, чем источник данных вернул результирующий набор. Период ожидания задается с помощью **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|Опрос недоступен в режиме асинхронное уведомление|Каждый раз, когда используется модель уведомлений, отключен опроса.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущий вызов функции в дескриптор возвращает SQL_STILL_EXECUTING, и если включен режим уведомлений, **SQLCompleteAsync** должен вызываться с дескриптором постобработки и завершить операцию.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция обычно используется перед выполнением инструкции для получения сведений о столбцах для таблицы или таблиц, из источника данных каталога. **SQLColumns** может использоваться для получения данных для всех типов элементов, возвращенных **SQLTables**. Помимо базовых таблицах, это может включать (но не ограничивается) представления, синонимы, системные таблицы и т. д. В отличие от этого, функции **SQLColAttribute** и **SQLDescribeCol** описывают столбцы в результирующем наборе и функцией **SQLNumResultCols** возвращает количество столбцы в результирующем наборе. Дополнительные сведения см. в разделе [использует данные из каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Дополнительные сведения о общего использования, аргументы и возвращаемые данные функций каталога ODBC, см. в разделе [функций каталога](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLColumns** возвращает результаты в виде стандартных результирующий набор, упорядоченный по TABLE_CAT, по значениям TABLE_SCHEM, TABLE_NAME и ORDINAL_POSITION.  
  
> [!NOTE]  
>  Когда приложение работает с ODBC 2. *x* драйвер, не столбец возвращается в результирующем наборе. Как следствие, при работе с ODBC 2. *x* драйверы, порядок столбцов в списке столбцов, возвращенных **SQLColumns** не обязательно так же, как порядок столбцов возвращается, если приложение выполняет инструкцию SELECT для всех столбцы в этой таблице.  
  
> [!NOTE]  
>  **SQLColumns** могут не возвращать все столбцы. Например драйвер могут не возвращать сведения о псевдо столбцов, таких как Oracle ROWID. Приложения могут использовать любой допустимый столбец ли он возвращается в виде **SQLColumns**.  
>   
>  Некоторые столбцы, которые могут быть возвращены **SQLStatistics** не возвращаются командой **SQLColumns**. Например **SQLColumns** не возвращает столбцы в индекс, созданный через выражение или фильтр, например Зарплата "+" ПРЕИМУЩЕСТВА "или" DEPT = 0012.  
  
 Длин столбцы типа VARCHAR не отображаются в таблице. фактические значения длины зависит от источника данных. Чтобы определить фактический длин столбцов TABLE_CAT, по значениям TABLE_SCHEM, TABLE_NAME и COLUMN_NAME, приложение может вызвать **SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN, и SQL_MAX_COLUMN_NAME_LEN параметры.  
  
 Следующие столбцы были переименованы для ODBC 3. *x*. Изменения имен столбцов не влияют на обратную совместимость так, как выполнить привязку приложения, номер столбца.  
  
|Столбец ODBC 2.0|ODBC 3. *x* столбца|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Были добавлены следующие столбцы результирующего набора, возвращаемого **SQLColumns** для ODBC 3. *x*:  
  
|||  
|-|-|  
|CHAR_OCTET_LENGTH|ORDINAL_POSITION|  
|COLUMN_DEF|SQL_DATA_TYPE|  
|IS_NULLABLE|SQL_DATETIME_SUB|  
  
 В следующей таблице перечислены столбцы в результирующем наборе. Дополнительные столбцы вслед за столбец 18 (IS_NULLABLE) можно определить с помощью драйвера. Приложение должно получить доступ к от драйвера, отсчет от конца результирующего набора вместо указания явной порядковый. Дополнительные сведения см. в разделе [данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Имя столбца|Столбец<br /><br /> number|Тип данных|Комментарии|  
|-----------------|-----------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Имя каталога; Значение NULL, если не применим к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, когда драйвер извлекает данные из разных СУБД, возвращается пустая строка ("») для этих таблиц, у которых нет каталогов.|  
|ПО ЗНАЧЕНИЯМ TABLE_SCHEM (ODBC 1.0)|2|Varchar|Имя схемы; Значение NULL, если не применим к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, когда драйвер извлекает данные из разных СУБД, возвращается пустая строка ("») для этих таблиц, у которых нет схемы.|  
|TABLE_NAME (ODBC 1.0)|3|Varchar not NULL|Имя таблицы.|  
|COLUMN_NAME (ODBC 1.0)|4|Varchar not NULL|Имя столбца. Драйвер возвращает пустую строку для столбца, который не имеет имени.|  
|DATA_TYPE (ODBC 1.0)|5|Smallint, не NULL|Тип данных SQL. Это может быть типом данных ODBC SQL или типом данных специфические для драйвера SQL. Для типов данных даты и времени и интервал этот столбец возвращает тип данных краткую (SQL_TYPE_DATE или SQL_INTERVAL_YEAR_TO_MONTH вместо типа nonconcise данных, например SQL_DATETIME или SQL_INTERVAL). Список допустимых типов данных ODBC SQL, см. в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) в приложение г Типы данных. Сведения о типах данных драйвера SQL см. в разделе документации по драйверу.<br /><br /> Типы данных, возвращаемых для ODBC 3. *x* и ODBC 2. *x* приложений может быть другим. Дополнительные сведения см. в разделе [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|TYPE_NAME (ODBC 1.0)|6|Varchar not NULL|Имя типа данных зависит от источника данных; Например «CHAR», «VARCHAR», «Деньги», «LONG VARBINAR» или «() CHAR FOR BIT DATA».|  
|COLUMN_SIZE (ODBC 1.0)|7|Целочисленный|Если DATA_TYPE SQL_CHAR или SQL_VARCHAR, этот столбец содержит максимальную длину в символах столбца. Для типов данных даты и времени это общее число символов, необходимых для отображения значения, при преобразовании в символы. Для числовых типов данных это общее число цифр или общее количество битов, разрешенных в столбце, в соответствии с NUM_PREC_RADIX столбца. Для интервальных типов данных, это число символов в символьном представлении литерала интервала (согласно точности интервала, см. в разделе [длина интервального типа данных](../../../odbc/reference/appendixes/interval-data-type-length.md) в приложение г Типы данных). Дополнительные сведения см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложение г Типы данных.|  
|BUFFER_LENGTH (ODBC 1.0)|8|Целочисленный|Длина в байтах данных, передаваемых при выполнении операции SQLGetData, SQLFetch или SQLFetchScroll Если SQL_C_DEFAULT указан. Для числовых данных этот размер может отличаться от размера данных, хранящихся в источнике данных. Это значение может отличаться от столбца COLUMN_SIZE для символьных данных. Дополнительные сведения о длине см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложение г Типы данных.|  
|DECIMAL_DIGITS (ODBC 1.0)|9|Smallint|Общее количество значащих цифр справа от десятичной запятой. SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP этот столбец содержит количество цифр в доли секунды. Для других типов данных это десятичные цифры из столбца в источнике данных. Для интервальных типов данных, содержащих компонент времени этот столбец содержит количество цифр справа от десятичного разделителя (в долях секунды). Для интервальных типов данных, которые не содержат компонент времени для этого столбца равно 0. Дополнительные сведения о десятичных цифр, см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложение г Типы данных. Возвращается значение NULL для типов данных, где DECIMAL_DIGITS не применяется.|  
|NUM_PREC_RADIX (ODBC 1.0)|10|Smallint|Для числовых типов данных 10 или 2. Если это 10 значений COLUMN_SIZE и DECIMAL_DIGITS предоставить количество десятичных разрядов, допустимых для столбца. Например столбец DECIMAL(12,5) возвратит NUM_PREC_RADIX 10, COLUMN_SIZE, 12 и DECIMAL_DIGITS 5; столбец с плавающей запятой может вернуть NUM_PREC_RADIX 10, COLUMN_SIZE, 15 и DECIMAL_DIGITS от NULL.<br /><br /> Если это 2 значений COLUMN_SIZE и DECIMAL_DIGITS предоставить количество битов, разрешенных в столбце. Например столбца FLOAT может вернуть основание системы СЧИСЛЕНИЯ, 2, COLUMN_SIZE 53 и DECIMAL_DIGITS от NULL.<br /><br /> Возвращается значение NULL для типов данных, где NUM_PREC_RADIX не применяется.|  
|ДОПУСКАЮЩИЙ ЗНАЧЕНИЕ NULL (ODBC 1.0)|11|Smallint, не NULL|SQL_NO_NULLS, если столбец не может содержать значения NULL.<br /><br /> SQL_NULLABLE, если столбец допускает значения NULL.<br /><br /> SQL_NULLABLE_UNKNOWN, если неизвестно, допускает ли столбец значения NULL.<br /><br /> Значение, возвращаемое для данного столбца отличается от значения, возвращаемого применительно к столбцу IS_NULLABLE. Указывает столбец допускает значения NULL, с уверенностью, что столбец может принимать значения NULL, но нельзя указать точно, что столбец не допускает значения NULL. К столбцу IS_NULLABLE указывает с уверенностью, что столбец не может принимать значения NULL, но нельзя указать точно, что столбец принимает значения NULL.|  
|"ПРИМЕЧАНИЯ" (ODBC 1.0)|12|Varchar|Описание столбца.|  
|COLUMN_DEF (ODBC 3.0)|13|Varchar|Значение по умолчанию для столбца. Значение в этом столбце должны интерпретироваться как строка, если он заключен в кавычки.<br /><br /> Значение по умолчанию задано значение NULL, этот столбец содержит слово NULL, не заключаются в кавычки. Если значение по умолчанию не может быть представлена без усечения, этот столбец содержит УСЕЧЕНА, не заключенный в одинарные кавычки. Если был указан без значения по умолчанию, этот столбец равен NULL.<br /><br /> Значение COLUMN_DEF может использоваться при формировании определения нового столбца, за исключением случаев, если он содержит значение УСЕЧЕНА.|  
|SQL_DATA_TYPE (ODBC 3.0)|14|Smallint, не NULL|Тип данных SQL, как оно отображается в поле "record" SQL_DESC_TYPE в IRD. Это может быть типом данных ODBC SQL или типом данных специфические для драйвера SQL. Этот столбец является таким же, как столбец DATA_TYPE, за исключением типов данных даты и времени и интервала. Этот столбец возвращает тип nonconcise данных (например, SQL_DATETIME или SQL_INTERVAL) вместо типа краткие данные (например, SQL_TYPE_DATE или SQL_INTERVAL_YEAR_TO_MONTH) для типа данных datetime и интервальных типов данных. Если этот столбец возвращает SQL_DATETIME или SQL_INTERVAL, можно определить в конкретном типе данных из столбца SQL_DATETIME_SUB. Список допустимых типов данных ODBC SQL, см. в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) в приложение г Типы данных. Сведения о типах данных драйвера SQL см. в разделе документации по драйверу.<br /><br /> Типы данных, возвращаемых для ODBC 3. *x* и ODBC 2. *x* приложений может быть другим. Дополнительные сведения см. в разделе [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|SQL_DATETIME_SUB (ODBC 3.0)|15|Smallint|Код подтипа для типов данных даты и времени и интервала. Для других типов данных этот столбец возвращает значение NULL. Дополнительные сведения о дополнительные коды datetime и интервал, см. в разделе «SQL_DESC_DATETIME_INTERVAL_CODE» в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|16|Целочисленный|Максимальная длина в байтах из символьных или двоичных данных типа столбца. Для всех других типов данных этот столбец возвращает значение NULL.|  
|ORDINAL_POSITION (ODBC 3.0)|17|Integer, не NULL|Порядковый номер столбца в таблице. Первый столбец в таблице имеет номер 1.|  
|IS_NULLABLE (ODBC 3.0)|18|Varchar|«Нет», если столбец не поддерживает значения NULL.<br /><br /> «Да», если столбец может содержать значения NULL.<br /><br /> Если допустимость значения NULL неизвестна, то этот столбец возвращает строку нулевой длины.<br /><br /> Допустимость значений NULL определяется в соответствии с правилами ISO. СУБД, совместимая с ISO SQL, не может вернуть пустую строку.<br /><br /> Значение, возвращаемое для данного столбца отличается от значения, возвращаемого в столбце NULLABLE. (См. описание столбца, допускающего значение NULL).|  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере приложение объявляет буферов для результирующего набора, возвращаемого **SQLColumns**. Он вызывает **SQLColumns** возвращать результирующий набор, описывающий каждый столбец в таблице EMPLOYEE. Затем он вызывает **SQLBindCol** для привязки столбцов в результирующем наборе в буферы. Наконец, приложение извлекает каждой строки данных с помощью **SQLFetch** и обрабатывает его.  
  
```  
// SQLColumns_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#define STR_LEN 128 + 1  
#define REM_LEN 254 + 1  
  
// Declare buffers for result set data  
SQLCHAR szSchema[STR_LEN];  
SQLCHAR szCatalog[STR_LEN];  
SQLCHAR szColumnName[STR_LEN];  
SQLCHAR szTableName[STR_LEN];  
SQLCHAR szTypeName[STR_LEN];  
SQLCHAR szRemarks[REM_LEN];  
SQLCHAR szColumnDefault[STR_LEN];  
SQLCHAR szIsNullable[STR_LEN];  
  
SQLINTEGER ColumnSize;  
SQLINTEGER BufferLength;  
SQLINTEGER CharOctetLength;  
SQLINTEGER OrdinalPosition;  
  
SQLSMALLINT DataType;  
SQLSMALLINT DecimalDigits;  
SQLSMALLINT NumPrecRadix;  
SQLSMALLINT Nullable;  
SQLSMALLINT SQLDataType;  
SQLSMALLINT DatetimeSubtypeCode;  
  
SQLHSTMT hstmt = NULL;  
  
// Declare buffers for bytes available to return  
SQLINTEGER cbCatalog;  
SQLINTEGER cbSchema;  
SQLINTEGER cbTableName;  
SQLINTEGER cbColumnName;  
SQLINTEGER cbDataType;  
SQLINTEGER cbTypeName;  
SQLINTEGER cbColumnSize;  
SQLLEN cbBufferLength;  
SQLINTEGER cbDecimalDigits;  
SQLINTEGER cbNumPrecRadix;  
SQLINTEGER cbNullable;  
SQLINTEGER cbRemarks;  
SQLINTEGER cbColumnDefault;  
SQLINTEGER cbSQLDataType;  
SQLINTEGER cbDatetimeSubtypeCode;  
SQLINTEGER cbCharOctetLength;  
SQLINTEGER cbOrdinalPosition;  
SQLINTEGER cbIsNullable;  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retcode = SQLColumns(hstmt, NULL, 0, NULL, 0, (SQLCHAR*)"CUSTOMERS", SQL_NTS, NULL, 0);  
  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      // Bind columns in result set to buffers  
      SQLBindCol(hstmt, 1, SQL_C_CHAR, szCatalog, STR_LEN,&cbCatalog);  
      SQLBindCol(hstmt, 2, SQL_C_CHAR, szSchema, STR_LEN, &cbSchema);  
      SQLBindCol(hstmt, 3, SQL_C_CHAR, szTableName, STR_LEN,&cbTableName);  
      SQLBindCol(hstmt, 4, SQL_C_CHAR, szColumnName, STR_LEN, &cbColumnName);  
      SQLBindCol(hstmt, 5, SQL_C_SSHORT, &DataType, 0, &cbDataType);  
      SQLBindCol(hstmt, 6, SQL_C_CHAR, szTypeName, STR_LEN, &cbTypeName);  
      SQLBindCol(hstmt, 7, SQL_C_SLONG, &ColumnSize, 0, &cbColumnSize);  
      SQLBindCol(hstmt, 8, SQL_C_SLONG, &BufferLength, 0, &cbBufferLength);  
      SQLBindCol(hstmt, 9, SQL_C_SSHORT, &DecimalDigits, 0, &cbDecimalDigits);  
      SQLBindCol(hstmt, 10, SQL_C_SSHORT, &NumPrecRadix, 0, &cbNumPrecRadix);  
      SQLBindCol(hstmt, 11, SQL_C_SSHORT, &Nullable, 0, &cbNullable);  
      SQLBindCol(hstmt, 12, SQL_C_CHAR, szRemarks, REM_LEN, &cbRemarks);  
      SQLBindCol(hstmt, 13, SQL_C_CHAR, szColumnDefault, STR_LEN, &cbColumnDefault);  
      SQLBindCol(hstmt, 14, SQL_C_SSHORT, &SQLDataType, 0, &cbSQLDataType);  
      SQLBindCol(hstmt, 15, SQL_C_SSHORT, &DatetimeSubtypeCode, 0, &cbDatetimeSubtypeCode);  
      SQLBindCol(hstmt, 16, SQL_C_SLONG, &CharOctetLength, 0, &cbCharOctetLength);  
      SQLBindCol(hstmt, 17, SQL_C_SLONG, &OrdinalPosition, 0, &cbOrdinalPosition);  
      SQLBindCol(hstmt, 18, SQL_C_CHAR, szIsNullable, STR_LEN, &cbIsNullable);  
  
      while (SQL_SUCCESS == retcode) {  
         retcode = SQLFetch(hstmt);  
         /*  
         if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // show_error();  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // Process fetched data  
         else  
            break;  
        */  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка к столбцу в результирующем наборе буфер|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработка инструкций|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возвращает привилегии для столбца или столбцов|[Функция SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Получение нескольких строк данных|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Возвращает столбцы, которые однозначно определяют строки или столбцы, автоматически обновляемые транзакцией|[Функция SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|Возврат статистики таблиц и индексов|[Функция SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Возвращает список таблиц в источнике данных|[Функция SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
|Возвращает привилегии для таблицы или таблиц|[Функция SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
