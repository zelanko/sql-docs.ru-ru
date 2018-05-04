---
title: Функция SQLForeignKeys | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLForeignKeys
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLForeignKeys
helpviewer_keywords:
- SQLForeignKeys function [ODBC]
ms.assetid: 07f3f645-f643-4d39-9a10-70a72f24e608
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02608a02190062b3530d27466d6ec319cf71b8f1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlforeignkeys-function"></a>Функция SQLForeignKeys
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ODBC  
  
 **Сводка**  
 **SQLForeignKeys** может возвращать:  
  
-   Список внешних ключей в указанной таблице (столбцы в указанной таблице, ссылающихся на первичные ключи в других таблицах).  
  
-   Список внешних ключей в других таблицах, ссылающихся на первичный ключ в указанной таблице.  
  
 Драйвер возвращает каждый список на указанную инструкцию в виде результирующего набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLForeignKeys(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      PKCatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      PKSchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      PKTableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      FKCatalogName,  
     SQLSMALLINT    NameLength4,  
     SQLCHAR *      FKSchemaName,  
     SQLSMALLINT    NameLength5,  
     SQLCHAR *      FKTableName,  
     SQLSMALLINT    NameLength6);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *PKCatalogName*  
 [Вход] Имя каталога таблицы первичного ключа. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, когда драйвер получает данные из различных DBMS, пустая строка ("») обозначает те таблицы, которые не имеют каталоги. *PKCatalogName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *PKCatalogName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *PKCatalogName* — обычный аргумент; он интерпретируется буквально и его регистр имеет значения. Дополнительные сведения см. в разделе [аргументов функций каталога](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 [Вход] Длина **PKCatalogName*, в символах.  
  
 *PKSchemaName*  
 [Вход] Имя схемы таблицы первичного ключа. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, когда драйвер получает данные из различных DBMS, пустая строка ("») обозначает этих таблиц, у которых нет схемы. *PKSchemaName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *PKSchemaName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *PKSchemaName* — обычный аргумент; он интерпретируется буквально и его регистр имеет значения.  
  
 *NameLength2*  
 [Вход] Длина **PKSchemaName*, в символах.  
  
 *PKTableName*  
 [Вход] Имя таблицы первичных ключей. *PKTableName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *PKTableName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *PKTableName* — обычный аргумент; он интерпретируется буквально и его регистр имеет значения.  
  
 *NameLength3*  
 [Вход] Длина **PKTableName*, в символах.  
  
 *FKCatalogName*  
 [Вход] Имя каталога таблицы внешнего ключа. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, когда драйвер получает данные из различных DBMS, пустая строка ("») обозначает те таблицы, которые не имеют каталоги. *FKCatalogName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *FKCatalogName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *FKCatalogName* — обычный аргумент; он интерпретируется буквально и его регистр имеет значения.  
  
 *NameLength4*  
 [Вход] Длина **FKCatalogName*, в символах.  
  
 *FKSchemaName*  
 [Вход] Имя схемы таблицы внешнего ключа. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, когда драйвер получает данные из различных DBMS, пустая строка ("») обозначает этих таблиц, у которых нет схемы. *FKSchemaName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *FKSchemaName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *FKSchemaName* — обычный аргумент; он интерпретируется буквально и его регистр имеет значения.  
  
 *NameLength5*  
 [Вход] Длина **FKSchemaName*, в символах.  
  
 *FKTableName*  
 [Вход] Имя таблицы внешних ключей. *FKTableName* не может содержать строку шаблона поиска.  
  
 Если атрибут инструкции SQL_ATTR_METADATA_ID задано значение SQL_TRUE, *FKTableName* рассматривается как идентификатор и его регистр не имеет значения. Если это значение SQL_FALSE, *FKTableName* — обычный аргумент; он интерпретируется буквально и его регистр имеет значения.  
  
 *NameLength6*  
 [Вход] Длина **FKTableName*, в символах.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLForeignKeys** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL _HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLForeignKeys** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|24000|Недопустимое состояние курсора|Курсор был открыт на *StatementHandle*, и **SQLFetch** или **SQLFetchScroll** бы была вызвана. Если эта ошибка возвращается диспетчером драйверов **SQLFetch** или **SQLFetchScroll** не вернула значение SQL_NO_DATA и возвращается с помощью драйвера, если **SQLFetch** или **SQLFetchScroll** вернула значение SQL_NO_DATA.<br /><br /> Курсор был открыт на *StatementHandle*, но **SQLFetch** или **SQLFetchScroll** не был вызван.|  
|40001|Сбой сериализации|Транзакции выполнен откат из-за взаимоблокировку ресурсов в другой транзакции.|  
|40003|Неизвестный завершение операторов|Сбой подключения во время выполнения этой функции и не удается определить состояние транзакции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, который необходим для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*, и затем вызова функции еще раз на *StatementHandle*.<br /><br /> Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY009|Недопустимое использование пустого указателя|(DM) аргументы *PKTableName* и *FKTableName* были оба указателя null.<br /><br /> Атрибут инструкции SQL_ATTR_METADATA_ID было задано значение SQL_TRUE, *FKCatalogName* или *PKCatalogName* аргумент был пустым указателем, а SQL_CATALOG_NAME *свойство*возвращает которых имена каталога поддерживаются.<br /><br /> (DM) атрибут инструкции SQL_ATTR_METADATA_ID было задано значение SQL_TRUE и *FKSchemaName*, *PKSchemaName*, *FKTableName*, или *PKTableName*  аргумент был пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. При вызове функции SQLForeignKeys по-прежнему выполнении асинхронной функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение одного из аргументов длины имени было меньше 0, но не равно SQL_NTS.|  
|||Значение одного из аргументов длина имени превышает значение максимальной длины для соответствующего имени. (В разделе «Комментарии».)|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Было указано имя каталога, а драйвер или источник данных не поддерживает каталоги.<br /><br /> Указано имя схемы, а драйвер или источник данных не поддерживает схемы.|  
|||Сочетание текущих настроек атрибуты инструкции SQL_ATTR_CONCURRENCY и SQL_ATTR_CURSOR_TYPE не поддерживается драйвером или источником данных.<br /><br /> Атрибут инструкции SQL_ATTR_USE_BOOKMARKS было задано значение SQL_UB_VARIABLE, а атрибут инструкции SQL_ATTR_CURSOR_TYPE был задан тип курсора, для которого драйвер не поддерживает закладки.|  
|HYT00|Время ожидания истекло|Время ожидания запроса истекло раньше, чем источник данных вернул результирующий набор. Время ожидания задается с помощью **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|В режиме асинхронное уведомление отключена опроса|При использовании модели уведомление опроса отключен.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущего вызова функции с дескриптором возвращает SQL_STILL_EXECUTING и уведомлений в режиме **SQLCompleteAsync** должен вызываться для этого после обработки и выполнения операции с дескриптором.|  
  
## <a name="comments"></a>Комментарии  
 Сведения об использовании сведений, возвращаемых этой функцией может быть см [использует данные из каталога](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Если \* *PKTableName* содержит имя таблицы **SQLForeignKeys** возвращает результирующий набор, содержащий первичного ключа указанной таблицы и внешние ключи, ссылающиеся на него. Список внешних ключей в других таблицах не включает внешние ключи, которые указывают на ограничения уникальности в указанной таблице.  
  
 Если \* *FKTableName* содержит имя таблицы **SQLForeignKeys** возвращает результирующий набор, содержащий все внешние ключи в указанной таблице, которые указывают на первичные ключи в других таблицах и первичные ключи в других таблицах, на которые они ссылаются. Список внешних ключей в указанной таблице не содержит внешние ключи, ссылающиеся на ограничения unique в другой таблице.  
  
 Если оба \* *PKTableName* и \* *FKTableName* имена таблиц, содержащих **SQLForeignKeys** Возвращает внешние ключи в таблице, указанной в \* *FKTableName* , ссылающиеся на первичный ключ таблицы, указанной в **PKTableName*. Это должна быть не более одного ключа.  
  
> [!NOTE]  
>  Дополнительные сведения о общего использования, аргументы и возвращаемые данные функций каталога ODBC см. в разделе [функций каталога](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLForeignKeys** возвращает результаты в виде стандартных результирующий набор. Если запрашиваются внешние ключи, связанные с первичным ключом, результирующий набор упорядочивается по FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME и KEY_SEQ. Если запрашиваются первичные ключи, связанные с внешним ключом, результирующий набор упорядочивается по PKTABLE_CAT, PKTABLE_SCHEM, PKTABLE_NAME и KEY_SEQ. В следующей таблице перечислены столбцы в результирующем наборе.  
  
 Длин столбцов VARCHAR не отображаются в таблице. фактические значения длины зависит от источника данных. Чтобы определить длин PKTABLE_CAT или FKTABLE_CAT, PKTABLE_SCHEM или FKTABLE_SCHEM, PKTABLE_NAME или FKTABLE_NAME и PKCOLUMN_NAME FKCOLUMN_NAME столбцов, приложение может вызвать **SQLGetInfo** с SQL_MAX_ Параметры CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN и SQL_MAX_COLUMN_NAME_LEN.  
  
 Следующие столбцы были переименованы для ODBC 3 *. x.* Имя столбца изменения не влияют на обратной совместимости так, как привязать приложений, номер столбца.  
  
|Столбец ODBC 2.0|ODBC 3 *.x* столбца|  
|---------------------|-----------------------|  
|PKTABLE_QUALIFIER|PKTABLE_CAT|  
|PKTABLE_OWNER|PKTABLE_SCHEM|  
|FKTABLE_QUALIFIER|FK_TABLE_CAT|  
|FKTABLE_OWNER|FKTABLE_SCHEM|  
  
 В следующей таблице перечислены столбцы в результирующем наборе. Драйвер можно определить дополнительные столбцы вслед за столбца 14 (примечания). Приложения должны доступа специфические для драйвера столбцами путем отсчет от конца результирующего набора вместо указания явного порядковый номер. Дополнительные сведения см. в разделе [данные, возвращаемые функциями каталога](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Имя столбца|Номер столбца|Тип данных|Комментарии|  
|-----------------|-------------------|---------------|--------------|  
|PKTABLE_CAT (ODBC 1.0)|1|Varchar|Имя каталога таблицы первичного ключа; Имеет значение NULL, если не применим к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, если драйвер получает данные из различных DBMS, возвращается пустая строка ("») для этих таблиц, у которых нет каталоги.|  
|PKTABLE_SCHEM (ODBC 1.0)|2|Varchar|Имя схемы таблицы первичного ключа; Имеет значение NULL, если не применим к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, если драйвер получает данные из различных DBMS, возвращается пустая строка ("») для этих таблиц, у которых нет схемы.|  
|PKTABLE_NAME (ODBC 1.0)|3|Varchar not NULL|Имя таблицы первичных ключей.|  
|PKCOLUMN_NAME (ODBC 1.0)|4|Varchar not NULL|Имя столбца первичного ключа. Драйвер возвращает пустую строку для столбца, который не имеет имени.|  
|FKTABLE_CAT (ODBC 1.0)|5|Varchar|Имя каталога таблицы внешнего ключа; Имеет значение NULL, если не применим к источнику данных. Если драйвер поддерживает каталоги для некоторых таблиц, но не для других пользователей, например, если драйвер получает данные из различных DBMS, возвращается пустая строка ("») для этих таблиц, у которых нет каталоги.|  
|FKTABLE_SCHEM (ODBC 1.0)|6|Varchar|Имя схемы таблицы внешнего ключа; Имеет значение NULL, если не применим к источнику данных. Если драйвер поддерживает схемы для некоторых таблиц, но не для других пользователей, например, если драйвер получает данные из различных DBMS, возвращается пустая строка ("») для этих таблиц, у которых нет схемы.|  
|FKTABLE_NAME (ODBC 1.0)|7|Varchar not NULL|Имя таблицы внешних ключей.|  
|FKCOLUMN_NAME (ODBC 1.0)|8|Varchar not NULL|Имя столбца внешнего ключа. Драйвер возвращает пустую строку для столбца, который не имеет имени.|  
|KEY_SEQ (ODBC 1.0)|9|Smallint, не NULL|Порядковый номер столбца (начиная с 1) ключа.|  
|ПРИЗНАК UPDATE_RULE (ODBC 1.0)|10|Smallint|Действие для применения к внешним ключом, когда операция SQL является **обновление**. Может принимать одно из следующих значений. (Ссылочная таблица является таблицей, имеет первичный ключ, ссылающаяся таблица является таблицей, содержит внешний ключ).<br /><br /> Значение SQL_CASCADE: При обновлении первичного ключа таблицы внешнего ключа из ссылающейся таблицы также обновляется.<br /><br /> Значение SQL_NO_ACTION: Если обновления первичного ключа из связанной таблицы вызовет «несвязанные ссылку» в ссылающейся таблице (то есть, строки в ссылающейся таблице будет иметь нет аналогов в указанной таблице), обновление отклоняется. Если обновление внешнего ключа из ссылающейся таблицы стало бы причиной значение, которое не существует как значение первичного ключа таблицы, на которую указывает ссылка, обновление отклоняется. (Это действие является таким же, как действие SQL_RESTRICT в ODBC 2 *.x*.)<br /><br /> SQL_SET_NULL: При обновлении одного или нескольких строк в связанной таблице таким образом, что один или несколько компонентов первичного ключа изменяются компоненты внешнего ключа в ссылающейся таблице, соответствующие измененных компонентов первичного ключа устанавливаются значение NULL в все совпадающие строки из ссылающейся таблицы.<br /><br /> SQL_SET_DEFAULT: При обновлении одного или нескольких строк в связанной таблице таким образом, что один или несколько компонентов первичного ключа изменяются на компоненты внешнего ключа в ссылающейся таблице соответствуют измененных компонентов первичного ключа: Задайте применимые значения по умолчанию в все совпадающие строки из ссылающейся таблицы.<br /><br /> Имеет значение NULL, если не применим к источнику данных.|  
|DELETE_RULE (ODBC 1.0)|11|Smallint|Действие для применения к внешним ключом, когда операция SQL является **удалить**. Может принимать одно из следующих значений. (Ссылочная таблица является таблицей, имеет первичный ключ, ссылающаяся таблица является таблицей, содержит внешний ключ).<br /><br /> Значение SQL_CASCADE: При удалении строки в указанной таблице все совпадающие строки в ссылающейся таблицы удаляются.<br /><br /> Значение SQL_NO_ACTION: Если удалить строку в указанной таблице вызовет «несвязанные ссылку» в ссылающейся таблице (то есть, строки в ссылающейся таблице будет иметь нет аналогов в указанной таблице), обновление отклоняется. (Это действие является таким же, как действие SQL_RESTRICT в ODBC 2 *.x*.)<br /><br /> SQL_SET_NULL: При удалении одной или нескольких строк в ссылочной таблице, каждый компонент ссылающейся таблицы внешнего ключа присваивается значение NULL в все совпадающие строки из ссылающейся таблицы.<br /><br /> SQL_SET_DEFAULT: При удалении одной или нескольких строк в ссылочной таблице, каждый компонент внешнего ключа из ссылающейся таблицы имеет значение применяется по умолчанию в все совпадающие строки из ссылающейся таблицы.<br /><br /> Имеет значение NULL, если не применим к источнику данных.|  
|FK_NAME (ODBC 2.0)|12|Varchar|Имя внешнего ключа. Имеет значение NULL, если не применим к источнику данных.|  
|PK_NAME (ODBC 2.0)|13|Varchar|Имя первичного ключа. Имеет значение NULL, если не применим к источнику данных.|  
|ОТСРОЧКИ (ODBC 3.0)|14|Smallint|SQL_INITIALLY_DEFERRED SQL_INITIALLY_IMMEDIATE, SQL_NOT_DEFERRABLE.|  
  
## <a name="code-example"></a>Пример кода  
 Как показано в следующей таблице, в этом примере используется три таблицы, с именем ORDERS, ЛИНИЙ и КЛИЕНТОВ.  
  
|ЗАКАЗЫ|СТРОКИ|КЛИЕНТЫ|  
|------------|-----------|---------------|  
|ORDERID|ORDERID|CUSTID|  
|CUSTID|СТРОКИ|NAME|  
|OPENDATE|PARTID|АДРЕС|  
|МЕНЕДЖЕР ПО ПРОДАЖАМ|КОЛИЧЕСТВО|ТЕЛЕФОН|  
|STATUS|||  
  
 В таблице ORDERS CUSTID определяет пользователя, которому была предпринята продажи. Он является внешним ключом, который ссылается CUSTID в таблице CUSTOMERS.  
  
 В таблице СТРОК ORDERID идентифицирует заказа на продажу, с которым связан элемент строки. Он является внешним ключом, который ссылается ORDERID в таблице ORDERS.  
  
 В этом примере вызывается **SQLPrimaryKeys** получить первичный ключ таблицы ORDERS. Результирующий набор будет иметь одну строку; в следующей таблице показаны значительные столбцов.  
  
|TABLE_NAME|COLUMN_NAME|KEY_SEQ|  
|-----------------|------------------|--------------|  
|ЗАКАЗЫ|ORDERID|1|  
  
 Затем в примере вызывается **SQLForeignKeys** для получения внешние ключи в других таблицах, ссылающихся на первичный ключ таблицы ORDERS. Результирующий набор будет иметь одну строку; в следующей таблице показаны значительные столбцов.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|ЗАКАЗЫ|CUSTID|СТРОКИ|CUSTID|1|  
  
 Наконец, в примере вызывается **SQLForeignKeys** для получения внешних ключей в таблице ORDERS, ссылающихся на первичные ключи таблиц. Результирующий набор будет иметь одну строку; в следующей таблице показаны значительные столбцов.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|КЛИЕНТЫ|CUSTID|ЗАКАЗЫ|CUSTID|1|  
  
```  
#define TAB_LEN SQL_MAX_TABLE_NAME_LEN + 1  
#define COL_LEN SQL_MAX_COLUMN_NAME_LEN + 1  
  
LPSTR   szTable;              /* Table to display */  
  
UCHAR szPkTable[TAB_LEN];   /* Primary key table name */  
UCHAR szFkTable[TAB_LEN];   /* Foreign key table name */  
UCHAR szPkCol[COL_LEN];     /* Primary key column */  
UCHAR szFkCol[COL_LEN];     /* Foreign key column */  
  
SQLHSTMT      hstmt;  
SQLINTEGER    cbPkTable, cbPkCol, cbFkTable, cbFkCol, cbKeySeq;  
SQLSMALLINT   iKeySeq;  
SQLRETURN     retcode;  
  
// Bind the columns that describe the primary and foreign keys.  
// Ignore the table schema, name, and catalog for this example.  
  
SQLBindCol(hstmt, 3, SQL_C_CHAR, szPkTable, TAB_LEN, &cbPkTable);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, szPkCol, COL_LEN, &cbPkCol);  
SQLBindCol(hstmt, 5, SQL_C_SSHORT, &iKeySeq, TAB_LEN, &cbKeySeq);  
SQLBindCol(hstmt, 7, SQL_C_CHAR, szFkTable, TAB_LEN, &cbFkTable);  
SQLBindCol(hstmt, 8, SQL_C_CHAR, szFkCol, COL_LEN, &cbFkCol);  
  
strcpy_s(szTable, sizeof(szTable), "ORDERS");  
  
/* Get the names of the columns in the primary key. */  
  
retcode = SQLPrimaryKeys(hstmt,  
         NULL, 0,             /* Catalog name */  
         NULL, 0,             /* Schema name */  
         szTable, SQL_NTS);   /* Table name */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL SUCCESS_WITH_INFO)) {  
  
   /* Fetch and display the result set. This will be a list of the */  
   /* columns in the primary key of the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "Table: %s Column: %s Key Seq: %hd \n", szPkTable, szPkCol,  
      iKeySeq);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys that refer to ORDERS primary key.*/   
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,            /* Primary catalog */  
         NULL, 0,            /* Primary schema */  
         szTable, SQL_NTS,   /* Primary table */  
         NULL, 0,            /* Foreign catalog */  
         NULL, 0,            /* Foreign schema */  
         NULL, 0);           /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* foreign keys in other tables that refer to the ORDERS */  
/* primary key. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s ) <-- %-s ( %-s )\n", szPkTable,  
               szPkCol, szFkTable, szFkCol);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys in the ORDERS table. */  
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,             /* Primary catalog */  
         NULL, 0,             /* Primary schema */  
         NULL, 0,             /* Primary table */  
         NULL, 0,             /* Foreign catalog */  
         NULL, 0,             /* Foreign schema */  
         szTable, SQL_NTS);   /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* primary keys in other tables that are referred to by foreign */  
/* keys in the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s )--> %-s ( %-s )\n", szFkTable, szFkCol, szPkTable, szPkCol);  
}  
  
/* Free the hstmt. */  
SQLFreeStmt(hstmt, SQL_DROP);  
```  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка к столбцу в результирующем наборе буфера|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выборка одной строки или блока данных в направлении только вперед|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Выборка блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Возврат столбцов первичного ключа|[Функция SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
|Получение статистики таблиц и индексов|[Функция SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
