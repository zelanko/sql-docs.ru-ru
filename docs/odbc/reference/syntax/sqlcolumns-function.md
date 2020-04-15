---
title: Функция S'LКолонки (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301260"
---
# <a name="sqlcolumns-function"></a>SQLColumns, функция
**Соответствия**  
 Версия Введена: Соответствие стандартам ODBC 1.0: Open Group  
  
 **Сводка**  
 В указанных **таблицах список** имен столбцов возвращается. Водитель возвращает эту информацию в результате, установленном на указанном *StatementHandle.*  
  
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
 *Обработка заявления*  
 (Вход) Ручка оператора.  
  
 *КаталогНайм*  
 (Вход) Название каталога. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других, например, когда драйвер получает данные из разных DBMS, пустая строка (") указывает на те таблицы, которые не имеют каталогов. *CatalogName* не может содержать шаблон поиска строк.  
  
> [!NOTE]  
>  Если атрибут SQL_ATTR_METADATA_ID оператора установлен на SQL_TRUE, *CatalogName* рассматривается как идентификатор, и его случай не является значительным. Если это SQL_FALSE, *CatalogName* является обычным аргументом; к нему относятся буквально, и его случай имеет важное значение. Для получения дополнительной информации смотрите [аргументы в каталоге функции](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 (Вход) Длина в символах*каталогаName*.  
  
 *Schemaname*  
 (Вход) Шаблон поиска строк для имен схем. Если драйвер поддерживает схемы для некоторых таблиц, но не для других, например, когда драйвер получает данные из различных DBMS, пустая строка (") указывает на те таблицы, которые не имеют схем.  
  
> [!NOTE]  
>  Если атрибут SQL_ATTR_METADATA_ID оператора установлен на SQL_TRUE, *SchemaName* рассматривается как идентификатор и его случай не является значительным. Если это SQL_FALSE, *SchemaName* является аргументом значения шаблона; к нему относятся буквально, и его случай имеет важное значение.  
  
 *NameLength2*  
 (Вход) Длина в символах*SchemaName*.  
  
 *Tablename*  
 (Вход) Шаблон поиска строк для имен таблиц.  
  
> [!NOTE]  
>  Если атрибут SQL_ATTR_METADATA_ID оператора установлен на SQL_TRUE, *TableName* рассматривается как идентификатор, и его случай не является значительным. Если это SQL_FALSE, *TableName* является аргументом значения шаблона; к нему относятся буквально, и его случай имеет важное значение.  
  
 *NameLength3*  
 (Вход) Длина в символах*таблицыName*.  
  
 *ColumnName*  
 (Вход) Шаблон поиска строк для имен столбцов.  
  
> [!NOTE]  
>  Если атрибут SQL_ATTR_METADATA_ID оператора установлен на SQL_TRUE, *ColumnName* рассматривается как идентификатор, и его случай не значителен. Если это SQL_FALSE, *ColumnName* является аргументом значения шаблона; к нему относятся буквально, и его случай имеет важное значение.  
  
 *NameLength4*  
 (Вход) Длина в символах*колонкиName*.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LColumns** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону s'LGetDiagRec** с *помощью handleType* of SQL_HANDLE_STMT и *ручки* *statementHandle.* В следующей таблице перечислены значения S'Lstate, обычно возвращаемые **S'LColumns,** и приведены в контексте этой функции. нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08S01|Сбой связи|Связь между драйвером и источником данных, к которому был подключен драйвер, не сработала до завершения обработки функции.|  
|24 000|Недопустимое состояние курсора|Курсор был открыт на *statementHandle*, и **S'LFetch** или **S'LFetchScroll** был вызван. Эта ошибка возвращается менеджером-драйвером, если **S'LFetch** или **S'LFetchScroll** не вернулись SQL_NO_DATA, и возвращается драйвером, если **S'LFetch** или **S'LFetchScroll** вернулся SQL_NO_DATA.<br /><br /> Курсор был открыт на *StatementHandle,* но **S'LFetch** или **S'LFetchScroll** не были вызваны.|  
|40001|Сбой сериализации|Транзакция была отката из-за взаимоблокировки ресурсов с другой транзакцией.|  
|40003|Завершение заявления неизвестно|Связанное соединение сбой во время выполнения этой функции, и состояние транзакции не может быть определено.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхлик** был вызван на *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхливнейра** был вызван на *StatementHandle* из другого потока в многопоточном приложении.|  
|HY009|Недействительное использование нулевой указатель|Атрибут SQL_ATTR_METADATA_ID оператора был установлен на SQL_TRUE, аргумент *CatalogName* был недействительным указателем, а SQL_CATALOG_NAME *InfoType* возвращает, что имена каталогов поддерживаются.<br /><br /> (DM) атрибут SQL_ATTR_METADATA_ID оператора был установлен для SQL_TRUE, а аргумент *SchemaName,* *TableName*или *ColumnName* был недействительным указателем.|  
|HY010|Ошибка последовательности функций|(DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *StatementHandle.* Эта асинхронная функция по-прежнему исполнялась, когда была вызвана функция **S'LColumns.**<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для *statementHandle* и вернулся SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.<br /><br /> (DM) Асинхронно выполнение функции (не этот) был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** был вызван для *statementHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY090|Недействительная длина строки или буфера|(DM) Значение одного из аргументов длины имени было меньше 0, но не равно SQL_NTS.|  
|||Значение одного из аргументов длины имени превысило значение максимальной длины для соответствующего каталога или имени. Максимальную длину каждого каталога или имени можно получить, позвонив по телефону **S'LGetInfo** со значениями *InfoType.* (См. "Комментарии.")|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYC00|Дополнительная функция не реализована|Было указано имя каталога, а драйвер или источник данных не поддерживает каталоги.<br /><br /> Было указано имя схемы, а драйвер или источник данных не поддерживает схемы.<br /><br /> Шаблон поиска строк был указан для имени схемы, имени таблицы или имени столбца, и источник данных не поддерживает шаблоны поиска для одного или нескольких из этих аргументов.<br /><br /> Комбинация текущих параметров атрибутов SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE оператора не была поддержана драйвером или источником данных.<br /><br /> Атрибут SQL_ATTR_USE_BOOKMARKS оператора был установлен на SQL_UB_VARIABLE, а атрибут SQL_ATTR_CURSOR_TYPE оператора был установлен на тип курсора, для которого водитель не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Период тайм-аута запроса истек до того, как источник данных вернул набор результатов. Период тайм-аута устанавливается с **помощью S'LSetStmtAttr,** SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
|IM017|Опрос отключен в асинхронном режиме уведомления|Всякий раз, когда используется модель уведомления, опрос отключается.|  
|IM018|Для завершения предыдущей асинхронной операции на этой ручке не был вызван **S'LCompleteAsync.**|Если предыдущий вызов функции на ручке возвращается SQL_STILL_EXECUTING и если режим уведомления включен, **s'LCompleteAsync** должен быть вызван на ручку, чтобы сделать пост-обработку и завершить операцию.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция обычно используется перед выполнением оператора для получения информации о столбцах для таблицы или таблиц из каталога источника данных. Для получения данных по всем типам товаров, возвращенных **S'LTables,** можно использовать **s-LКолонки.** В дополнение к базовым таблицам, это может включать (но не ограничивается) представления, синонимы, системные таблицы и так далее. В отличие от этого, функции **S'LColAttribute** и **S'LDescribeCol** описывают столбцы в наборе результатов, а функция **S'LNumResultCols** возвращает количество столбцов в набор результатов. Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
> [!NOTE]  
>  Для получения дополнительной информации об общем использовании, аргументах и возвращенных данных функций каталога ODBC [см.](../../../odbc/reference/develop-app/catalog-functions.md)  
  
 **SLColumns** возвращает результаты в стандартный набор результатов, заказанный TABLE_CAT, TABLE_SCHEM, TABLE_NAME и ORDINAL_POSITION.  
  
> [!NOTE]  
>  Когда приложение работает с ODBC 2. *x* драйвер, в наборе результатов не возвращается ORDINAL_POSITION столбец. В результате при работе с ODBC 2. *x* драйверов, порядок столбцов в списке столбцов, возвращенных **S'LColumns,** не обязательно совпадает с порядком столбцов, возвращенных при выполнении приложением оператора SELECT на всех столбцах в этой таблице.  
  
> [!NOTE]  
>  **S'LКолонки** могут не возвращать все столбцы. Например, драйвер может не возвращать информацию о псевдоколонках, таких как Oracle ROWID. Приложения могут использовать любой допустимый столбец, независимо от того, возвращается ли он **s'LColumns.**  
>   
>  Некоторые столбцы, которые могут быть возвращены **s'LStatistics,** не возвращаются **S'LColumns.** Например, **S'LColumns** не возвращает столбцы в индексе, созданном по выражению или фильтру, например, SALARY и BENEFITS или DEPT 0012.  
  
 Длина столбцов VARCHAR не отображается в таблице; фактическая длина зависит от источника данных. Для определения фактической длины столбцов TABLE_CAT, TABLE_SCHEM, TABLE_NAME и COLUMN_NAME приложение может позвонить в **s'LGetInfo** с вариантами SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN и SQL_MAX_COLUMN_NAME_LEN.  
  
 Следующие столбцы были переименованы в ODBC 3. *x*. Изменения имени столбца не влияют на обратную совместимость, поскольку приложения связываются с номером столбца.  
  
|Колонка ODBC 2.0|ODBC 3. *x* колонка|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 Следующие столбцы были добавлены к набору результатов, возвращенному **S'LColumns** для ODBC 3. *x*:  
  
|||  
|-|-|  
|CHAR_OCTET_LENGTH|ORDINAL_POSITION|  
|COLUMN_DEF|SQL_DATA_TYPE|  
|IS_NULLABLE|SQL_DATETIME_SUB|  
  
 В следующей таблице перечислены столбцы в наборе результатов. Дополнительные столбцы за столбец 18 (IS_NULLABLE) могут быть определены драйвером. Приложение должно получить доступ к столбику, в зависимости от драйвера, отсчитывая от конца набора результатов вместо указания явного ординаторского положения. Для получения дополнительной информации смотрите [данные, возвращенные функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Имя столбца|Столбец<br /><br /> number|Тип данных|Комментарии|  
|-----------------|-----------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|Название каталога; NULL, если не применим к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других, например, когда драйвер получает данные из различных DBMS, он возвращает пустую строку ("") для тех таблиц, которые не имеют каталогов.|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|Название схемы; NULL, если не применим к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других, например, когда драйвер получает данные из различных DBMS, он возвращает пустую строку ("") для тех таблиц, которые не имеют схем.|  
|TABLE_NAME (ODBC 1.0)|3|Варчар не NULL|Имя таблицы.|  
|COLUMN_NAME (ODBC 1.0)|4|Варчар не NULL|Имя столбца. Драйвер возвращает пустую строку для столбца, у которого нет имени.|  
|DATA_TYPE (ODBC 1.0)|5|Smallint, не NULL|Тип данных S'L. Это может быть тип данных ODBC S'L или тип данных, специфичный для драйверов, с помощью s-L. Для типов дат и интервальных данных этот столбец возвращает краткий тип данных (например, SQL_TYPE_DATE или SQL_INTERVAL_YEAR_TO_MONTH, вместо несугоналивого типа данных, например SQL_DATETIME или SQL_INTERVAL). В приложении D: Типы данных ODBC S'L [можно](../../../odbc/reference/appendixes/sql-data-types.md) ознакомиться с перечном списке действительных типов данных ODBC S'L. Для получения информации о типах данных, специфичных для драйверов, просмотрите документацию водителя.<br /><br /> Типы данных вернулись для ODBC 3. *x* и ODBC 2. *x* приложения могут быть разными. Для получения дополнительной [информации](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)см.|  
|TYPE_NAME (ODBC 1.0)|6|Варчар не NULL|Имя типа типа данных, зависящих от источников данных; например, "CHAR", "VARCHAR", "MONEY", "LONG VARBINAR", или "CHAR ( ) ДЛЯ BIT DATA".|  
|COLUMN_SIZE (ODBC 1.0)|7|Целое число|Если DATA_TYPE SQL_CHAR или SQL_VARCHAR, эта колонка содержит максимальную длину в символах столбца. Для типов данных о дате это общее количество символов, необходимых для отображения значения при преобразовании в символы. Для численных типов данных это либо общее число цифр, либо общее количество битов, разрешенных в столбце, согласно столбце NUM_PREC_RADIX. Для типов интервальных данных это число символов в представлении символов интервала буквального (как определено точностью интервала, [см. Длина типа данных Интервала](../../../odbc/reference/appendixes/interval-data-type-length.md) в приложении D: Типы данных). Для получения дополнительной информации в приложении D: Типы данных [см.](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)|  
|BUFFER_LENGTH (ODBC 1.0)|8|Целое число|Длина байтов данных, передаваемых в операции S'LGetData, S'LFetch или S'LFetchScroll, если указано SQL_C_DEFAULT. Для числовых данных этот размер может отличаться от размера данных, хранящихся в источнике данных. Это значение может отличаться от COLUMN_SIZE столбец для данных символов. Для получения дополнительной информации о длине см. [Размер столбца, десятичные цифры, длина переноса Octet и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении D: Типы данных.|  
|DECIMAL_DIGITS (ODBC 1.0)|9|Smallint|Общее количество значительных цифр справа от десятичной точки. Для SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP этот столбец содержит количество цифр в компоненте дробных секунд. Для других типов данных это десятичные цифры столбца на источнике данных. Для типов интервальных данных, содержащих временной компонент, этот столбец содержит количество цифр справа от десятичной точки (фракционные секунды). Для типов интервальных данных, не содержащих временной компонент, этот столбец радо 0. Для получения дополнительной информации о десятичных цифрах см. [Размер столбца, десятичные цифры, длина переноса Octet и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении D: Типы данных. NULL возвращается для типов данных, где DECIMAL_DIGITS не применимо.|  
|NUM_PREC_RADIX (ODBC 1.0)|10|Smallint|Для численных типов данных, либо 10 или 2. Если это 10, значения в COLUMN_SIZE и DECIMAL_DIGITS дают количество десятичных цифр, разрешенных для столбца. Например, столбец DECIMAL (12,5) возвращает NUM_PREC_RADIX 10, COLUMN_SIZE 12 и DECIMAL_DIGITS 5; столбец FLOAT может вернуть NUM_PREC_RADIX 10, COLUMN_SIZE 15 и DECIMAL_DIGITS NULL.<br /><br /> Если это 2, значения в COLUMN_SIZE и DECIMAL_DIGITS дают количество битов, разрешенных в столбце. Например, столбец FLOAT может вернуть RADIX 2, COLUMN_SIZE 53 и DECIMAL_DIGITS NULL.<br /><br /> NULL возвращается для типов данных, где NUM_PREC_RADIX не применимо.|  
|НЕОБЫДАНЫЙ (ODBC 1.0)|11|Smallint, не NULL|SQL_NO_NULLS, если столбец не может включать значения NULL.<br /><br /> SQL_NULLABLE, принимает ли столбец значения NULL.<br /><br /> SQL_NULLABLE_UNKNOWN если не известно, принимает ли столбец значения NULL.<br /><br /> Возвратное значение для этой колонки отличается от значения, возвращенного для IS_NULLABLE столбца. Столбец NULLABLE с уверенностью указывает, что столбец может принимать NULL, но не может с уверенностью указать, что столбец не принимает NULLs. Столбец IS_NULLABLE с уверенностью указывает, что столбец не может принимать NUL, но не может с уверенностью указать, что столбец принимает NUL.|  
|ЗАМЕЧАНИЯ (ODBC 1.0)|12|Varchar|Описание колонки.|  
|COLUMN_DEF (ODBC 3.0)|13|Varchar|Значение по умолчанию для столбца. Значение в этой колонке следует интерпретировать как строку, если она заключена в кавычки.<br /><br /> Если NULL был указан как значение по умолчанию, этот столбец является словом NULL, не заключенным в кавычки. Если значение по умолчанию не может быть представлено без усечения, этот столбец содержит TRUNCATED, без прикладных отдельных меток котировок. Если значение по умолчанию не было указано, этот столбец является NULL.<br /><br /> Значение COLUMN_DEF может быть использовано при создании нового определения столбца, за исключением случаев, когда оно содержит значение TRUNCATED.|  
|SQL_DATA_TYPE (ODBC 3.0)|14|Smallint, не NULL|Тип данных S'L, как это появляется в поле записи SQL_DESC_TYPE в IRD. Это может быть тип данных ODBC S'L или тип данных, специфичный для драйверов, с помощью s-L. Этот столбец совпадает с DATA_TYPE столбец, за исключением типов датиметра же и интервалов данных. Этот столбец возвращает несужаемый тип данных (например, SQL_DATETIME или SQL_INTERVAL), а не на краткий тип данных (например, SQL_TYPE_DATE или SQL_INTERVAL_YEAR_TO_MONTH) для типов дат и интервалов данных. Если этот столбец возвращается SQL_DATETIME или SQL_INTERVAL, определенный тип данных может быть определен из SQL_DATETIME_SUB столбца. В приложении D: Типы данных ODBC S'L [можно](../../../odbc/reference/appendixes/sql-data-types.md) ознакомиться с перечном списке действительных типов данных ODBC S'L. Для получения информации о типах данных, специфичных для драйверов, просмотрите документацию водителя.<br /><br /> Типы данных вернулись для ODBC 3. *x* и ODBC 2. *x* приложения могут быть разными. Для получения дополнительной [информации](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)см.|  
|SQL_DATETIME_SUB (ODBC 3.0)|15|Smallint|Код подтипа для типов дат и интервальных данных. Для других типов данных этот столбец возвращает значение NULL. Подробнее о времени и интервальных подкодах читайте в материале «SQL_DESC_DATETIME_INTERVAL_CODE» в [s'LSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|16|Целое число|Максимальная длина байтов символа или двоичного столбца типа данных. Для всех других типов данных этот столбец возвращает значение NULL.|  
|ORDINAL_POSITION (ODBC 3.0)|17|Integer, не NULL|Порядковый номер столбца в таблице. Первая колонка в таблице — номер 1.|  
|IS_NULLABLE (ODBC 3.0)|18|Varchar|"НЕТ", если столбец не включает NULLs.<br /><br /> "ДА", если столбец может включать NULLs.<br /><br /> Если допустимость значения NULL неизвестна, то этот столбец возвращает строку нулевой длины.<br /><br /> Допустимость значений NULL определяется в соответствии с правилами ISO. СУБД, совместимая с ISO SQL, не может вернуть пустую строку.<br /><br /> Возвратное значение для этой колонки отличается от значения, возвращенного для столбца NULLABLE. (См. описание столбца NULLABLE.)|  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере приложение объявляет буферы для набора результатов, возвращенного **S'LColumns.** Он вызывает **S'LColumns,** чтобы вернуть набор результатов, описывающий каждый столбец в таблице EMPLOYEE. Затем он вызывает **S'LBindCol,** чтобы связать столбцы в результате, установленном к буферам. Наконец, приложение получает каждый ряд данных с **помощью S'LFetch** и обрабатывает их.  
  
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
|Привязка буфера к столбцовику в наборе результатов|[SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки оператора|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возвращение привилегий для столбцов или столбцов|[Функция SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|Получение блока данных или прокрутка набора результатов|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Получение нескольких строк данных|[Функция S'LFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Возвращающиеся столбцы, которые однозначно идентифицируют строку, или столбцы, автоматически обновляемые транзакцией|[SQLSpecialColumns, функция](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|Статистика и индексы возвращающихся таблиц|[Функция SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|Возвращение списка таблиц в источнике данных|[Функция SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
|Возвращение привилегий для таблицы или таблицы|[Функция SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
