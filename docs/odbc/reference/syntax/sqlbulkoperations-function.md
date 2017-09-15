---
title: "Функция SQLBulkOperations | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLBulkOperations
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBulkOperations
helpviewer_keywords:
- SQLBulkOperations function [ODBC]
ms.assetid: 7029d0da-b0f2-44e6-9114-50bd96f47196
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ea439a41a6a3d42c9266bbccfe53aace1c0f37f4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlbulkoperations-function"></a>Функция SQLBulkOperations
**Соответствия**  
 Появился в версии: ODBC 3.0 нормативных требований: ODBC  
  
 **Сводка**  
 **SQLBulkOperations** выполняет операции массовой вставки и закладки массовой операции, включая обновления, удаления и выборку по закладке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLBulkOperations(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Operation);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *Операция*  
 [Вход] Для выполнения операции:  
  
 SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK  
  
 Дополнительные сведения см. в разделе «Комментарии».  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLBulkOperations** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из Значение SQL_HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLBulkOperations** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов . Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
 Для всех этих SQLSTATE, которые могут возвращать значение SQL_SUCCESS_WITH_INFO или SQL_ERROR (за исключением SQLSTATE 01xxx), возвращается SQL_SUCCESS_WITH_INFO, если в одной или нескольким, но не для всех строк многострочные операции происходит ошибка, и возвращается значение SQL_ERROR, если произошла ошибка Операция одной строки.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Правый усечение данных строки|*Операции* аргумент был SQL_FETCH_BY_BOOKMARK и строка или двоичные данные, возвращаемые для столбца или столбцов с типом данных SQL_C_CHAR и SQL_C_BINARY привело к усечению непустых символьных или двоичных данных от NULL.|  
