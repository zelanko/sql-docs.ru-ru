---
title: Функция SQLBulkOperations | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06a1997b482c45ea4b529c1230ef1cb2c61dc873
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63237851"
---
# <a name="sqlbulkoperations-function"></a>Функция SQLBulkOperations
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0 стандартов соответствия: интерфейс ODBC  
  
 **Сводка**  
 **SQLBulkOperations** выполняет операции массовой вставки и закладка массовой операции, включая обновления, удаления и выборку по закладкам.  
  
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
 [Вход] Выполняемая операция:  
  
 SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK  
  
 Дополнительные сведения см. в разделе «Примечания».  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, or SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLBulkOperations** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из Значение SQL_HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые при помощи **SQLBulkOperations** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)» . Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
 Для всех этих SQLSTATE, которые могут возвращать значение SQL_SUCCESS_WITH_INFO или SQL_ERROR (за исключением SQLSTATE 01xxx) возвращается SQL_SUCCESS_WITH_INFO, если в одной или нескольким, но не все строки многострочной операции происходит ошибка, и возвращается значение SQL_ERROR, если произошла ошибка Операция одной строки.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Усечение строковых данных справа|*Операции* аргумент был SQL_FETCH_BY_BOOKMARK и символьные или двоичные данные, возвращаемые для столбца или столбцов с типом данных SQL_C_CHAR и SQL_C_BINARY возникло усечение непустых символьных или двоичных данных от NULL.|  
