---
title: Функция S'LBulkOperations (ru) Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBulkOperations
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBulkOperations
helpviewer_keywords:
- SQLBulkOperations function [ODBC]
ms.assetid: 7029d0da-b0f2-44e6-9114-50bd96f47196
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f4f294a6d84856bc3065b599a370bb5658e3ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301334"
---
# <a name="sqlbulkoperations-function"></a>Функция SQLBulkOperations
**Соответствия**  
 Версия Введена: Соответствие стандартам ODBC 3.0: ODBC  
  
 **Сводка**  
 **СЗЛБалКОперации** выполняют объемные вставки и оптовые операции закладок, включая обновление, удаление и получение закладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLBulkOperations(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Operation);  
```  
  
## <a name="arguments"></a>Аргументы  
 *Обработка заявления*  
 (Вход) Ручка оператора.  
  
 *Операции*  
 (Вход) Операция по выполнению:  
  
 SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK  
  
 Для получения дополнительной информации см.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 При возврате SQL_ERROR или **SQL_SUCCESS_WITH_INFO,** связанные с этим значения S'LSTATE могут быть получены, позвонив по **телефону s'LGetDiagRec** с *помощью handleType* of SQL_HANDLE_STMT и *ручки* *выписки.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **СЗЛБалКОперации,** и приведены в контексте этой функции. нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
 Для всех тех S'LSTATEs, которые могут вернуться SQL_SUCCESS_WITH_INFO или SQL_ERROR (кроме 01xxx S'LSTATEs), SQL_SUCCESS_WITH_INFO возвращается, если ошибка происходит на одном или нескольких, но не все строки многорычного операции, и SQL_ERROR возвращается, если ошибка происходит на однострокоперации.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Усечение правой строки данных|Аргумент *операции* был SQL_FETCH_BY_BOOKMARK, и строка или двоичные данные, возвращенные для столбца или столбцов с типом данных SQL_C_CHAR или SQL_C_BINARY привели к усечению непустого символа или не-NULL двоичных данных.|  
|01S01|Ошибка в строке|Аргумент *операции* был SQL_ADD, и ошибка произошла в одном или нескольких строках при выполнении операции, но по крайней мере одна строка была успешно добавлена. (Функция возвращает SQL_SUCCESS_WITH_INFO.)<br /><br /> (Эта ошибка возникает только тогда, когда приложение работает с ODBC 2. *x* водитель.)|  
|01S07|Фракционная усечение|*Аргументоперации* был SQL_FETCH_BY_BOOKMARK, тип данных буфера приложения не был SQL_C_CHAR или SQL_C_BINARY, и данные, возвращенные в буферы приложений для одного или нескольких столбцов, были усечены. (Для численных типов C данных дробная часть числа была усечена. Для типов данных времени, меток времени и интервала C, содержащих временной компонент, дробная часть времени была усечена.)<br /><br /> (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|07006|Нарушение атрибута типа ограниченного доступа|Аргумент *операции* был SQL_FETCH_BY_BOOKMARK, и значение данных столбца в наборе результатов не может быть преобразовано в тип данных, указанный аргументом *TargetType* в вызове на **S'LBindCol.**<br /><br /> Аргумент *операции* был SQL_UPDATE_BY_BOOKMARK или SQL_ADD, и значение данных в буферах приложения не может быть преобразовано в тип данных столбца в наборе результатов.|  
|07009|Недействительный индекс дескриптора|Аргумент *Операция* была SQL_ADD, и столбец был связан с числом столбцов, превышающее количество столбцов в наборе результатов.|  
|21S02|Степень производной таблицы не соответствует списку столбцов|Аргумент *операция* была SQL_UPDATE_BY_BOOKMARK; и никакие столбцы не были updatable, потому что все столбцы были либо несвязанными, либо только для чтения, или значение в буфере длины/индикатора оговорок между границами SQL_COLUMN_IGNORE.|  
|22001|Усечение правой строки данных|Назначение символа или двоичного значения столбцюку в наборе результатов привело к усечению непустых (для персонажей) или ненулевых (для двоичных) символов или байтов.|  
|22003|Числовое значение вне диапазона|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, и назначение численного значения столбцу в наборе результатов привело к тому, что вся (в отличие от дробной) часть числа была усечена.<br /><br /> Аргумент *операции* был SQL_FETCH_BY_BOOKMARK, и возвращение численного значения для одного или нескольких связанных столбцов привело бы к потере значительных цифр.|  
|22007|Недействительный формат дата-времени|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, и назначение значения даты или метки времени в столбец в наборе результатов привело к тому, что поле года, месяца или дня было вне диапазона.<br /><br /> Аргумент *Операции* был SQL_FETCH_BY_BOOKMARK, и возвращение значения даты или метки времени для одного или нескольких связанных столбцов привело бы к тому, что поле года, месяца или дня было бы вне диапазона.|  
|22008|Переполниние поля даты/времени|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, а также выполнение арифметики дат на данных, отправляемых в столбец в наборе результатов, привело к тому, что поле времени даты (год, месяц, день, час, минута или второе поле) результата, выпадающего за пределы допустимого диапазона значений для поля или недействительного на основе естественных правил григорианского календаря для datetimes.<br /><br /> Аргумент *операции* был SQL_FETCH_BY_BOOKMARK, и выполнение арифметики дат на данных, извлекаемых из набора результатов, привело к тому, что поле времени даты (год, месяц, день, час, минута или второе поле) результата, выпадающего за пределы допустимого диапазона значений для поля или недействительное на основе естественных правил григорианского календаря для datetimes.|  
|22015|Переполниние поля интервала|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, и назначение точного типа c числа или интервала C к интервалу типа данных S'L вызвало потерю значительных цифр.<br /><br /> Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK; при назначении к типу интервала S'L не было представления значения типа C в типе интервала S'L.<br /><br /> Аргумент *операции* был SQL_FETCH_BY_BOOKMARK, и присвоение от точного числа или интервала типа S'L к типу интервала C вызвало потерю значительных цифр в ведущем поле.<br /><br /> Аргументом *операции* было SQL_FETCH_BY_BOOKMARK; при назначении типа интервала C в типе интервала C не было представлено значение типа S'L.|  
|22018|Недействительное значение символов для спецификации литья|Аргументом *операции* было SQL_FETCH_BY_BOOKMARK; тип C был точным или приблизительным числом, временем даты или типом данных интервала; тип столбца s'L был типом данных символов; и значение в колонке не было действительным буквальным типа C.<br /><br /> Аргумент *операция* была SQL_ADD или SQL_UPDATE_BY_BOOKMARK; тип S'L был точным или приблизительным числом, временем даты или типом данных интервала; тип C был SQL_C_CHAR; и значение в колонке не было действительным буквальным из связанного типа S'L.|  
|23000|Нарушение ограничения целостности|Аргументом *операции* было SQL_ADD, SQL_DELETE_BY_BOOKMARK или SQL_UPDATE_BY_BOOKMARK, и было нарушено ограничение целостности.<br /><br /> Аргумент *операции* был SQL_ADD, и столбец, который не был связан, определяется как НЕ NULL и не имеет значения по умолчанию.<br /><br /> Аргумент *операции* был SQL_ADD, длина, указанная в связанном *StrLen_or_IndPtr* буфере, была SQL_COLUMN_IGNORE, а столбец не имел значения по умолчанию.|  
|24 000|Недопустимое состояние курсора|*StatementHandle* находился в выполненном состоянии, но ни один набор результатов не был связан с *statementHandle.*|  
|40001|Сбой сериализации|Транзакция была отката из-за взаимоблокировки ресурсов с другой транзакцией.|  
|40003|Завершение заявления неизвестно|Связанное соединение сбой во время выполнения этой функции, и состояние транзакции не может быть определено.|  
|42000|Ошибка синтаксиса или нарушение доступа|Водитель не смог заблокировать строку по мере необходимости для выполнения операции, запрошенной в аргументе *операции.*|  
|44000|Нарушение параметра WITH CHECK OPTION|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, и вставка или обновление было выполнено на просматриваемой таблице (или таблице, полученной из просматриваемой таблицы), которая была создана путем указания **С CHECK OPTION**, таким образом, что один или несколько строк, затронутых вставкой или обновлением, больше не будут присутствовать в просмотренной таблице.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхлик** был вызван на *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхливнейра** был вызван на *StatementHandle* из другого потока в многопоточном приложении.|  
|HY010|Ошибка последовательности функций|(DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *StatementHandle.* Эта асинхронная функция по-прежнему исполнялась при вызове функции **S'LBulkOperations.**<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для *statementHandle* и вернулся SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.<br /><br /> (DM) Указанное *statementHandle* не находилось в выполненном состоянии. Функция была вызвана без предварительного вызова **S'LExecDirect**, **S'LExecute**, или функции каталога.<br /><br /> (DM) Асинхронно выполнение функции (не этот) был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LSetPos** был вызван для *statementHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.<br /><br /> (DM) Водитель был ODBC 2. *x* драйвер, а **также S'LBulkOperations** был вызван для *выписки,* прежде чем **s'LFetchScroll** или **S'LFetch** был вызван.<br /><br /> (DM) **S'LBulkOperations** был вызван после того, как **S'LExtendedFetch** был вызван на *statementHandle*.|  
|HY011|Атрибут не может быть установлен сейчас|(DM) Водитель был ODBC 2. *x* драйвер, а атрибут SQL_ATTR_ROW_STATUS_PTR оператора был установлен между вызовами на **s'LFetch** или **S'LFetchScroll** и **S'LBulkOperations.**|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY090|Недействительная длина строки или буфера|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK; значение данных не является нулевой указкой; тип данных C был SQL_C_BINARY или SQL_C_CHAR; значение длины столбца было меньше 0, но не равно SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NTS или SQL_NULL_DATA или менее или равно SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Значение в буфере длины/индикатора составляло SQL_DATA_AT_EXEC; тип СЗЛ был либо SQL_LONGVARCHAR, SQL_LONGVARBINARY, либо длинным типом данных, специфичным для конкретных источников данных; а SQL_NEED_LONG_DATA_LEN информационный тип в **"СЗЛГетИнфо"** был "Y".<br /><br /> Аргумент *операции* был SQL_ADD, атрибут SQL_ATTR_USE_BOOKMARK оператора был установлен на SQL_UB_VARIABLE, а столбец 0 был привязан к буферу, длина которого не была равна максимальной длине закладки для этого набора результатов. (Эта длина доступна в SQL_DESC_OCTET_LENGTH поле IRD и может быть получена по телефону **S'LDescribeCol**, **S'LColAttribute**, или **S'LGetDescfield**.)|  
|HY092|Недействительный идентификатор атрибута|(DM) Значение, указанное для аргумента *операции,* было недействительным.<br /><br /> Аргумент *операции* был SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK, а атрибут SQL_ATTR_CONCURRENCY оператора был установлен на SQL_CONCUR_READ_ONLY.<br /><br /> Аргумент *операции* был SQL_DELETE_BY_BOOKMARK, SQL_FETCH_BY_BOOKMARK или SQL_UPDATE_BY_BOOKMARK, и столбец закладки не был связан или атрибут SQL_ATTR_USE_BOOKMARKS оператора был установлен для SQL_UB_OFF.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYC00|Дополнительная функция не реализована|Драйвер или источник данных не поддерживает операцию, запрошенную в аргументе *операции.*|  
|HYT00|Время ожидания истекло|Период тайм-аута запроса истек до того, как источник данных вернул набор результатов. Период тайм-аута устанавливается с **помощью S'LSetStmtAttr** с аргументом *атрибута* SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
|IM017|Опрос отключен в асинхронном режиме уведомления|Всякий раз, когда используется модель уведомления, опрос отключается.|  
|IM018|Для завершения предыдущей асинхронной операции на этой ручке не был вызван **S'LCompleteAsync.**|Если предыдущий вызов функции на ручке возвращается SQL_STILL_EXECUTING и если режим уведомления включен, **s'LCompleteAsync** должен быть вызван на ручку, чтобы сделать пост-обработку и завершить операцию.|  
  
## <a name="comments"></a>Комментарии  
  
> [!CAUTION]  
>  Для получения информации о том, в каком заявлении говорится, что можно вызвать **s'LBulkOperations** и что он должен сделать для совместимости с ODBC 2. *приложения x* см. раздел [«Курсоры блока», «Прокрутки» и раздел «Обратная совместимость»](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) в приложении G: Руководство по драйверам для обратной совместимости.  
  
 Приложение использует **S'LBulkOperations** для выполнения следующих операций на базовой таблице или представлении, которое соответствует текущему запросу:  
  
-   Добавить новые строки.  
  
-   Обновление набора строк, где каждая строка идентифицируется закладкой.  
  
-   Удалите набор строк, где каждая строка идентифицируется закладкой.  
  
-   Принесите набор строк, где каждая строка идентифицируется закладкой.  
  
 После вызова в **S'LBulkOperations**позиция курсора блока не определена. Для настройки положения курсора приложение должно вызвать **S'LFetchScroll.** Приложение должно **вызыватьs S'LFetchScroll** только с *аргументом FetchOrientation* SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE или SQL_FETCH_BOOKMARK. Позиция курсора не определена, если приложение вызывает **S'LFetch** или **S'LFetchScroll** с аргументом *FetchOrientation* SQL_FETCH_PRIOR, SQL_FETCH_NEXT или SQL_FETCH_RELATIVE.  
  
 Столбец может быть проигнорирован в оптовых операциях, выполняемых вызовом на **S'LBulkOperations,** установив буфер длины/индикатора столбца, указанный в вызове на **S'LBindCol,** чтобы SQL_COLUMN_IGNORE.  
  
 Приложение не обязано устанавливать атрибут SQL_ATTR_ROW_OPERATION_PTR оператора при вызове **S'LBulkOperations,** поскольку строки не могут быть проигнорированы при выполнении оптовых операций с этой функцией.  
  
 Буфер, на который указывает атрибут SQL_ATTR_ROWS_FETCHED_PTR оператора, содержит количество строк, затронутых вызовом на **S'LBulkOperations.**  
  
 Когда аргумент *Операции* SQL_ADD или SQL_UPDATE_BY_BOOKMARK и список выбора спецификации запроса, связанный с курсором, содержит несколько ссылок на один и тот же столбец, определяется ли драйвер, генерируется ли ошибка или драйвер игнорирует дублированные ссылки и выполняет запрашиваемые операции.  
  
 Для получения более подробной информации о [Updating Data with SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)том, как использовать **S'LBulkOperations,** см.  
  
## <a name="performing-bulk-inserts"></a>Выполнение массовых вставок  
 Для вставки данных с **помощью S'LBulkOperations**приложение выполняет следующую последовательность шагов:  
  
1.  Выполняет запрос, который возвращает набор результатов.  
  
2.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE оператора на количество строк, которые он хочет вставить.  
  
3.  Вызывает **S'LBindCol,** чтобы связать данные, которые он хочет вставить. Данные привязаны к массиву с размером, равным значению SQL_ATTR_ROW_ARRAY_SIZE.  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут SQL_ATTR_ROW_STATUS_PTR оператора, должен быть либо равен SQL_ATTR_ROW_ARRAY_SIZE, либо SQL_ATTR_ROW_STATUS_PTR должен быть нулевой указателем.  
  
4.  Для выполнения вставки вызывает **s'LBulkOperations***(заявление,* SQL_ADD).  
  
5.  Если приложение установило атрибут SQL_ATTR_ROW_STATUS_PTR оператора, оно может проверить этот массив, чтобы увидеть результат операции.  
  
 Если приложение связывает столбец 0 до вызова **S'LBulkOperations** с аргументом *операции* SQL_ADD, драйвер обновит буферы связанного столбца 0 со значениями закладки для вновь вставленного ряда. Для этого приложение должно установить атрибут SQL_ATTR_USE_BOOKMARKS оператора на SQL_UB_VARIABLE перед выполнением оператора. (Это не работает с ODBC 2. *x* водитель.)  
  
 Длинные данные могут быть добавлены в части с помощью s'LBulkOperations, используя вызовы на S'LParamData и S'LPutData. Для получения дополнительной информации, см. "Предоставление длинных данных для массовых вставок и обновлений" позже в этой функции ссылки.  
  
 Это не обязательно для приложения, чтобы позвонить **s'LFetch** или **S'LFetchScroll,** прежде чем он вызывает **S'LBulkOperations** (за исключением, когда происходит против ODBC 2.* x* драйвер; см [Назад совместимость и соответствие стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)).  
  
 Поведение определяется драйвером, если **аргумент** *операции* SQL_ADD называется на курсоре, содержащем дубликаты столбцов. Водитель может вернуть драйвер-определяемый S'Lstate, добавить данные в первый столбец, который отображается в наборе результатов, или выполнить другое поведение, определяемое драйвером.  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>Выполнение массовых обновлений с помощью закладок  
 Для выполнения оптовых обновлений с помощью закладок с **помощью S'LBulkOperations**, приложение выполняет следующие шаги последовательно:  
  
1.  Устанавливает атрибут SQL_ATTR_USE_BOOKMARKS оператора на SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, который возвращает набор результатов.  
  
3.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE оператора на количество строк, которые он хочет обновить.  
  
4.  Вызывает **S'LBindCol,** чтобы связать данные, которые он хочет обновить. Данные привязаны к массиву с размером, равным значению SQL_ATTR_ROW_ARRAY_SIZE. Он также вызывает **S'LBindCol,** чтобы связать столбец 0 (столбец закладки).  
  
5.  Копирует закладки для строк, которые он заинтересован в обновлении в массив, связанный с столбцей 0.  
  
6.  Обновление данных в связанных буферах.  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут SQL_ATTR_ROW_STATUS_PTR оператора, должен быть равен SQL_ATTR_ROW_ARRAY_SIZE или SQL_ATTR_ROW_STATUS_PTR должен быть нулевой указателем.  
  
7.  Вызывает **s'LBulkOperations***(Выписка,* SQL_UPDATE_BY_BOOKMARK).  
  
    > [!NOTE]  
    >  Если приложение установило атрибут SQL_ATTR_ROW_STATUS_PTR оператора, оно может проверить этот массив, чтобы увидеть результат операции.  
  
8.  Дополнительно вызывает **S'LBulkOperations***(StatementHandle,* SQL_FETCH_BY_BOOKMARK) для получения данных в буферы связанных приложений, чтобы убедиться, что обновление произошло.  
  
9. Если данные были обновлены, драйвер изменяет значение в массиве состояния строки для соответствующих строк, чтобы SQL_ROW_UPDATED.  
  
 Массовые обновления, выполняемые **S'LBulkOperations,** могут включать длинные данные с помощью вызовов на **S'LParamData** и **S'LPutData.** Для получения дополнительной информации, см. "Предоставление длинных данных для массовых вставок и обновлений" позже в этой функции ссылки.  
  
 Если закладки сохраняются в курсорах, приложение не нужно вызывать **S'LFetch** или **S'LFetchScroll** перед обновлением закладками. Он может использовать закладки, которые он хранил из предыдущего курсора. Если закладки не сохраняются в курсорах, приложение должно вызывать **S'LFetch** или **S'LFetchScroll,** чтобы получить закладки.  
  
 Поведение определяется драйвером, если **аргумент** *операции* SQL_UPDATE_BY_BOOKMARK называется на курсоре, содержащем дубликаты столбцов. Водитель может вернуть драйвер-определяемый S'LSTATE, обновить первую колонку, которая отображается в наборе результатов, или выполнить другое поведение, определяемое драйвером.  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>Выполнение Массовые fetches С помощью закладок  
 Для выполнения оптовых извлечений с помощью закладок с **S'LBulkOperations**, приложение выполняет следующие шаги в последовательности:  
  
1.  Устанавливает атрибут SQL_ATTR_USE_BOOKMARKS оператора на SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, который возвращает набор результатов.  
  
3.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE оператора на количество строк, которые он хочет получить.  
  
4.  Вызывает **S'LBindCol,** чтобы связать данные, которые он хочет получить. Данные привязаны к массиву с размером, равным значению SQL_ATTR_ROW_ARRAY_SIZE. Он также вызывает **S'LBindCol,** чтобы связать столбец 0 (столбец закладки).  
  
5.  Копирует закладки для строк, которые он заинтересован в получении в массив, связанный с столбцей 0. (Это предполагает, что приложение уже получило закладки отдельно.)  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут SQL_ATTR_ROW_STATUS_PTR оператора, должен быть равен SQL_ATTR_ROW_ARRAY_SIZE или SQL_ATTR_ROW_STATUS_PTR должен быть нулевой указателем.  
  
6.  Вызывает **s'LBulkOperations***(Заявление,* SQL_FETCH_BY_BOOKMARK).  
  
7.  Если приложение установило атрибут SQL_ATTR_ROW_STATUS_PTR оператора, оно может проверить этот массив, чтобы увидеть результат операции.  
  
 Если закладки сохраняются в курсорах, приложение не нужно вызывать **S'LFetch** или **S'LFetchScroll,** прежде чем получать закладки. Он может использовать закладки, которые он хранил из предыдущего курсора. Если закладки не сохраняются в курсорах, приложение должно один раз позвонить в **S'LFetch(S'LFetchScroll)** или **S'LFetchScroll,** чтобы получить закладки.  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>Выполнение массовых удаляет с помощью закладок  
 Для выполнения оптовых удаляет с помощью закладок с **S'LBulkOperations**, приложение выполняет следующие шаги в последовательности:  
  
1.  Устанавливает атрибут SQL_ATTR_USE_BOOKMARKS оператора на SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, который возвращает набор результатов.  
  
3.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE оператора на количество строк, которые он хочет удалить.  
  
4.  Вызывает **s'LBindCol,** чтобы связать столбец 0 (столбец закладки).  
  
5.  Копирует закладки для строк, которые он заинтересован в удалении в массив, связанный с столбцей 0.  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут SQL_ATTR_ROW_STATUS_PTR оператора, должен быть равен SQL_ATTR_ROW_ARRAY_SIZE или SQL_ATTR_ROW_STATUS_PTR должен быть нулевой указателем.  
  
6.  Вызывает **S'LBulkOperations***(Выписка,* SQL_DELETE_BY_BOOKMARK).  
  
7.  Если приложение установило атрибут SQL_ATTR_ROW_STATUS_PTR оператора, оно может проверить этот массив, чтобы увидеть результат операции.  
  
 Если закладки сохраняются в курсорах, приложение не должно вызывать **S'LFetch** или **S'LFetchScroll** перед удалять закладки. Он может использовать закладки, которые он хранил из предыдущего курсора. Если закладки не сохраняются в курсорах, приложение должно один раз позвонить в **S'LFetch(S'LFetchScroll)** или **S'LFetchScroll,** чтобы получить закладки.  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>Предоставление длинных данных для массовых вставок и обновлений  
 Длинные данные могут быть предоставлены для оптовых вставок и обновлений, выполняемых вызовами на **S'LBulkOperations.** Для вставки или обновления длинных данных приложение выполняет следующие шаги в дополнение к шагам, описанным в разделах "Выполнение массовых вставок" и "Выполнение массовых обновлений с использованием закладок", описанных ранее в этой теме.  
  
1.  При связывании данных с помощью **S'LBindCol**приложение помещает определенное значение приложения, например номер столбца, в буфер * \*TargetValuePtr* для столбцов данных. Значение может быть использовано позже для определения столбца.  
  
     Приложение помещает результат макроса SQL_LEN_DATA_AT_EXEC *(длина)* в * \*StrLen_or_IndPtr* буфер. Если тип данных в столбце является SQL_LONGVARBINARY, SQL_LONGVARCHAR или длинным типом исходных данных, а драйвер возвращает "Y" для SQL_NEED_LONG_DATA_LEN типа информации в **S'LGetInfo,** *длина* — это количество байтов данных, которые будут отправлены для параметра; в противном случае, она должна быть ненегативной стоимости и игнорируется.  
  
2.  При вызове **S'LBulkOperations,** если есть столбцы данных по исполнению, функция возвращается SQL_NEED_DATA и переходит к шагу 3, который следует за ним. (Если нет столбцов данных по исполнению, процесс завершен.)  
  
3.  Приложение вызывает **S'LParamData** для получения адреса буфера * \*TargetValuePtr* для обработки первого столбца данных. **S'LParamData** возвращает SQL_NEED_DATA. Приложение извлекает значение, определяемое приложением, из буфера * \*TargetValuePtr.*  
  
    > [!NOTE]  
    >  Несмотря на то, что параметры данных по исполнению напоминают столбцы данных по исполнению, значение, возвращенное **S'LParamData,** отличается для каждого из них.  
  
     Столбцы данных по исполнению — это столбцы в строке, для которых данные будут отправлены с **помощью S'LPutData** при обновлении или вставке строки с **помощью S'LBulkOperations.** Они связаны с **S'LBindCol**. Значение, возвращенное **S'LParamData,** является адресом строки в буфере*TargetValuePtr,* который обрабатывается.  
  
4.  Приложение вызывает **S'LPutData** один или несколько раз, чтобы отправить данные для столбца. Требуется несколько вызовов, если все значение данных не может быть возвращено в * \*буфере TargetValuePtr,* указанном в **S'LPutData;** несколько вызовов на **S'LPutData** для одного и того же столбца разрешены только при отправке данных о символе C в столбец с типом данных, двоичных или данных, имеющих конкретные источники данных, или при отправке двоичных данных C в столбец с типом данных, характерных для символов, двоичных или исходных данных.  
  
5.  Приложение снова вызывает **S'LParamData,** чтобы сигнализировать о том, что все данные были отправлены в столбец.  
  
    -   При наличии большего количества столбцов данных по исполнению, **s'LParamData** возвращает SQL_NEED_DATA и адрес буфера *TargetValuePtr* для следующей колонки data-at-execution, которая будет обработана. Приложение повторяет шаги 4 и 5.  
  
    -   Если больше нет столбцов данных по исполнению, процесс завершен. Если выписка была выполнена успешно, **S'LParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO; если выполнение не удалось, он возвращает SQL_ERROR. На этом **этапе, S'LParamData** может вернуть любой S'Lstate, которые могут быть возвращены **s'LBulkOperations**.  
  
 Если операция отменена или произошла ошибка в **S'LParamData** или **SLPutData** после возвращения SQL_NEED_DATA **sLBulkOperations** и до того, как данные будут отправлены для всех столбцов данных по исполнению, приложение может **SQLPutData** вызвать только **S'LCancel**, **S'LGetDiagField**, **S'LGetDiagRec**, **S'L.LGet.** **SQLParamData** Если он вызывает любую другую функцию для оператора или соединения, связанного с выпиской, функция возвращается SQL_ERROR и S'Lstate HY010 (ошибка последовательности функций).  
  
 Если приложение вызывает **S'LCancel,** в то время как водителю по-прежнему нужны данные для столбцов данных, драйвер отменяет операцию. Затем приложение может снова вызывать **S'LBulkOperations;** отмена не влияет на состояние курсора или текущее положение курсора.  
  
## <a name="row-status-array"></a>Массив статусов строк  
 Массив состояния строк содержит значения статуса для каждой строки данных в строке после вызова в **S'LBulkOperations.** Драйвер устанавливает значения статуса в этом массиве после звонка в **S'LFetch,** **S'LFetchScroll,** **S'LSetPos**или **S'LBulkOperations.** Этот массив изначально заполняется вызовом в **S'LBulkOperations,** если до **sLBulkOperations**не был вызван **s'LFetch.** **SQLFetchScroll** На этот массив указывает атрибут SQL_ATTR_ROW_STATUS_PTR оператора. Количество элементов в массивах состояния строк должно равняться числу строк в строке (как это определено атрибутом SQL_ATTR_ROW_ARRAY_SIZE оператора). Для получения информации об этом массиве статуса строки, [см.](../../../odbc/reference/syntax/sqlfetch-function.md)  
  
## <a name="code-example"></a>Пример кода  
 Следующий пример получает 10 строк данных одновременно из таблицы Заказчиков. Затем он подсказывает пользователю для действия. Чтобы уменьшить сетевой трафик, пример буфера обновляется, удаляет и вставляет локально в связанных массивах, но при смещениях мимо данных строки. Когда пользователь выбирает для отправки обновлений, удаляет и вставляет в источник данных, код устанавливает обязательное смещение соответствующим образом и вызывает **S'LBulkOperations.** Для простоты пользователь не может буферизировать более 10 обновлений, удалений или вставок.  
  
```cpp  
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
|Привязка буфера к столбцовику в наборе результатов|[SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки оператора|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Получение блока данных или прокрутка набора результатов|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Получение одного поля дескриптора|[Функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Получение нескольких полей дескриптора|[Функция SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Установка одного поля дескриптора|[Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Установка нескольких полей дескриптора|[Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Позиционирование курсора, обновление данных в строке или обновление или удаляние данных в строке|[Функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Установка атрибута оператора|[Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