|01S01|Ошибка в строке|*Операции* аргумент был SQL_ADD и при выполнении операции произошла ошибка в одну или несколько строк, но был успешно добавлен хотя бы одна строка. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).<br /><br /> (Эта ошибка возникает только в том случае, если приложение работает вместе с ODBC 2. *x* драйвера.)|  
|01S07|Частичное усечение|*Операции* аргумент был SQL_FETCH_BY_BOOKMARK, тип данных буфера приложения не была SQL_C_CHAR и SQL_C_BINARY и потери данных, возвращаемых буферы приложения для одного или нескольких столбцов. (Для числовых типов данных C, был усечен дробную часть числа. Время, отметка времени и типы данных интервала C, которые содержат компонент времени дробная часть времени были усечены.)<br /><br /> (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07006|Нарушение атрибута ограниченного типа данных|*Операции* аргумент был SQL_FETCH_BY_BOOKMARK, а значение столбца в результирующем наборе не удалось преобразовать тип данных, указанный в *TargetType* аргумента в вызове **SQLBindCol**.<br /><br /> *Операции* аргумент имеет SQL_UPDATE_BY_BOOKMARK или SQL_ADD и значение данных в буферы приложения не удалось преобразовать в тип данных столбца в результирующем наборе.|  
|07009|Недопустимый индекс дескриптора|Аргумент *операции* было SQL_ADD, и столбец был связан с числом столбцов больше, чем количество столбцов в результирующем наборе.|  
|21S02|Структура полученной таблицы не соответствуют списку столбцов|Аргумент *операции* SQL_UPDATE_BY_BOOKMARK; и столбцы не имели обновляемых, так как все столбцы были свободные или только для чтения, или значение в буфер связанного длины/индикатора был SQL_COLUMN_IGNORE.|  
|22001|Правый усечение данных строки|Назначение символьное или двоичное значение для столбца в результирующем наборе привело к усечению непустым (для символов) или ненулевой (для двоичного файла) символов или байтов.|  
|22003|Численное значение вне допустимого диапазона|*Операции* аргумент имеет SQL_ADD или SQL_UPDATE_BY_BOOKMARK, и назначение числовое значение для столбца в результирующем наборе вызвало целиком (в отличие от доли) часть усекаемое число.<br /><br /> Аргумент *операции* было SQL_FETCH_BY_BOOKMARK, и возвращает числовое значение для одного или нескольких связанных столбцов могло привести к потере значащих цифр.|  
|22007|Формат недопустимые даты и времени|*Операции* аргумент имеет SQL_ADD или SQL_UPDATE_BY_BOOKMARK и присвоение значения date и timestamp со столбцом в результирующем наборе за год, месяц или день поле должно быть вне допустимого диапазона.<br /><br /> Аргумент *операции* был SQL_FETCH_BY_BOOKMARK и возврат значения даты или отметки времени для одного или нескольких связанных столбцов могло привести год, месяц или день поле должно быть вне допустимого диапазона.|  
|22008|Переполнение поля даты и времени|*Операции* аргумент имеет SQL_ADD или SQL_UPDATE_BY_BOOKMARK и производительность арифметика на данные, отправляемые в столбец в результирующем наборе datetime привело к поля даты и времени (год, месяц, день, час, минуту или секунду поле) в результате падают пределы допустимого диапазона значений для поля или являющихся допустимыми на основе правил естественным григорианского календаря для даты.<br /><br /> *Операции* аргумент был SQL_FETCH_BY_BOOKMARK и производительность арифметика на полученных из результирующего набора данных datetime привело к datetime поле (год, месяц, день, час, минуту или второе поле) результат падают пределы допустимого диапазона значений для поля или недопустимом основан на естественным правила даты григорианского календаря.|  
|22015|Переполнение поля интервала|*Операции* аргумент имеет SQL_ADD или SQL_UPDATE_BY_BOOKMARK и назначение точным или тип интервала C в пределах типа данных SQL привело к потере значащих цифр.<br /><br /> *Операции* аргумент имеет SQL_ADD или SQL_UPDATE_BY_BOOKMARK; при назначении в пределах типа SQL была не представление значения типа C, в течение интервала, тип SQL.<br /><br /> *Операции* аргумент был SQL_FETCH_BY_BOOKMARK и присвоение тип интервала C из точное числовое значение или интервал тип SQL привело к потере значащих разрядов в начале поля.<br /><br /> *Операции* аргумент был SQL_FETCH_BY_BOOKMARK; присвоить тип интервала C, возникла не представление значения в тип интервала C типа SQL.|  
|22018|Недопустимое символьное значение для спецификации приведения|*Операции* аргумент был SQL_FETCH_BY_BOOKMARK; тип C был точное или Приблизительное числовое, datetime или тип интервала данных; тип SQL столбца был в символьный тип данных; и значение в столбце не является допустимым литерал связанного типа C.<br /><br /> Аргумент *операции* SQL_ADD или SQL_UPDATE_BY_BOOKMARK; тип SQL был точное или Приблизительное числовое, datetime или тип интервала данных; тип C была SQL_C_CHAR; и значение в столбце не является допустимым литералом из связанный тип SQL.|  
|23000|Нарушение ограничения целостности|*Операции* аргумент был SQL_ADD, SQL_DELETE_BY_BOOKMARK или SQL_UPDATE_BY_BOOKMARK и было нарушено ограничение целостности.<br /><br /> *Операции* аргумент был SQL_ADD и столбец, который не был привязан определен как NOT NULL, а нет значения по умолчанию.<br /><br /> *Операции* аргумент был SQL_ADD, длина, указанная в значение границы *StrLen_or_IndPtr* буфер был SQL_COLUMN_IGNORE и столбце отсутствует значение по умолчанию.|  
|24000|Недопустимое состояние курсора|*StatementHandle* находился в состоянии выполнения, но результирующий набор не связан с *StatementHandle*.|  
|40001|Сбой сериализации|Транзакции выполнен откат из-за взаимоблокировку ресурсов в другой транзакции.|  
|40003|Неизвестный завершение операторов|Сбой подключения во время выполнения этой функции и не удается определить состояние транзакции.|  
|42000|Синтаксическая ошибка или нарушение доступа|Драйвер не удалось заблокировать строки, необходимыми для выполнения операции, запрашиваемый в *операции* аргумент.|  
|44000|Нарушение параметра WITH CHECK OPTION|*Операции* аргумент был SQL_ADD или SQL_UPDATE_BY_BOOKMARK и вставка или обновление было выполнено для просмотра таблицы (или таблицы, полученное из просматриваемого таблицы), созданного путем указания **WITH CHECK OPTION**, таким образом, что одну или несколько строк, затронутых вставки или обновления больше не присутствовать в таблице просматриваемого.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в * \*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом асинхронной функция **SQLBulkOperations** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.<br /><br /> (DM) указанного *StatementHandle* не находился в состоянии выполнения. Функция была вызвана без предварительного вызова функции **SQLExecDirect**, **SQLExecute**, или функции каталога.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLSetPos** был вызван для *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.<br /><br /> (DM) был драйвер ODBC 2. *x* драйвер, и **SQLBulkOperations** был вызван для *StatementHandle* перед **SQLFetchScroll** или **SQLFetch ** был вызван.<br /><br /> (DM) **SQLBulkOperations** был вызван после **SQLExtendedFetch** был вызван для *StatementHandle*.|  
|HY011|Невозможно задать атрибут сейчас|(DM) был драйвер ODBC 2. *x* драйвер и атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR было установлено между вызовами **SQLFetch** или **SQLFetchScroll** и **SQLBulkOperations **.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|*Операции* аргумент имеет SQL_ADD или SQL_UPDATE_BY_BOOKMARK; значение данных не является пустым указателем; был тип данных C SQL_C_BINARY и SQL_C_CHAR; и значение длины столбца был меньше 0, но не равны в значение SQL_DATA_AT_EXEC , SQL_COLUMN_IGNORE, SQL_NTS или SQL_NULL_DATA, или меньше или равно SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Значение в буфер длины/индикатора было значение SQL_DATA_AT_EXEC; тип SQL была SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных long, определяемые источником данных; и введите сведения о SQL_NEED_LONG_DATA_LEN **SQLGetInfo** была «Y».<br /><br /> *Операции* аргумент был SQL_ADD и атрибут инструкции SQL_ATTR_USE_BOOKMARK было задано значение SQL_UB_VARIABLE 0 был привязан к буфера, длина которого не равно Максимальная длина закладки для этого результирующего набора. (Эта длина доступен в поле SQL_DESC_OCTET_LENGTH IRD и может быть получен путем вызова **SQLDescribeCol**, **SQLColAttribute**, или **SQLGetDescField**.)|  
|HY092|Недопустимый атрибут идентификатора|(DM) значение, указанное для *операции* недопустимый аргумент.<br /><br /> *Операции* аргумент был SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK и атрибута инструкции SQL_ATTR_CONCURRENCY было задано значение SQL_CONCUR_READ_ONLY.<br /><br /> *Операции* аргумент был SQL_DELETE_BY_BOOKMARK, SQL_FETCH_BY_BOOKMARK или SQL_UPDATE_BY_BOOKMARK и столбец закладки не привязан или атрибут инструкции SQL_ATTR_USE_BOOKMARKS было задано значение SQL_UB_OFF.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Драйвер или источник данных не поддерживает операцию, запрашиваемый в *операции* аргумент.|  
|HYT00|Время ожидания истекло|Время ожидания запроса истекло раньше, чем источник данных вернул результирующий набор. Время ожидания задается с помощью **SQLSetStmtAttr** с *атрибута* аргумент SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|В режиме асинхронное уведомление отключена опроса|При использовании модели уведомление опроса отключен.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущего вызова функции с дескриптором возвращает SQL_STILL_EXECUTING и уведомлений в режиме **SQLCompleteAsync** должен вызываться для этого после обработки и выполнения операции с дескриптором.|  
  
## <a name="comments"></a>Комментарии  
  
> [!CAUTION]  
>  Сведения о том, какие инструкции **SQLBulkOperations** может быть вызвана и что необходимо сделать для обеспечения совместимости с ODBC 2.* x* приложения, см. [блочных курсоров, Прокручиваемые курсоры и обратной совместимости](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) раздела приложение G: драйвер рекомендации для обеспечения обратной совместимости.  
  
 Приложение использует **SQLBulkOperations** для выполнения следующих операций над базовой таблицы или представления, соответствующий текущему запросу:  
  
-   Добавление новых строк.  
  
-   Обновление набора строк, где каждая строка определяется закладки.  
  
-   Удаление набора строк, где каждая строка определяется закладки.  
  
-   Получить набор строк, где каждая строка определяется закладки.  
  
 После вызова **SQLBulkOperations**, позиция курсора блок не определено. Приложение должно вызвать **SQLFetchScroll** Чтобы установить позицию курсора. Приложение должно вызывать **SQLFetchScroll** только с *FetchOrientation* SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE или SQL_FETCH_BOOKMARK аргумента. Положение курсора не определено, если приложение вызывает **SQLFetch** или **SQLFetchScroll** с *FetchOrientation* аргумент SQL_FETCH_PRIOR, SQL_FETCH_NEXT, или SQL_FETCH_RELATIVE.  
  
 Столбец может быть проигнорирована в массовой операции, выполняемые с помощью вызова **SQLBulkOperations** , задав буфер длины/индикатора столбец, указанный в вызове **SQLBindCol**, чтобы SQL_COLUMN_IGNORE.  
  
 Это необходимо для приложения задать атрибут инструкции SQL_ATTR_ROW_OPERATION_PTR при вызове **SQLBulkOperations** , так как строки не учитываются при выполнении массовых операций с помощью этой функции.  
  
 Буфер, на который указывает атрибут инструкции SQL_ATTR_ROWS_FETCHED_PTR содержит количество строк, затронутых при вызове **SQLBulkOperations**.  
  
 Когда *операции* аргумент SQL_ADD или SQL_UPDATE_BY_BOOKMARK и список выбора спецификация запроса, связанный с курсором содержит более одной ссылки в том же столбце, он является определяемым драйвером ли ошибка создается или драйвер не учитывает повторяющиеся ссылки и выполняет запрошенных операций.  
  
 Дополнительные сведения об использовании **SQLBulkOperations**, в разделе [обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).  
  
## <a name="performing-bulk-inserts"></a>Выполнения массовых вставок  
 Вставка данных с **SQLBulkOperations**, приложение выполняет следующие действия:  
  
1.  Выполняет запрос, который возвращает результирующий набор.  
  
2.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции на число строк, которые необходимо вставить.  
  
3.  Вызовы **SQLBindCol** для привязки данных, который требуется вставить. Данные, привязанные к массив с размером, равным значение SQL_ATTR_ROW_ARRAY_SIZE.  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут инструкции sql_attr_row_status_ptr, которое указывает должно быть равным SQL_ATTR_ROW_ARRAY_SIZE или значения SQL_ATTR_ROW_STATUS_PTR должен быть указателем null.  
  
4.  Вызовы **SQLBulkOperations**(*StatementHandle,* SQL_ADD) для выполнения вставки.  
  
5.  Если приложение значение атрибута инструкции sql_attr_row_status_ptr, которое указывает, можно изучить этого массива, чтобы увидеть результат операции.  
  
 Если приложение связывает столбец 0, перед вызовом **SQLBulkOperations** с *операции* аргумент SQL_ADD, драйвер будет обновлять буферах связанных столбцов 0 со значениями закладки для вновь вставляемой строки. Для этого приложения необходимо установить атрибут инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE до выполнения инструкции. (Это не работает с ODBC 2. *x* драйвера.)  
  
 Большие объемы данных могут быть добавлены в части SQLBulkOperations, с помощью вызова методов SQLParamData и SQLPutData. Дополнительные сведения см. в разделе «Предоставление Long данных для Bulk INSERT и Update» далее в этом справочнике по функциям.  
  
 Это необходимо для приложения для вызова **SQLFetch** или **SQLFetchScroll** перед вызовом **SQLBulkOperations** (кроме случаев, когда начинается с ODBC 2.* x* драйвера см. в разделе [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)).  
  
 Поведение является определяемым драйвером Если **SQLBulkOperations**, с *операции* аргумент SQL_ADD, будет вызван на курсор, который содержит повторяющиеся столбцы. Драйвер может возвращать SQLSTATE, определяемым драйвером, добавляют данные в первый столбец, который отображается в результатах, и выполнять другие правила поведения, определяемым драйвером.  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>Выполнение массового обновления, с помощью закладок  
 Для выполнения массовых обновлений с помощью закладок с **SQLBulkOperations**, приложение выполняет следующие шаги в последовательности:  
  
1.  Устанавливает атрибут инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, который возвращает результирующий набор.  
  
3.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции на число строк, которые требуется обновить.  
  
4.  Вызовы **SQLBindCol** для привязки данных, необходимо обновить. Данные, привязанные к массив с размером, равным значение SQL_ATTR_ROW_ARRAY_SIZE. Он также вызывает метод **SQLBindCol** привязать столбец 0 (закладку для столбца).  
  
5.  Копирует закладок для строк, что интересующие его обновление в массив, привязанное к столбцу 0.  
  
6.  Обновляет данные в буферах привязанного.  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут инструкции sql_attr_row_status_ptr, которое указывает должно быть равно SQL_ATTR_ROW_ARRAY_SIZE или значения SQL_ATTR_ROW_STATUS_PTR должен быть указателем null.  
  
7.  Вызовы **SQLBulkOperations**(*StatementHandle,* SQL_UPDATE_BY_BOOKMARK).  
  
    > [!NOTE]  
    >  Если приложение значение атрибута инструкции sql_attr_row_status_ptr, которое указывает, можно изучить этого массива, чтобы увидеть результат операции.  
  
8.  При необходимости вызывает **SQLBulkOperations**(*StatementHandle*, SQL_FETCH_BY_BOOKMARK) для выборки данных в буферы связанного приложения, чтобы убедиться, что произошло обновление.  
  
9. Если данные обновлены, драйвер изменяет значение в массиве строк состояния для соответствующих строк на SQL_ROW_UPDATED.  
  
 Массового обновления, выполненные **SQLBulkOperations** может включать большие объемы данных с помощью вызова **SQLParamData** и **SQLPutData**. Дополнительные сведения см. в разделе «Предоставление Long данных для Bulk INSERT и Update» далее в этом справочнике по функциям.  
  
 Если закладки сохраняются на курсоры, приложение не нужно вызывать **SQLFetch** или **SQLFetchScroll** перед обновлением с закладки. Его можно использовать закладки, которые он сохранен из предыдущей курсора. Если закладки не сохраняются на курсоры, приложение должно вызвать **SQLFetch** или **SQLFetchScroll** для получения закладки.  
  
 Поведение является определяемым драйвером Если **SQLBulkOperations**, с *операции* аргумент SQL_UPDATE_BY_BOOKMARK, будет вызван на курсор, который содержит повторяющиеся столбцы. Драйвер можно вернуть SQLSTATE, определяемым драйвером, обновить первый столбец, который отображается в результирующем наборе или выполнять другие правила поведения, определяемым драйвером.  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>Выполнение массового выбирается с помощью закладок  
 Для выполнения массового выборки с помощью закладок с **SQLBulkOperations**, приложение выполняет следующие шаги в последовательности:  
  
1.  Устанавливает атрибут инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, который возвращает результирующий набор.  
  
3.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции на число строк, которые необходимо извлечь.  
  
4.  Вызовы **SQLBindCol** для привязки данных, ему нужно извлечь. Данные, привязанные к массив с размером, равным значение SQL_ATTR_ROW_ARRAY_SIZE. Он также вызывает метод **SQLBindCol** привязать столбец 0 (закладку для столбца).  
  
5.  Копирует закладки для заинтересована в выборке в массив строк, привязанное к столбцу 0. (Предполагается, что приложение уже получил закладки отдельно.)  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут инструкции sql_attr_row_status_ptr, которое указывает должно быть равно SQL_ATTR_ROW_ARRAY_SIZE или значения SQL_ATTR_ROW_STATUS_PTR должен быть указателем null.  
  
6.  Вызовы **SQLBulkOperations**(*StatementHandle,* SQL_FETCH_BY_BOOKMARK).  
  
7.  Если приложение значение атрибута инструкции sql_attr_row_status_ptr, которое указывает, можно изучить этого массива, чтобы увидеть результат операции.  
  
 Если закладки сохраняются на курсоры, приложение не нужно вызывать **SQLFetch** или **SQLFetchScroll** перед выборкой с закладки. Его можно использовать закладки, которые он сохранен из предыдущей курсора. Если закладки не сохраняются на курсоры, приложение должно вызвать **SQLFetch** или **SQLFetchScroll** один раз для получения закладки.  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>Выполнение массового удаления с помощью закладок  
 Для выполнения массового удаления с помощью закладок с **SQLBulkOperations**, приложение выполняет следующие шаги в последовательности:  
  
1.  Устанавливает атрибут инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, который возвращает результирующий набор.  
  
3.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции на число строк, которые требуется удалить.  
  
4.  Вызовы **SQLBindCol** привязать столбец 0 (закладку для столбца).  
  
5.  Копирует закладок для строк, что интересующие его удалении в массиве, привязанное к столбцу 0.  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут инструкции sql_attr_row_status_ptr, которое указывает должно быть равно SQL_ATTR_ROW_ARRAY_SIZE или значения SQL_ATTR_ROW_STATUS_PTR должен быть указателем null.  
  
6.  Вызовы **SQLBulkOperations**(*StatementHandle,* SQL_DELETE_BY_BOOKMARK).  
  
7.  Если приложение значение атрибута инструкции sql_attr_row_status_ptr, которое указывает, можно изучить этого массива, чтобы увидеть результат операции.  
  
 Если закладки сохраняются на курсоры, приложение не имеет для вызова **SQLFetch** или **SQLFetchScroll** перед удалением с закладки. Его можно использовать закладки, которые он сохранен из предыдущей курсора. Если закладки не сохраняются на курсоры, приложение должно вызвать **SQLFetch** или **SQLFetchScroll** один раз для получения закладки.  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>Предоставление данных большой длины для операции массовой вставки и обновления  
 Длинные данные могут быть предоставлены для массовой вставки и обновлений, выполняемых вызовов **SQLBulkOperations**. Вставлять или обновлять данные большой длины, приложение выполняет следующие действия в дополнение к действия, описанные в разделах «Выполнения осуществляет массовую вставку» и «Выполнение массового обновления с помощью закладок» ранее в этом разделе.  
  
1.  Когда связывает данные с помощью **SQLBindCol**, приложение размещает определяемые приложением значения, такие как номер столбца в * \*TargetValuePtr* буфера для данных времени выполнения столбцы. Значение может использоваться для идентификации столбца.  
  
     Приложение размещает результат SQL_LEN_DATA_AT_EXEC (*длина*) макрос в * \*StrLen_or_IndPtr* буфера. Если тип данных SQL столбца SQL_LONGVARBINARY, SQL_LONGVARCHAR или тип данных long, определяемые источником данных и драйвер возвращает «Y» для типа данных SQL_NEED_LONG_DATA_LEN в **SQLGetInfo**, *длина * число байтов данных, отправляемых для параметра; в противном случае он должен иметь неотрицательное значение и учитывается.  
  
2.  Когда **SQLBulkOperations** вызывается, если нет столбцов данных времени выполнения, функция возвращает SQL_NEED_DATA и переходит к шагу 3, которая следует за. (Если нет столбцов данных времени выполнения, процесс будет завершен.)  
  
3.  Приложение вызывает **SQLParamData** для получения адреса * \*TargetValuePtr* буфера для первого столбца данных во время выполнения для обработки. **SQLParamData** возвращает SQL_NEED_DATA. Приложение извлекает определяемые приложением значения из * \*TargetValuePtr* буфера.  
  
    > [!NOTE]  
    >  Несмотря на то, что параметры с данными времени выполнения напоминают столбцов данных времени выполнения, значение, возвращаемое **SQLParamData** отличается для каждого.  
  
     Столбцы данных времени выполнения являются столбцами в наборе строк, для которого данные будут отправлены с **SQLPutData** при обновлении или вставке с строки **SQLBulkOperations**. Они связаны с **SQLBindCol**. Значение, возвращаемое **SQLParamData** адрес строки в **TargetValuePtr* буфера, который обрабатывается.  
  
4.  Приложение вызывает **SQLPutData** один или несколько раз для отправки данных для столбца. Более одного вызова необходим в том случае, если все значения данных нельзя вернуть в * \*TargetValuePtr* буфера, указанный в **SQLPutData**; несколько вызовов **SQLPutData** для того же столбца разрешены только в том случае, при отправке данных символ C для столбца с типом данных, определяемые источником символьных, двоичных и данных или при отправке двоичных данных C для столбца с символом, двоичных данных, либо тип данных, определяемые источником данных.  
  
5.  Приложение вызывает **SQLParamData** еще раз, чтобы сообщить, что все данные были переданы для столбца.  
  
    -   Если есть дополнительные столбцы данных времени выполнения, **SQLParamData** возвращает SQL_NEED_DATA и адрес *TargetValuePtr* буфер для следующего столбца данных во время выполнения для обработки. Приложение повторяет шаги 4 и 5.  
  
    -   Если больше нет столбцов данных времени выполнения, процесс будет завершен. Если инструкция была выполнена успешно, **SQLParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO; Если выполнение завершилось неудачей, он возвращает значение SQL_ERROR. На этом этапе **SQLParamData** может возвращать любой SQLSTATE, которые могут быть возвращены с **SQLBulkOperations**.  
  
 Если операция отменена, или произошла ошибка в **SQLParamData** или **SQLPutData** после **SQLBulkOperations** возвращает SQL_NEED_DATA и перед отправкой данных для всех столбцы данных времени выполнения, приложение может вызвать только **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions **, **SQLParamData**, или **SQLPutData** для инструкции или соединения, связанные с инструкцией. Если он вызывает любой другой функции для инструкции или соединения, связанные с инструкцией, функция возвращает значение SQL_ERROR и SQLSTATE HY010 (функция ошибка последовательности).  
  
 Если приложение вызывает **SQLCancel** пока драйвер по-прежнему требуются данные для столбцов данных времени выполнения, драйвер отменяет операцию. Затем приложение может вызвать **SQLBulkOperations** попытку; Отмена не влияет на состояние курсора или текущей позиции курсора.  
  
## <a name="row-status-array"></a>Массив состояния строк  
 Массив состояния строк содержит значения состояния для каждой строки данных в наборе строк после вызова **SQLBulkOperations**. Драйвер устанавливает значения состояний в этом массиве после вызова **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**, или **SQLBulkOperations** . Изначально этот массив заполняется с помощью вызова **SQLBulkOperations** Если **SQLFetch** или **SQLFetchScroll** не был вызван перед **SQLBulkOperations **. Этот массив указывает атрибут значения SQL_ATTR_ROW_STATUS_PTR инструкции. Количество элементов в массивах состояния строк должно быть равно числу строк в наборе строк (как определено в атрибуте SQL_ATTR_ROW_ARRAY_SIZE инструкции). Сведения об этом массив состояния строк см. в разделе [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Пример кода  
 Следующий пример извлекает 10 строк данных по одному из таблицы Customers. Он затем предлагает пользователю для действия занять. Чтобы уменьшить сетевой трафик, буфер пример обновления, удаления и вставляет локально в привязанные массивы, но с смещениями строк данных в прошлом. Когда пользователь выбирает для отправки обновления, удаления и вставки в источнике данных, код задает привязку, смещение соответствующим образом и вызывает **SQLBulkOperations**. Для простоты пользователь не может буфера более 10 обновления, удаления и вставки.  
  
```  
// SQLBulkOperations_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include "stdio.h"  
  
#define UPDATE_ROW 100  
#define DELETE_ROW 101  
#define ADD_ROW 102  
#define SEND_TO_DATA_SOURCE 103  
#define UPDATE_OFFSET 10  
#define INSERT_OFFSET 20  
#define DELETE_OFFSET 30  
  
// Define structure for customer data (assume 10 byte maximum bookmark size).  
typedef struct tagCustStruct {  
   SQLCHAR Bookmark[10];  
   SQLINTEGER BookmarkLen;  
   SQLUINTEGER CustomerID;  
   SQLINTEGER CustIDInd;  
   SQLCHAR CompanyName[51];  
   SQLINTEGER NameLenOrInd;  
   SQLCHAR Address[51];  
   SQLINTEGER AddressLenOrInd;  
   SQLCHAR Phone[11];  
   SQLINTEGER PhoneLenOrInd;  
} CustStruct;  
  
// Allocate 40 of these structures. Elements 0-9 are for the current rowset,  
// elements 10-19 are for the buffered updates, elements 20-29 are for  
// the buffered inserts, and elements 30-39 are for the buffered deletes.  
CustStruct CustArray[40];  
SQLUSMALLINT RowStatusArray[10], Action, RowNum, NumUpdates = 0, NumInserts = 0,  
NumDeletes = 0;  
SQLLEN BindOffset = 0;  
SQLRETURN retcode;  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLHSTMT hstmt = NULL;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // Set the following statement attributes:  
   // SQL_ATTR_CURSOR_TYPE:           Keyset-driven  
   // SQL_ATTR_ROW_BIND_TYPE:         Row-wise  
   // SQL_ATTR_ROW_ARRAY_SIZE:        10  
   // SQL_ATTR_USE_BOOKMARKS:         Use variable-length bookmarks  
   // SQL_ATTR_ROW_STATUS_PTR:        Points to RowStatusArray  
   // SQL_ATTR_ROW_BIND_OFFSET_PTR:   Points to BindOffset  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_KEYSET_DRIVEN, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER)sizeof(CustStruct), 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_USE_BOOKMARKS, (SQLPOINTER)SQL_UB_VARIABLE, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_OFFSET_PTR, &BindOffset, 0);  
  
   // Bind arrays to the bookmark, CustomerID, CompanyName, Address, and Phone columns.  
   retcode = SQLBindCol(hstmt, 0, SQL_C_VARBOOKMARK, CustArray[0].Bookmark, sizeof(CustArray[0].Bookmark), &CustArray[0].BookmarkLen);  
   retcode = SQLBindCol(hstmt, 1, SQL_C_ULONG, &CustArray[0].CustomerID, 0, &CustArray[0].CustIDInd);  
   retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, CustArray[0].CompanyName, sizeof(CustArray[0].CompanyName), &CustArray[0].NameLenOrInd);  
   retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, CustArray[0].Address, sizeof(CustArray[0].Address), &CustArray[0].AddressLenOrInd);  
   retcode = SQLBindCol(hstmt, 4, SQL_C_CHAR, CustArray[0].Phone, sizeof(CustArray[0].Phone), &CustArray[0].PhoneLenOrInd);  
  
   // Execute a statement to retrieve rows from the Customers table.  
   retcode = SQLExecDirect(hstmt, (SQLCHAR*)"SELECT CustomerID, CompanyName, Address, Phone FROM Customers", SQL_NTS);  
  
   // Fetch and display the first 10 rows.  
   retcode = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
   // DisplayCustData(CustArray, 10);  
  
   // Call GetAction to get an action and a row number from the user.  
   // while (GetAction(&Action, &RowNum)) {  
   Action = SQL_FETCH_NEXT;  
   RowNum = 2;  
   switch (Action) {  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmt, Action, RowNum);  
         // DisplayCustData(CustArray, 10);  
         break;  
  
      case UPDATE_ROW:  
         // Check if we have reached the maximum number of buffered updates.  
         if (NumUpdates < 10) {  
            // Get the new customer data and place it in the next available element of  
            // the buffered updates section of CustArray, copy the bookmark of the row  
            // being updated to the same element, and increment the update counter.  
            // Checking to see we have not already buffered an update for this  
            // row not shown.  
            // GetNewCustData(CustArray, UPDATE_OFFSET + NumUpdates);  
            memcpy(CustArray[UPDATE_OFFSET + NumUpdates].Bookmark,  
               CustArray[RowNum - 1].Bookmark,  
               CustArray[RowNum - 1].BookmarkLen);  
            CustArray[UPDATE_OFFSET + NumUpdates].BookmarkLen =  
               CustArray[RowNum - 1].BookmarkLen;  
            NumUpdates++;  
         } else {  
            printf("Buffers full. Send buffered changes to the data source.");  
         }  
         break;  
      case DELETE_ROW:  
         // Check if we have reached the maximum number of buffered deletes.  
         if (NumDeletes < 10) {  
            // Copy the bookmark of the row being deleted to the next available element  
            // of the buffered deletes section of CustArray and increment the delete  
            // counter. Checking to see we have not already buffered an update for  
            // this row not shown.  
            memcpy(CustArray[DELETE_OFFSET + NumDeletes].Bookmark,  
               CustArray[RowNum - 1].Bookmark,  
               CustArray[RowNum - 1].BookmarkLen);  
  
            CustArray[DELETE_OFFSET + NumDeletes].BookmarkLen =  
               CustArray[RowNum - 1].BookmarkLen;  
  
            NumDeletes++;  
         } else  
            printf("Buffers full. Send buffered changes to the data source.");  
         break;  
  
      case ADD_ROW:  
         // reached maximum number of buffered inserts?  
         if (NumInserts < 10) {  
            // Get the new customer data and place it in the next available element of  
            // the buffered inserts section of CustArray and increment insert counter.  
            // GetNewCustData(CustArray, INSERT_OFFSET + NumInserts);  
            NumInserts++;  
         } else  
            printf("Buffers full. Send buffered changes to the data source.");  
         break;  
  
      case SEND_TO_DATA_SOURCE:  
         // If there are any buffered updates, inserts, or deletes, set the array size  
         // to that number, set the binding offset to use the data in the buffered  
         // update, insert, or delete part of CustArray, and call SQLBulkOperations to  
         // do the updates, inserts, or deletes. Because we will never have more than  
         // 10 updates, inserts, or deletes, we can use the same row status array.  
         if (NumUpdates) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumUpdates, 0);  
            BindOffset = UPDATE_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_UPDATE_BY_BOOKMARK);  
            NumUpdates = 0;  
         }  
  
         if (NumInserts) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumInserts, 0);  
            BindOffset = INSERT_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_ADD);  
            NumInserts = 0;  
         }  
  
         if (NumDeletes) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumDeletes, 0);  
            BindOffset = DELETE_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_DELETE_BY_BOOKMARK);  
            NumDeletes = 0;  
         }  
  
         // If there were any updates, inserts, or deletes, reset the binding offset  
         // and array size to their original values.  
         if (NumUpdates || NumInserts || NumDeletes) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);  
            BindOffset = 0;  
         }  
         break;  
   }  
   // }  
  
   // Close the cursor.  
   SQLFreeStmt(hstmt, SQL_CLOSE);  
}  
```  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка к столбцу в результирующем наборе буфера|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выборка блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Получение одного поля дескриптора|[Функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Получение нескольких полей дескриптора|[Функция SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Настройка одного поля дескриптора|[Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Задание нескольких полей дескриптора|[Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Позиционирование курсора, обновление данных в наборе строк или удаления данных в наборе строк|[Функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|С помощью атрибута инструкции|[Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
