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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36293c1f2393e9a57351fc8cd19dcc6e3338f5cc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301260"
---
# <a name="sqlcolumns-function"></a>SQLColumns, функция
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: открытая группа  
  
 **Сводка**  
 **SQLColumns** возвращает список имен столбцов в указанных таблицах. Драйвер возвращает эти сведения в виде результирующего набора для указанного *статеменсандле*.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
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
 *статеменсандле*  
 Входной Маркер инструкции.  
  
 *CatalogName*  
 Входной Имя каталога. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других, например, когда драйвер извлекает данные из разных СУБД, пустая строка ("") указывает на таблицы, не имеющие каталогов. *CatalogName* не может содержать шаблон поиска строки.  
  
> [!NOTE]  
>  Если атрибуту инструкции SQL_ATTR_METADATA_ID присвоено значение SQL_TRUE, *CatalogName* рассматривается как идентификатор и его регистр не важен. Если это SQL_FALSE, *CatalogName* является обычным аргументом. он обрабатывается буквально, и его регистр важен. Дополнительные сведения см. [в разделе аргументы в функциях каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 Входной Длина в символах **CatalogName*.  
  
 *SchemaName*  
 Входной Шаблон поиска строк для имен схем. Если драйвер поддерживает схемы для некоторых таблиц, но не для других, например, когда драйвер извлекает данные из разных СУБД, пустая строка ("") указывает на те таблицы, которые не имеют схем.  
  
> [!NOTE]  
>  Если атрибуту инструкции SQL_ATTR_METADATA_ID присвоено значение SQL_TRUE, то объект *SchemaName* рассматривается как идентификатор и его регистр не важен. Если это SQL_FALSE, то *SchemaName* является аргументом-шаблоном значения; он обрабатывается буквально, и его регистр важен.  
  
 *NameLength2*  
 Входной Длина в символах **SchemaName*.  
  
 *TableName*  
 Входной Шаблон поиска строки для имен таблиц.  
  
> [!NOTE]  
>  Если атрибут инструкции SQL_ATTR_METADATA_ID имеет значение SQL_TRUE, *TableName* рассматривается как идентификатор и его регистр не важен. Если это SQL_FALSE, *TableName* является аргументом значения шаблона; он обрабатывается буквально, и его регистр важен.  
  
 *NameLength3*  
 Входной Длина в символах **TableName*.  
  
 *ColumnName*  
 Входной Шаблон поиска строки для имен столбцов.  
  
> [!NOTE]  
>  Если атрибуту инструкции SQL_ATTR_METADATA_ID присвоено значение SQL_TRUE, то *ColumnName* обрабатывается как идентификатор и его регистр не имеет значения. Если это SQL_FALSE, *ColumnName* является аргументом значения шаблона; он обрабатывается буквально, и его регистр важен.  
  
 *NameLength4*  
 Входной Длина в символах **ColumnName*.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLColumns** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLColumns** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08S01|Сбой канала связи|Канал связи между драйвером и источником данных, к которому был подключен драйвер, был неудачен до завершения обработки функции.|  
|24 000|Недопустимое состояние курсора|В *статеменсандле*был открыт курсор, а также был вызван **SQLFetch** или **SQLFetchScroll** . Эта ошибка возвращается диспетчером драйверов, если **SQLFetch** или **SQLFetchScroll** не вернул SQL_NO_DATA, и возвращается драйвером, если **SQLFetch** или **SQLFetchScroll** вернул SQL_NO_DATA.<br /><br /> Курсор был открыт в *статеменсандле* , но **SQLFetch** или **SQLFetchScroll** не был вызван.|  
|40001|Сбой сериализации|Выполнен откат транзакции из-за взаимоблокировки ресурсов с другой транзакцией.|  
|40003|Неизвестное завершение инструкции|Не удалось выполнить связанное соединение во время выполнения этой функции, и состояние транзакции не может быть определено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка включена для *статеменсандле*. Функция была вызвана, и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** для *статеменсандле*. Затем функция была вызвана в *статеменсандле*.<br /><br /> Функция была вызвана и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** в *статеменсандле* из другого потока многопоточного приложения.|  
|HY009|Недопустимое использование пустого указателя|Атрибуту инструкции SQL_ATTR_METADATA_ID было присвоено значение SQL_TRUE, аргумент *CatalogName* был пустым указателем, а SQL_CATALOG_NAME *инфотипе* возвращает, что эти имена каталогов поддерживаются.<br /><br /> (DM) атрибуту инструкции SQL_ATTR_METADATA_ID было присвоено значение SQL_TRUE, а аргумент *SchemaName*, *TableName*или *ColumnName* был пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове функции **SQLColumns** .<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.<br /><br /> (DM) вызывается асинхронно исполняемая функция (не эта одна) для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение одного из аргументов длины имени меньше 0, но не равно SQL_NTS.|  
|||Длина значения одного из аргументов длины имени превышает максимально допустимое значение для соответствующего каталога или имени. Максимальная длина каждого каталога или имени может быть получена путем вызова **SQLGetInfo** со значениями *инфотипе* . (См. раздел "Комментарии".)|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Необязательная функция не реализована|Указано имя каталога, а драйвер или источник данных не поддерживает каталоги.<br /><br /> Указано имя схемы, а драйвер или источник данных не поддерживает схемы.<br /><br /> Для имени схемы, имени таблицы или столбца был указан шаблон поиска строки, а источник данных не поддерживает шаблоны поиска для одного или нескольких из этих аргументов.<br /><br /> Сочетание текущих параметров атрибутов SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE не поддерживалось драйвером или источником данных.<br /><br /> Атрибуту инструкции SQL_ATTR_USE_BOOKMARKS было присвоено значение SQL_UB_VARIABLE, а атрибуту инструкции SQL_ATTR_CURSOR_TYPE задан тип курсора, для которого драйвер не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Время ожидания запроса истекло до того, как источник данных вернул результирующий набор. Период ожидания задается через **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
|IM017|Опрос отключен в режиме асинхронного уведомления|При использовании модели уведомления опрос отключен.|  
|IM018|**Склкомплетеасинк** не был вызван для завершения предыдущей асинхронной операции с этим обработчиком.|Если предыдущий вызов функции в обработчике возвращает SQL_STILL_EXECUTING и если включен режим уведомления, то для обработки после обработки и завершения операции необходимо вызвать **склкомплетеасинк** .|  
  
## <a name="comments"></a>Комментарии  
 Эта функция обычно используется перед выполнением инструкции для получения сведений о столбцах таблицы или таблиц из каталога источника данных. **SQLColumns** можно использовать для получения данных обо всех типах элементов, возвращаемых **SQLTables**. В дополнение к базовым таблицам это могут быть представления (но не ограничены), синонимы, системные таблицы и т. д. В отличие от этого, функции **SQLColAttribute** и **SQLDescribeCol** описывают столбцы в результирующем наборе, а функция **SQLNumResultCols** возвращает количество столбцов в результирующем наборе. Дополнительные сведения см. в разделе [использование данных каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
> [!NOTE]  
>  Дополнительные сведения об общем использовании, аргументах и возвращаемых данных функций каталога ODBC см. в разделе [функции каталога](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLColumns** возвращает результаты в виде стандартного результирующего набора, упорядоченного по TABLE_CAT, TABLE_SCHEM, TABLE_NAME и ORDINAL_POSITION.  
  
> [!NOTE]  
>  Когда приложение работает с ODBC 2. драйвер *x* , в результирующем наборе не возвращается столбец ORDINAL_POSITION. В результате при работе с ODBC 2. драйверы *x* , порядок столбцов в списке столбцов, возвращаемых функцией **SQLColumns** , не обязательно совпадает с порядком столбцов, возвращаемых приложением при выполнении инструкции SELECT для всех столбцов в этой таблице.  
  
> [!NOTE]  
>  **SQLColumns** может не возвращать все столбцы. Например, драйвер может не возвращать сведения о псевдо-столбцах, например Oracle ROWID. Приложения могут использовать любой допустимый столбец, независимо от того, возвращается ли он методом **SQLColumns**.  
>   
>  Некоторые столбцы, которые могут возвращаться **SQLStatistics** , не возвращаются **SQLColumns**. Например, **SQLColumns** не возвращает столбцы в индексе, созданном на основе выражения или фильтра, например ОКЛАД + преимущества или отдел = 0012.  
  
 Длины столбцов VARCHAR не показаны в таблице; Фактическая длина зависит от источника данных. Чтобы определить фактическую длину столбцов TABLE_CAT, TABLE_SCHEM, TABLE_NAME и COLUMN_NAME, приложение может вызвать **SQLGetInfo** с параметрами SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN и SQL_MAX_COLUMN_NAME_LEN.  
  
 Следующие столбцы были переименованы для ODBC 3. *x*. Изменения имени столбца не влияют на обратную совместимость, так как приложения привязаны по номеру столбца.  
  
|Столбец ODBC 2,0|ODBC 3. *x* , столбец|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 В результирующий набор, возвращенный функцией **SQLColumns** для ODBC 3, были добавлены следующие столбцы. *x*:  
  
|||  
|-|-|  
|CHAR_OCTET_LENGTH|ORDINAL_POSITION|  
|COLUMN_DEF|SQL_DATA_TYPE|  
|IS_NULLABLE|SQL_DATETIME_SUB|  
  
 В следующей таблице перечислены столбцы результирующего набора. Дополнительные столбцы, которые выходят за пределы столбца 18 (IS_NULLABLE), могут быть определены драйвером. Приложение должно получить доступ к столбцам, относящимся к драйверу, выполнив подсчет с конца результирующего набора вместо того, чтобы задавать явную порядковую точку. Дополнительные сведения см. в разделе [данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Имя столбца|Столбец<br /><br /> number|Тип данных|Комментарии|  
|-----------------|-----------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1,0)|1|Varchar|Имя каталога; Значение NULL, если неприменимо к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других, например, когда драйвер извлекает данные из разных СУБД, он возвращает пустую строку ("") для таблиц, не имеющих каталогов.|  
|TABLE_SCHEM (ODBC 1,0)|2|Varchar|Имя схемы; Значение NULL, если неприменимо к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других, например, когда драйвер извлекает данные из разных СУБД, он возвращает пустую строку ("") для тех таблиц, которые не имеют схем.|  
|TABLE_NAME (ODBC 1,0)|3|Varchar, не РАВНый NULL|Имя таблицы.|  
|COLUMN_NAME (ODBC 1,0)|4|Varchar, не РАВНый NULL|Имя столбца. Драйвер возвращает пустую строку для столбца, у которого нет имени.|  
|DATA_TYPE (ODBC 1,0)|5|Smallint, не NULL|Тип данных SQL. Это может быть тип данных ODBC SQL или тип данных SQL, зависящий от драйвера. Для типов данных DateTime и Interval этот столбец возвращает тип данных краткая (например, SQL_TYPE_DATE или SQL_INTERVAL_YEAR_TO_MONTH, вместо несжатого типа данных, такого как SQL_DATETIME или SQL_INTERVAL). Список допустимых типов данных ODBC SQL см. в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) в приложении г: типы данных. Дополнительные сведения о типах данных SQL, относящихся к драйверам, см. в документации по драйверу.<br /><br /> Типы данных, возвращаемые для ODBC 3. *x* и ODBC 2. приложения *x* могут отличаться. Дополнительные сведения см. в разделе [обратная совместимость и соответствие стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|TYPE_NAME (ODBC 1,0)|6|Varchar, не РАВНый NULL|Имя типа данных, зависящее от источника данных; Например, «CHAR», «VARCHAR», «MONEY», «LONG ВАРБИНАР» или «CHAR () для данных BIT».|  
|COLUMN_SIZE (ODBC 1,0)|7|Целое число|Если DATA_TYPE имеет значение SQL_CHAR или SQL_VARCHAR, этот столбец содержит максимальную длину в символах столбца. Для типов данных DateTime это общее число символов, необходимое для вывода значения при преобразовании в символы. Для числовых типов данных это либо общее количество цифр, либо общее число битов, допустимых в столбце, в соответствии со столбцом NUM_PREC_RADIX. Для типов данных интервала это число символов в символьном представлении литерала интервала (как определено в параметре "точность в начале интервала", см. в разделе [тип данных интервала](../../../odbc/reference/appendixes/interval-data-type-length.md) в приложении г: типы данных). Дополнительные сведения см. в разделе [размер столбца, десятичные цифры, длина октета и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении г: типы данных.|  
|BUFFER_LENGTH (ODBC 1,0)|8|Целое число|Длина данных в байтах, передаваемых в операции SQLGetData, SQLFetch или SQLFetchScroll при указании SQL_C_DEFAULT. Для числовых данных этот размер может отличаться от размера данных, хранящихся в источнике данных. Это значение может отличаться от COLUMN_SIZE столбца для символьных данных. Дополнительные сведения о длине см. в разделе [размер столбца, десятичные цифры, длина октета и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении г: типы данных.|  
|DECIMAL_DIGITS (ODBC 1,0)|9|Smallint|Общее число значащих цифр справа от десятичной запятой. Для SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP этот столбец содержит количество цифр в компоненте доли секунды. Для других типов данных это десятичные разряды столбца в источнике данных. Для типов данных интервала, содержащих компонент времени, этот столбец содержит количество цифр справа от десятичной запятой (доли секунды). Для типов данных интервала, которые не содержат компонент времени, этот столбец имеет значение 0. Дополнительные сведения о десятичных цифрах см. в разделе [размер столбца, десятичные цифры, длина октета и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении D: типы данных. Для типов данных, где DECIMAL_DIGITS неприменимо, возвращается значение NULL.|  
|NUM_PREC_RADIX (ODBC 1,0)|10|Smallint|Для числовых типов данных: 10 или 2. Если значение равно 10, то значения в COLUMN_SIZE и DECIMAL_DIGITS выдают количество десятичных цифр, допустимых для столбца. Например, столбец типа DECIMAL (12, 5) возвратит NUM_PREC_RADIX 10, COLUMN_SIZE 12 и DECIMAL_DIGITS 5; столбец с плавающей запятой может возвращать NUM_PREC_RADIX 10, COLUMN_SIZE с 15 и DECIMAL_DIGITS NULL.<br /><br /> Если значение равно 2, то значения в COLUMN_SIZE и DECIMAL_DIGITS приводят к допустимому количеству битов в столбце. Например, столбец с плавающей запятой может возвращать основание системы счисления 2, COLUMN_SIZE 53 и DECIMAL_DIGITS NULL.<br /><br /> Для типов данных, где NUM_PREC_RADIX неприменимо, возвращается значение NULL.|  
|NULLABLE (ODBC 1,0)|11|Smallint, не NULL|SQL_NO_NULLS, если столбец не может содержать значения NULL.<br /><br /> SQL_NULLABLE, если столбец допускает значения NULL.<br /><br /> SQL_NULLABLE_UNKNOWN, если неизвестно, допускает ли столбец значения NULL.<br /><br /> Значение, возвращаемое для этого столбца, отличается от значения, возвращаемого для IS_NULLABLE столбца. Столбец, допускающий значение null, указывает на то, что столбец может принимать значения NULL, но не может указывать на то, что столбец не принимает значения NULL. Столбец IS_NULLABLE указывает на то, что столбец не может принимать значения NULL, но не может указывать на то, что столбец принимает значения NULL.|  
|ЗАМЕЧАНИЯ (ODBC 1,0)|12|Varchar|Описание столбца.|  
|COLUMN_DEF (ODBC 3,0)|13|Varchar|Значение по умолчанию для столбца. Значение в этом столбце должно интерпретироваться как строка, если оно заключено в кавычки.<br /><br /> Если в качестве значения по умолчанию было указано значение NULL, то этот столбец является словом NULL, а не заключен в кавычки. Если значение по умолчанию не может быть представлено без усечения, этот столбец содержит УСЕЧЕНИЕ, не заключая одинарные кавычки. Если значение по умолчанию не указано, этот столбец имеет значение NULL.<br /><br /> Значение COLUMN_DEF может использоваться при формировании нового определения столбца, за исключением случаев, когда оно содержит значение, УСЕЧЕНное.|  
|SQL_DATA_TYPE (ODBC 3,0)|14|Smallint, не NULL|Тип данных SQL, как он отображается в поле записи SQL_DESC_TYPE в IRD. Это может быть тип данных ODBC SQL или тип данных SQL, зависящий от драйвера. Этот столбец аналогичен столбцу DATA_TYPE, за исключением типов данных DateTime и Interval. В этом столбце возвращается нелаконичный тип данных (например, SQL_DATETIME или SQL_INTERVAL), а не тип данных с кратким форматом (например, SQL_TYPE_DATE или SQL_INTERVAL_YEAR_TO_MONTH) для типов данных DateTime и Interval. Если этот столбец возвращает SQL_DATETIME или SQL_INTERVAL, конкретный тип данных можно определить из столбца SQL_DATETIME_SUB. Список допустимых типов данных ODBC SQL см. в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) в приложении г: типы данных. Дополнительные сведения о типах данных SQL, относящихся к драйверам, см. в документации по драйверу.<br /><br /> Типы данных, возвращаемые для ODBC 3. *x* и ODBC 2. приложения *x* могут отличаться. Дополнительные сведения см. в разделе [обратная совместимость и соответствие стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).|  
|SQL_DATETIME_SUB (ODBC 3,0)|15|Smallint|Код подтипа для типов данных DateTime и Interval. Для других типов данных этот столбец возвращает значение NULL. Дополнительные сведения о значениях даты и времени и подкода интервала см. в разделе "SQL_DESC_DATETIME_INTERVAL_CODE" в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).|  
|CHAR_OCTET_LENGTH (ODBC 3,0)|16|Целое число|Максимальная длина в байтах для столбца символьного или двоичного типа данных. Для всех других типов данных этот столбец возвращает значение NULL.|  
|ORDINAL_POSITION (ODBC 3,0)|17|Integer, не NULL|Порядковый номер столбца в таблице. Первый столбец в таблице имеет номер 1.|  
|IS_NULLABLE (ODBC 3,0)|18|Varchar|"NO", если столбец не содержит значений NULL.<br /><br /> Значение "Да", если столбец может содержать значения NULL.<br /><br /> Если допустимость значения NULL неизвестна, то этот столбец возвращает строку нулевой длины.<br /><br /> Допустимость значений NULL определяется в соответствии с правилами ISO. СУБД, совместимая с ISO SQL, не может вернуть пустую строку.<br /><br /> Значение, возвращаемое для этого столбца, отличается от значения, возвращаемого для столбца, допускающего значение null. (См. описание столбца, допускающего значение null.)|  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере приложение объявляет буферы для результирующего набора, возвращаемого функцией **SQLColumns**. Он вызывает **SQLColumns** для возврата результирующего набора, который описывает каждый столбец в таблице Employee. Затем он вызывает **SQLBindCol** для привязки столбцов в результирующем наборе к буферам. Наконец, приложение извлекает каждую строку данных с помощью **SQLFetch** и обрабатывает ее.  
  
```cpp  
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
|Привязка буфера к столбцу в результирующем наборе|[SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возвращение привилегий для столбца или столбцов|[Функция SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Выборка блока данных или прокрутка результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Выборка нескольких строк данных|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Возврат столбцов, уникально идентифицирующих строку, или столбцов, автоматически обновляемых транзакцией|[SQLSpecialColumns, функция](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|Возврат статистики и индексов таблицы|[Функция SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Возврат списка таблиц в источнике данных|[Функция SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
|Возвращение привилегий для таблицы или таблиц|[Функция SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