|01S01|Ошибка в строке|*Операции* аргумент был SQL_ADD и при выполнении операции произошла ошибка в одну или несколько строк, но был успешно добавлен хотя бы одна строка. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).<br /><br /> (Эта ошибка возникает только в том случае, если приложение работает с ODBC 2. *x* драйвера.)|  
|01S07|Частичное усечение|*Операции* аргумент был SQL_FETCH_BY_BOOKMARK, тип данных буфера приложения не SQL_C_CHAR и SQL_C_BINARY и данные, возвращаемые буферы приложения для одного или нескольких столбцов были усечены. (Для числовых типов данных C, были усечены дробная часть числа. Для времени, метка времени и типы данных интервала C, содержащих компонент времени десятичная часть времени были усечены.)<br /><br /> (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07006|Нарушение атрибута ограниченного типа данных|*Операции* аргумент был SQL_FETCH_BY_BOOKMARK, а значение столбца в результирующем наборе не удалось преобразовать тип данных, указанный в *TargetType* аргумента в вызове **SQLBindCol**.<br /><br /> *Операции* аргумент был SQL_UPDATE_BY_BOOKMARK или SQL_ADD, и значение данных в буферы приложения не удалось преобразовать в тип данных столбца в результирующем наборе.|  
|07009|Недопустимый индекс дескриптора|Аргумент *операции* было SQL_ADD, и столбец был привязан с номером столбца больше, чем количество столбцов в результирующем наборе.|  
|21S02|Структура полученной таблицы не соответствует списку столбцов|Аргумент *операции* SQL_UPDATE_BY_BOOKMARK; и отсутствуют столбцы имели обновляемых, так как все столбцы были свободные или только для чтения, или значение в буфер связанного длины и индикатора было SQL_COLUMN_IGNORE.|  
|22001|Усечение строковых данных справа|Назначение символьное или двоичное значение в столбец в результирующем наборе привело к усечению непустым (для символов) или символов, отличных от null (для двоичного файла) или байтов.|  
|22003|Численное значение вне допустимого диапазона|*Операции* аргумент был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, и назначение числовое значение для столбца в результирующем наборе вызвало целиком (в отличие от долей) часть усекаемое число.<br /><br /> Аргумент *операции* было SQL_FETCH_BY_BOOKMARK, и возвращает числовое значение для одного или нескольких привязанных столбцов могло привести к потере значащих цифр.|  
|22007|Формат недопустимые даты и времени|*Операции* аргумент был SQL_ADD или SQL_UPDATE_BY_BOOKMARK и присвоение значения даты или метки времени для столбца в результирующем наборе приводит год, месяц или день поле должно быть вне допустимого диапазона.<br /><br /> Аргумент *операции* был SQL_FETCH_BY_BOOKMARK и возврат значения даты или метки времени для одного или нескольких привязанных столбцов вызвало бы год, месяц или день поле должно быть вне допустимого диапазона.|  
|22008|Переполнение поля даты и времени|*Операции* аргумент был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, и привела к производительность datetime арифметика на данные, отправляемые в столбец в результирующем наборе, в поле даты и времени (год, месяц, день, час, минуты или секунды поле) в результате падает за пределами допустимого диапазона значений для поля или недопустимом на основе правил естественным григорианского календаря для значений даты и времени.<br /><br /> *Операции* аргумент был SQL_FETCH_BY_BOOKMARK и производительность datetime арифметика на данных, извлекаемых из результирующего набора привело к datetime поле (год, месяц, день, час, минуту или второе поле) результат падает за пределами допустимого диапазона значений для поля или допустимыми основан на григорианском календаре естественным правила для значений даты и времени.|  
|22015|Переполнение поля интервала|*Операции* аргумент был SQL_ADD или SQL_UPDATE_BY_BOOKMARK и назначение точным или тип интервала C период, в тип данных SQL привело к потере значащих цифр.<br /><br /> *Операции* аргумент был SQL_ADD или SQL_UPDATE_BY_BOOKMARK; произошла при назначении период, в тип SQL не представление значения типа C в интервале тип SQL.<br /><br /> *Операции* аргумент был SQL_FETCH_BY_BOOKMARK и присвоение тип интервала C из точное числовое значение или интервал тип SQL привело к потере значащих цифр в начале поля.<br /><br /> *Операции* аргумент был SQL_FETCH_BY_BOOKMARK; присвоить тип интервала C, возникла не представление значения типа SQL в тип интервала C.|  
|22018|Недопустимое символьное значение для спецификации приведения|*Операции* аргумент был SQL_FETCH_BY_BOOKMARK; тип C был точное или Приблизительное числовое, datetime или тип интервала данных; тип SQL столбца был в символьный тип данных; и значение в столбце не является допустимым литерал типа, C.<br /><br /> Аргумент *операции* SQL_ADD или SQL_UPDATE_BY_BOOKMARK; тип SQL был точное или Приблизительное числовое, datetime или тип интервала данных; тип C был SQL_C_CHAR; и значение в столбце не является допустимым литералом из связанный тип SQL.|  
|23000|Нарушение ограничения целостности|*Операции* аргумент был SQL_ADD, SQL_DELETE_BY_BOOKMARK или SQL_UPDATE_BY_BOOKMARK и было нарушено ограничение целостности.<br /><br /> *Операции* аргумент был SQL_ADD и столбец, который не привязан, определен как NOT NULL, а нет значения по умолчанию.<br /><br /> *Операции* аргумент был SQL_ADD, длина, указанная в качестве границы *StrLen_or_IndPtr* буфер был SQL_COLUMN_IGNORE и столбце не было значения по умолчанию.|  
|24000|Недопустимое состояние курсора|*StatementHandle* была выполненного состоянии, но результирующий набор не связан с *StatementHandle*.|  
|40001|Сбой сериализации|Выполнен откат транзакции из-за взаимоблокировки ресурсов с другой транзакцией.|  
|40003|Состояние транзакции неизвестно|Не удалось выполнить связанное соединение во время выполнения этой функции и не удается определить состояние транзакции.|  
|42000|Синтаксическая ошибка или нарушение доступа|Драйвер не удалось заблокировать строку для выполнения операции, запрашиваемой в *операции* аргумент.|  
|44000|Нарушение параметра WITH CHECK OPTION|*Операции* аргумент был SQL_ADD или SQL_UPDATE_BY_BOOKMARK и вставка или обновление было выполнено в просматриваемой таблице (или таблицы, полученного из просматриваемого таблицы), созданный путем указания **WITH CHECK OPTION**, так что одна или несколько строк, затронутых путем вставки или обновления больше не присутствовать в просматриваемой таблице.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция был снова вызван для *StatementHandle*.<br /><br /> Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. Если по-прежнему выполнении асинхронной функции **SQLBulkOperations** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.<br /><br /> (DM) указанного *StatementHandle* не находился в состоянии выполненного. Функция был вызван без предварительного вызова функции **SQLExecDirect**, **SQLExecute**, или функции каталога.<br /><br /> (DM) асинхронно выполняемой функции (не такой) был вызван для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLSetPos** был вызван для *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.<br /><br /> (DM) драйвер был ODBC 2. *x* драйвер, и **SQLBulkOperations** был вызван для *StatementHandle* перед **SQLFetchScroll** или **SQLFetch**  был вызван.<br /><br /> (DM) **SQLBulkOperations** был вызван после **SQLExtendedFetch** был вызван для *StatementHandle*.|  
|HY011|Атрибут нельзя установить сейчас|(DM) драйвер был ODBC 2. *x* драйвер и атрибут значения SQL_ATTR_ROW_STATUS_PTR инструкции было установлено между вызовами **SQLFetch** или **SQLFetchScroll** и **SQLBulkOperations** .|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|*Операции* аргумент был SQL_ADD или SQL_UPDATE_BY_BOOKMARK; значение данных не был пустым указателем; был тип данных C SQL_C_BINARY и SQL_C_CHAR; и значение Длина столбца меньше 0, но не равны в значение SQL_DATA_AT_EXEC , SQL_COLUMN_IGNORE, SQL_NTS или SQL_NULL_DATA, или меньше или равно SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Значение в буфер длины/индикатора было значение SQL_DATA_AT_EXEC; тип SQL был SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных long зависящие от источника данных; и введите сведения SQL_NEED_LONG_DATA_LEN **SQLGetInfo** был «Y».<br /><br /> *Операции* аргумент был SQL_ADD и атрибут инструкции SQL_ATTR_USE_BOOKMARK было присвоено SQL_UB_VARIABLE 0 был привязан к буфер, длина которого не равна длине максимального закладки для данного результирующего набора. (Эта длина доступен в поле SQL_DESC_OCTET_LENGTH IRD и может быть получен путем вызова **SQLDescribeCol**, **SQLColAttribute**, или **SQLGetDescField**.)|  
|HY092|Недопустимый атрибут идентификатора|(DM) значение, заданное для *операции* предоставил недопустимый аргумент.<br /><br /> *Операции* аргумент был SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK и атрибута инструкции SQL_ATTR_CONCURRENCY было присвоено SQL_CONCUR_READ_ONLY.<br /><br /> *Операции* аргумент был SQL_DELETE_BY_BOOKMARK, SQL_FETCH_BY_BOOKMARK или SQL_UPDATE_BY_BOOKMARK и не был привязан столбец закладки или атрибут инструкции SQL_ATTR_USE_BOOKMARKS было задано SQL_UB_OFF.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Дополнительная возможность не реализована|Драйвер или источник данных не поддерживает операции, запрашиваемой в *операции* аргумент.|  
|HYT00|Время ожидания истекло|Время ожидания запроса истекло раньше, чем источник данных вернул результирующий набор. Период ожидания задается с помощью **SQLSetStmtAttr** с *атрибут* аргумент SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|Опрос недоступен в режиме асинхронное уведомление|Каждый раз, когда используется модель уведомлений, отключен опроса.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущий вызов функции в дескриптор возвращает SQL_STILL_EXECUTING, и если включен режим уведомлений, **SQLCompleteAsync** должен вызываться с дескриптором постобработки и завершить операцию.|  
  
## <a name="comments"></a>Комментарии  
  
> [!CAUTION]  
>  Сведения о том, какие инструкции **SQLBulkOperations** может вызываться в и что необходимо сделать для обеспечения совместимости с ODBC 2. *x* приложений, см. в разделе [блочные курсоры, Прокручиваемые курсоры и обратная совместимость](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) разделе в приложении G: Рекомендации по драйверов для обеспечения обратной совместимости.  
  
 Приложение использует **SQLBulkOperations** для выполнения следующих операций в базовой таблице или представлению, которое соответствует текущему запросу:  
  
-   Добавьте новые строки.  
  
-   Обновите набор строк, где каждая строка определяется закладки.  
  
-   Удаление набора строк, где каждая строка определяется закладки.  
  
-   Получите набор строк, где каждая строка определяется закладки.  
  
 После вызова **SQLBulkOperations**, позицию курсора блок не определено. Приложение должно вызвать **SQLFetchScroll** для установки положения курсора. Приложение должно вызывать **SQLFetchScroll** только с *FetchOrientation* SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE или инструкция SQL_FETCH_BOOKMARK аргумента. Положение курсора не определено, если приложение вызывает **SQLFetch** или **SQLFetchScroll** с *FetchOrientation* аргумент SQL_FETCH_PRIOR, SQL_FETCH_NEXT, или SQL_FETCH_RELATIVE.  
  
 Столбец может игнорироваться в массовой операции, выполняемые с помощью вызова **SQLBulkOperations** , задав буфер длины/индикатора столбец, указанный в вызове **SQLBindCol**, чтобы SQL_COLUMN_IGNORE.  
  
 Нет необходимости для приложения, чтобы присвоить атрибуту инструкции SQL_ATTR_ROW_OPERATION_PTR, при вызове **SQLBulkOperations** поскольку строки нельзя пропустить при выполнении массовых операций с этой функцией.  
  
 Буфер, на которые указывают атрибут инструкции SQL_ATTR_ROWS_FETCHED_PTR содержит количество строк, затронутых при вызове **SQLBulkOperations**.  
  
 Когда *операции* равно SQL_ADD или SQL_UPDATE_BY_BOOKMARK и список выбора спецификация запроса, связанный с курсором содержит более одной ссылки в том же столбце, он драйвера — определен ли ошибка создается или драйвер не учитывает повторяющиеся ссылки и выполняет операции.  
  
 Дополнительные сведения об использовании **SQLBulkOperations**, см. в разделе [обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).  
  
## <a name="performing-bulk-inserts"></a>Выполнения массовых вставок  
 Для вставки данных с помощью **SQLBulkOperations**, приложение выполняет следующие действия:  
  
1.  Выполняет запрос, который возвращает результирующий набор.  
  
2.  Задает число строк, которые необходимо вставить инструкцию атрибута SQL_ATTR_ROW_ARRAY_SIZE.  
  
3.  Вызовы **SQLBindCol** для привязки данных, в которой необходимо вставить. Данные привязываются к массиву с размером, равным значение SQL_ATTR_ROW_ARRAY_SIZE.  
  
    > [!NOTE]  
    >  Размер массива, на которые указывают атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR должно быть равно SQL_ATTR_ROW_ARRAY_SIZE или значения SQL_ATTR_ROW_STATUS_PTR должно быть пустым указателем.  
  
4.  Вызовы **SQLBulkOperations**(*StatementHandle,* SQL_ADD) для выполнения вставки.  
  
5.  Если приложение установило атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR, для проверки этого массива, чтобы увидеть результат операции.  
  
 Если приложение связывает столбец 0, перед вызовом **SQLBulkOperations** с *операции* аргумент SQL_ADD, драйвер будет обновлять буферах связанных столбцов 0 значениями, закладка вновь вставленная строка. Это произошло приложение должно установить атрибут инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE до выполнения инструкции. (Это не работает с ODBC 2. *x* драйвера.)  
  
 Длинные данные могут добавляться в части с помощью SQLBulkOperations, с помощью вызова методов SQLParamData и SQLPutData. Дополнительные сведения см. в разделе «Предоставление Long данных Bulk INSERT и Update» далее в этом справочнике по функциям.  
  
 Это необходимо для приложения для вызова **SQLFetch** или **SQLFetchScroll** перед вызовом **SQLBulkOperations** (кроме случаев, когда начинается с ODBC 2. *x* драйвера; см. описание [обратной совместимости и соответствия стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)).  
  
 Поведение драйвер определенное, если **SQLBulkOperations**, с помощью *операции* аргумент SQL_ADD, вызывается в курсоре, который содержит повторяющиеся столбцы. Драйвер может возвращать SQLSTATE, определяемым драйвером, добавляют данные в первый столбец, который отображается в результатах, и выполнять другие правила поведения, определяемые драйвером.  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>Выполнение групповых обновлений с помощью закладок  
 Для выполнения массового обновления с помощью закладок с **SQLBulkOperations**, приложение выполняет следующие действия в последовательности:  
  
1.  Задает атрибут инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, который возвращает результирующий набор.  
  
3.  Задает число строк, которые необходимо обновить инструкции атрибута SQL_ATTR_ROW_ARRAY_SIZE.  
  
4.  Вызовы **SQLBindCol** для привязки данных, в которой необходимо обновить. Данные привязываются к массиву с размером, равным значение SQL_ATTR_ROW_ARRAY_SIZE. Он также вызовет **SQLBindCol** для привязки столбца 0 (столбец закладки).  
  
5.  Копирует закладок для строк, что он заинтересован в обновление в массив, привязанное к столбцу 0.  
  
6.  Обновляет данные в привязанных буферах.  
  
    > [!NOTE]  
    >  Размер массива, на которые указывают атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR должен быть равным SQL_ATTR_ROW_ARRAY_SIZE или значения SQL_ATTR_ROW_STATUS_PTR должно быть пустым указателем.  
  
7.  Вызовы **SQLBulkOperations**(*StatementHandle,* SQL_UPDATE_BY_BOOKMARK).  
  
    > [!NOTE]  
    >  Если приложение установило атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR, для проверки этого массива, чтобы увидеть результат операции.  
  
8.  При необходимости вызывает **SQLBulkOperations**(*StatementHandle*, SQL_FETCH_BY_BOOKMARK) для выборки данных в буферах привязанного приложения чтобы убедиться, что произошло обновление.  
  
9. Если данные были обновлены, драйвер изменяет значение в массиве строк состояния для соответствующих строк на SQL_ROW_UPDATED.  
  
 Массовых обновлений, выполненных **SQLBulkOperations** может включать большие объемы данных с помощью вызова **SQLParamData** и **SQLPutData**. Дополнительные сведения см. в разделе «Предоставление Long данных Bulk INSERT и Update» далее в этом справочнике по функциям.  
  
 Если закладки сохраняются на курсоры, приложению не требуется вызывать **SQLFetch** или **SQLFetchScroll** перед обновлением с закладки. Он может использовать закладки, которые он сохранен из предыдущих курсора. Если закладки не сохраняются на курсоры, приложение должно вызвать **SQLFetch** или **SQLFetchScroll** извлекаемого закладки.  
  
 Поведение драйвер определенное, если **SQLBulkOperations**, с помощью *операции* аргумент SQL_UPDATE_BY_BOOKMARK, вызывается в курсоре, который содержит повторяющиеся столбцы. Драйвер может возвращать SQLSTATE, определяемым драйвером, обновить первый столбец, который отображается в результирующем наборе или выполнить другие правила поведения, определяемые драйвером.  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>Выполнение массового извлекает с помощью закладок  
 Для выполнения массовой выборки с помощью закладок с **SQLBulkOperations**, приложение выполняет следующие действия в последовательности:  
  
1.  Задает атрибут инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, который возвращает результирующий набор.  
  
3.  Задает число строк, которые он хочет получить инструкцию атрибута SQL_ATTR_ROW_ARRAY_SIZE.  
  
4.  Вызовы **SQLBindCol** для привязки данных, в которой необходимо получить. Данные привязываются к массиву с размером, равным значение SQL_ATTR_ROW_ARRAY_SIZE. Он также вызовет **SQLBindCol** для привязки столбца 0 (столбец закладки).  
  
5.  Копирует закладок для строк, что он заинтересован в получении в массив, привязанное к столбцу 0. (Предполагается, что приложение уже получал закладки отдельно.)  
  
    > [!NOTE]  
    >  Размер массива, на которые указывают атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR должен быть равным SQL_ATTR_ROW_ARRAY_SIZE или значения SQL_ATTR_ROW_STATUS_PTR должно быть пустым указателем.  
  
6.  Вызовы **SQLBulkOperations**(*StatementHandle,* SQL_FETCH_BY_BOOKMARK).  
  
7.  Если приложение установило атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR, для проверки этого массива, чтобы увидеть результат операции.  
  
 Если закладки сохраняются на курсоры, приложению не требуется вызывать **SQLFetch** или **SQLFetchScroll** перед извлечением с закладки. Он может использовать закладки, которые он сохранен из предыдущих курсора. Если закладки не сохраняются на курсоры, приложение должно вызвать **SQLFetch** или **SQLFetchScroll** один раз для получения закладки.  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>Выполнение массового удаления с помощью закладок  
 Чтобы выполнить массовое удаление с помощью закладок с **SQLBulkOperations**, приложение выполняет следующие действия в последовательности:  
  
1.  Задает атрибут инструкции SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, который возвращает результирующий набор.  
  
3.  Задает число строк, которые он хочет удалить атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции.  
  
4.  Вызовы **SQLBindCol** для привязки столбца 0 (столбец закладки).  
  
5.  Копирует закладок для строк, что он заинтересован в удалении в массиве, привязанное к столбцу 0.  
  
    > [!NOTE]  
    >  Размер массива, на которые указывают атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR должен быть равным SQL_ATTR_ROW_ARRAY_SIZE или значения SQL_ATTR_ROW_STATUS_PTR должно быть пустым указателем.  
  
6.  Вызовы **SQLBulkOperations**(*StatementHandle,* SQL_DELETE_BY_BOOKMARK).  
  
7.  Если приложение установило атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR, для проверки этого массива, чтобы увидеть результат операции.  
  
 Если закладки сохраняются на курсоры, приложение не имеет для вызова **SQLFetch** или **SQLFetchScroll** перед удалением с закладки. Он может использовать закладки, которые он сохранен из предыдущих курсора. Если закладки не сохраняются на курсоры, приложение должно вызвать **SQLFetch** или **SQLFetchScroll** один раз для получения закладки.  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>Предоставление данных большой длины для операции массовой вставки и обновления  
 Длинные данные могут быть предоставлены для массовой вставки и обновлений, выполняемых вызовов **SQLBulkOperations**. Для вставки или обновления данных long, приложение выполняет следующие действия, а также действия, описанные в разделах «Выполнения массовых вставок» и «Выполнение массового обновления с помощью закладок» ранее в этом разделе.  
  
1.  Когда он выполняет привязку данных с помощью **SQLBindCol**, приложение размещает определяемое приложением значение, например номер столбца в  *\*TargetValuePtr* буфер для данных времени выполнения столбцы. Значение может использоваться для идентификации столбца.  
  
     Приложение размещает результат значение SQL_LEN_DATA_AT_EXEC (*длина*) в макрос  *\*StrLen_or_IndPtr* буфера. Если тип данных SQL столбца является SQL_LONGVARBINARY, SQL_LONGVARCHAR или тип данных long зависящие от источника данных и драйвер возвращает «Y» для типа данных SQL_NEED_LONG_DATA_LEN в **SQLGetInfo**, *длина*  — количество байтов данных, отправляемых для параметра; в противном случае оно должно быть неотрицательное значение и учитывается.  
  
2.  Когда **SQLBulkOperations** вызывается, при наличии столбцов данных времени выполнения, функция возвращает SQL_NEED_DATA и переходит к шагу 3, который следует за. (Если нет столбцов данных времени выполнения, процесс будет завершен.)  
  
3.  Приложение вызывает **SQLParamData** для извлечения адреса  *\*TargetValuePtr* буфера для первого столбца данных во время выполнения для обработки. **SQLParamData** возвращает SQL_NEED_DATA. Приложение извлекает значение, определенное приложением, от  *\*TargetValuePtr* буфера.  
  
    > [!NOTE]  
    >  Несмотря на то, что параметры данных времени выполнения напоминают столбцов данных времени выполнения, значение, возвращаемое функцией **SQLParamData** отличается для каждого.  
  
     Столбцы данных во время выполнения являются столбцами в наборе строк, для которого данные будут отправлены с **SQLPutData** при обновлении или вставке с строки **SQLBulkOperations**. Они связаны с **SQLBindCol**. Значение, возвращенное **SQLParamData** — это адрес строки в **TargetValuePtr* буфера, который обрабатывается.  
  
4.  Приложение вызывает **SQLPutData** один или несколько раз для отправки данных для столбца. Более чем один вызов является обязательным, если все значения данных не может быть возвращен в  *\*TargetValuePtr* буфера, указанного в **SQLPutData**; несколько вызовов **SQLPutData** для того же столбца разрешены только в том случае, при отправке данных символа C к столбцу с типом данных зависящие от источника символьных, двоичных или данных, или при отправке двоичных данных C для столбца с символом, двоичных данных, или тип данных зависящие от источника данных.  
  
5.  Приложение вызывает **SQLParamData** еще раз, чтобы сообщить, что все данные отправлены для столбца.  
  
    -   Если имеются дополнительные столбцы данных времени выполнения, **SQLParamData** возвращает SQL_NEED_DATA и адрес *TargetValuePtr* буфер для следующего столбца данных во время выполнения для обработки. Приложение повторяет шаги 4 и 5.  
  
    -   Если больше нет столбцов данных времени выполнения, процесс будет завершен. Если инструкция была выполнена успешно, **SQLParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO; Если выполнение завершилось сбоем, возвращается значение SQL_ERROR. На этом этапе **SQLParamData** может возвращать любой SQLSTATE, которые могут быть возвращены с **SQLBulkOperations**.  
  
 Если операция отменена, или произошла ошибка в **SQLParamData** или **SQLPutData** после **SQLBulkOperations** возвращает SQL_NEED_DATA и перед отправкой данных для всех столбцы данных времени выполнения, приложение может вызвать только **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions** , **SQLParamData**, или **SQLPutData** для инструкции или соединения, связанного с инструкцией. Если он вызывает любой другой функции для инструкции или соединения, связанного с инструкцией, функция возвращает значение SQL_ERROR и параметром SQLSTATE HY010 (функционировать ошибка последовательности).  
  
 Если приложение вызывает **SQLCancel** пока драйвер по-прежнему нужны данные для столбцов данных времени выполнения, драйвер отменяет операцию. Затем приложение может вызвать **SQLBulkOperations** снова; Отмена не влияет на состояние курсора или текущую позицию курсора.  
  
## <a name="row-status-array"></a>Массив статусов строк  
 Массив статусов строк содержит значения состояния для каждой строки данных в наборе строк после вызова **SQLBulkOperations**. Драйвер задает значения состояний в этом массиве после вызова **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**, или **SQLBulkOperations** . Этот массив изначально была заполнена с помощью вызова **SQLBulkOperations** Если **SQLFetch** или **SQLFetchScroll** не был вызван перед **SQLBulkOperations** . Этот массив указывает атрибут значения SQL_ATTR_ROW_STATUS_PTR инструкции. Количество элементов в массивах состояния строк должно быть равно количество строк в наборе строк (как определено в атрибуте SQL_ATTR_ROW_ARRAY_SIZE инструкции). Сведения об этом массив статусов строк, см. в разделе [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Пример кода  
 Следующий пример извлекает 10 строк данных одновременно из таблицы Customers. Затем оно предлагает от пользователя действие выполнить. Для снижения сетевого трафика, буфер пример обновления, удаления и вставляет локально в привязанные массивы, но с смещениями строк данных в прошлом. Когда пользователь выбирает отправку обновления, удаления и вставляет в источник данных, код устанавливает привязки, смещение соответствующим образом и вызывает **SQLBulkOperations**. Для простоты пользователь не может буфера более чем 10 обновления, удаления и вставки.  
  
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
|Привязка к столбцу в результирующем наборе буфер|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработка инструкций|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Блока данных или прокрутке результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Получение одного поля дескриптора|[Функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Получение нескольких полей дескриптора|[Функция SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Задание одного поля дескриптора|[Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Задание нескольких полей дескриптора|[Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Позиционирование курсора, обновление данных в наборе строк или удаления данных в наборе строк|[Функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Присвоение атрибуту инструкции|[Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
