---
title: Функция SQLBulkOperations | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301334"
---
# <a name="sqlbulkoperations-function"></a>Функция SQLBulkOperations
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 3,0: ODBC  
  
 **Сводка**  
 **SQLBulkOperations** выполняет операции с массовыми вставками и выполнением операций с закладками, включая обновление, удаление и выборку по закладке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLBulkOperations(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Operation);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции.  
  
 *Операция*  
 Входной Выполняемая операция:  
  
 SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK  
  
 Дополнительные сведения см. в разделе "Комментарии".  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLBulkOperations** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLBulkOperations** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
 Для всех этих SQLSTATE, которые могут возвращать SQL_SUCCESS_WITH_INFO или SQL_ERROR (за исключением 01XXX SQLSTATE), SQL_SUCCESS_WITH_INFO возвращается в случае возникновения ошибки в одной или нескольких строках операции многострочные, а SQL_ERROR возвращается в случае возникновения ошибки в операции с одной строкой.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Усечение строковых данных справа|Аргумент *операции* был SQL_FETCH_BY_BOOKMARK, а строковые или двоичные данные, возвращенные для столбца или столбцов с типом данных SQL_C_CHAR или SQL_C_BINARY привели к усечению непустого символа или двоичных данных, отличных от NULL.|  
|01S01|Ошибка в строке|Аргумент *операции* был SQL_ADD, и произошла ошибка в одной или нескольких строках при выполнении операции, но по крайней мере одна строка была успешно добавлена. (Функция возвращает SQL_SUCCESS_WITH_INFO.)<br /><br /> (Эта ошибка возникает только в том случае, если приложение работает с ODBC 2. драйвер *x* .)|  
|01S07|Усечение дробной части|Аргумент *операции* был SQL_FETCH_BY_BOOKMARK, тип данных буфера приложения не SQL_C_CHAR или SQL_C_BINARY, а данные, возвращенные в буферы приложений для одного или нескольких столбцов, были усечены. (Для числовых типов данных C дробная часть числа была усечена. Для типов данных time, timestamp и Interval C, которые содержат компонент времени, дробная часть времени была усечена.)<br /><br /> (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|07006|Нарушение атрибута ограниченного типа данных|Аргумент *операции* был SQL_FETCH_BY_BOOKMARK, и значение данных столбца в результирующем наборе не может быть преобразовано в тип данных, указанный в аргументе *TargetType* в вызове **SQLBindCol**.<br /><br /> Аргумент *операции* был SQL_UPDATE_BY_BOOKMARK или SQL_ADD, и значение данных в буферах приложения не может быть преобразовано в тип данных столбца результирующего набора.|  
|07009|Недопустимый индекс дескриптора|*Операция* аргумента была SQL_ADD, а столбец был привязан с номером столбца, превышающим число столбцов в результирующем наборе.|  
|21S02|Степень производной таблицы не соответствует списку столбцов|*Операция* аргумента была SQL_UPDATE_BY_BOOKMARKа; не удалось обновить ни один столбец, так как все столбцы были либо свободными, либо только для чтения, либо значение в буфере длины или индикатора SQL_COLUMN_IGNORE.|  
|22001|Усечение строковых данных справа|Присвоение символьного или двоичного значения столбцу в результирующем наборе привело к усечению непустых (для символов) или не NULL (для двоичных) символов или байтов.|  
|22003|Числовое значение вне допустимого диапазона|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, а присваивание числового значения столбцу в результирующем наборе привело к усечению всего (в отличие от дробной части) числа.<br /><br /> *Операция* аргумента была SQL_FETCH_BY_BOOKMARK, и возврат числового значения для одного или нескольких связанных столбцов привело бы к утрате значащих цифр.|  
|22007|Недопустимый формат даты и времени|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, а присваивание значения даты или метки времени столбцу в результирующем наборе привело к тому, что поле год, месяц или день выходит за пределы диапазона.<br /><br /> *Операция* аргумента была SQL_FETCH_BY_BOOKMARK, и возврат значения даты или метки времени для одного или нескольких связанных столбцов привело к тому, что поле год, месяц или день выходит за пределы диапазона.|  
|22008|Переполнение поля даты и времени|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, а производительность арифметических операций с типом DateTime для данных, отправляемых в столбец результирующего набора, привела к появлению поля DateTime (год, месяц, день, час, минута или второе поле) результата, который выходит за пределы допустимого диапазона значений для поля или является недопустимым в зависимости от естественных правил григорианского календаря для DateTimes.<br /><br /> Аргумент *операции* был SQL_FETCH_BY_BOOKMARK, и производительность арифметических операций над данными, получаемых из результирующего набора, привела к полю DateTime (год, месяц, день, час, минута или второе поле) результата, который выходит за пределы допустимого диапазона значений для поля или является недопустимым в зависимости от естественных правил григорианского календаря для значений DateTime.|  
|22015|Переполнение поля интервала|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, а назначение точного числового или временного типа C для типа данных SQL Interval привело к утрате значащих цифр.<br /><br /> Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK; При назначении типа SQL Interval не было представления значения типа C в поле Interval SQL Type.<br /><br /> Аргумент *операции* был SQL_FETCH_BY_BOOKMARK, и присваивание от точного числового или временного типа SQL к типу Interval C привело к утере значащих цифр в начальном поле.<br /><br /> Аргумент *операции* был SQL_FETCH_BY_BOOKMARK; При назначении в тип C Interval не было представления значения типа SQL в типе Interval C.|  
|22018|Недопустимое символьное значение для спецификации приведения|Аргумент *операции* был SQL_FETCH_BY_BOOKMARK; Тип C был точным или приблизительным числовым, типом данных DateTime или интервалом. тип SQL столбца имеет символьный тип данных; и значение в столбце не было допустимым литералом привязанного типа C.<br /><br /> *Операция* аргумента была SQL_ADDа или SQL_UPDATE_BY_BOOKMARKа; тип SQL был точным или приблизительным числовым, типом данных DateTime или значением интервала. Тип C — SQL_C_CHAR; и значение в столбце не было допустимым литералом привязанного типа SQL.|  
|23000|Нарушение ограничения целостности|Аргумент *операции* был SQL_ADD, SQL_DELETE_BY_BOOKMARK или SQL_UPDATE_BY_BOOKMARK, и нарушено ограничение целостности.<br /><br /> Аргумент *операции* был SQL_ADD, а столбец, который не был привязан, ОПРЕДЕЛЕН как NOT NULL и не имеет значения по умолчанию.<br /><br /> Аргумент *операции* был SQL_ADD, длина, указанная в связанном *StrLen_or_IndPtr* буфере, была SQL_COLUMN_IGNORE, а столбец не имеет значения по умолчанию.|  
|24 000|Недопустимое состояние курсора|*Статеменсандле* был в выполненном состоянии, но с *статеменсандле*не связан ни один результирующий набор.|  
|40001|Сбой сериализации|Выполнен откат транзакции из-за взаимоблокировки ресурсов с другой транзакцией.|  
|40003|Неизвестное завершение инструкции|Не удалось выполнить связанное соединение во время выполнения этой функции, и состояние транзакции не может быть определено.|  
|42000|Синтаксическая ошибка или нарушение прав доступа|Драйверу не удалось заблокировать строку по мере необходимости для выполнения операции, запрошенной в аргументе *операции* .|  
|44000|Нарушение параметра WITH CHECK OPTION|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK, а Вставка или обновление выполнялись в просматриваемой таблице (или таблице, производной от просматриваемой таблицы), которая была создана с помощью **параметра WITH CHECK**, таким образом, что одна или несколько строк, затронутых вставкой или обновлением, больше не будут присутствовать в просматриваемой таблице.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка включена для *статеменсандле*. Функция была вызвана, и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** для *статеменсандле*. Затем функция была вызвана в *статеменсандле*.<br /><br /> Функция была вызвана и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** в *статеменсандле* из другого потока многопоточного приложения.|  
|HY010|Ошибка последовательности функций|(DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове функции **SQLBulkOperations** .<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.<br /><br /> (DM) указанный *статеменсандле* не находится в выполненном состоянии. Функция была вызвана без предварительного вызова **SQLExecDirect**, **SQLExecute**или функции каталога.<br /><br /> (DM) вызывается асинхронно исполняемая функция (не эта одна) для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLSetPos** были вызваны для *статеменсандле* и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.<br /><br /> (DM) драйвер был ODBC 2. *x* Driver и **SQLBulkOperations** был вызван для *статеменсандле* перед вызовом **SQLFetchScroll** или **SQLFetch** .<br /><br /> (DM) **SQLBulkOperations** был вызван после вызова **SQLExtendedFetch** в *статеменсандле*.|  
|HY011|Задать атрибут сейчас невозможно|(DM) драйвер был ODBC 2. драйвер *x* , а атрибут оператора SQL_ATTR_ROW_STATUS_PTR был задан между вызовами **SQLFetch** или **SQLFetchScroll** и **SQLBulkOperations**.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|Аргумент *операции* был SQL_ADD или SQL_UPDATE_BY_BOOKMARK; значение данных не является пустым указателем; тип данных C — SQL_C_BINARY или SQL_C_CHAR; значение длины столбца было меньше 0, но не равно SQL_DATA_AT_EXEC, SQL_COLUMN_IGNORE, SQL_NTS или SQL_NULL_DATA или меньше или равно SQL_LEN_DATA_AT_EXEC_OFFSET.<br /><br /> Значение в буфере длины или индикатора было SQL_DATA_AT_EXEC; тип SQL был либо SQL_LONGVARCHAR, SQL_LONGVARBINARY, либо типом данных типа Long, относящимся к источнику данных. а тип сведений SQL_NEED_LONG_DATA_LEN в **SQLGetInfo** — «Y».<br /><br /> Аргумент *операции* был SQL_ADD, атрибуту инструкции SQL_ATTR_USE_BOOKMARK было присвоено значение SQL_UB_VARIABLE, а столбец 0 был привязан к буферу, длина которого не равна максимальной длине закладки для этого результирующего набора. (Эта длина доступна в поле SQL_DESC_OCTET_LENGTH IRD и может быть получено путем вызова **SQLDescribeCol**, **SQLColAttribute**или **SQLGetDescField**.)|  
|HY092|Недопустимый идентификатор атрибута|(DM) значение, указанное для аргумента *операции* , недопустимо.<br /><br /> Аргумент *операции* был SQL_ADD, SQL_UPDATE_BY_BOOKMARK или SQL_DELETE_BY_BOOKMARK, а атрибуту инструкции SQL_ATTR_CONCURRENCY было задано значение SQL_CONCUR_READ_ONLY.<br /><br /> Аргумент *операции* был SQL_DELETE_BY_BOOKMARK, SQL_FETCH_BY_BOOKMARK или SQL_UPDATE_BY_BOOKMARK, а столбец закладки не был привязан, либо атрибуту инструкции SQL_ATTR_USE_BOOKMARKS было присвоено значение SQL_UB_OFF.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Необязательная функция не реализована|Драйвер или источник данных не поддерживает операцию, запрошенную в аргументе *операции* .|  
|HYT00|Время ожидания истекло|Время ожидания запроса истекло до того, как источник данных вернул результирующий набор. Период ожидания задается через **SQLSetStmtAttr** с аргументом *атрибута* SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
|IM017|Опрос отключен в режиме асинхронного уведомления|При использовании модели уведомления опрос отключен.|  
|IM018|**Склкомплетеасинк** не был вызван для завершения предыдущей асинхронной операции с этим обработчиком.|Если предыдущий вызов функции в обработчике возвращает SQL_STILL_EXECUTING и если включен режим уведомления, то для обработки после обработки и завершения операции необходимо вызвать **склкомплетеасинк** .|  
  
## <a name="comments"></a>Комментарии  
  
> [!CAUTION]  
>  Сведения о том, какие состояния инструкций **SQLBulkOperations** могут вызываться в и что они должны сделать для СОВМЕСТИМОСТИ с ODBC 2. приложения *x* см. в разделе " [блочные курсоры", "прокручиваемые курсоры" и "Обратная совместимость](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) " в приложении G: рекомендации по драйверу для обеспечения обратной совместимости.  
  
 Приложение использует **SQLBulkOperations** для выполнения следующих операций с базовой таблицей или представлением, которые соответствуют текущему запросу:  
  
-   Добавление новых строк.  
  
-   Обновление набора строк, где каждая строка идентифицируется закладкой.  
  
-   Удаляет набор строк, в котором каждая строка идентифицируется закладкой.  
  
-   Получение набора строк, где каждая строка идентифицируется закладкой.  
  
 После вызова **SQLBulkOperations**позицию блочного курсора не определена. Чтобы задать позицию курсора, приложение должно вызвать **SQLFetchScroll** . Приложение должно вызывать **SQLFetchScroll** только с аргументом *фетчориентатион* SQL_FETCH_FIRST, SQL_FETCH_LAST, SQL_FETCH_ABSOLUTE или SQL_FETCH_BOOKMARK. Если приложение вызывает **SQLFetch** или **SQLFetchScroll** с аргументом *фетчориентатион* SQL_FETCH_PRIOR, SQL_FETCH_NEXT или SQL_FETCH_RELATIVE, то позиции курсора не определяются.  
  
 Столбец может быть пропущен в ходе выполнения операций, выполняемых при вызове **SQLBulkOperations** путем установки буфера длины столбца или индикатора, указанного в вызове **SQLBindCol**, для SQL_COLUMN_IGNORE.  
  
 Приложению не нужно задавать атрибут SQL_ATTR_ROW_OPERATION_PTR инструкции при вызове **SQLBulkOperations** , так как строки не могут быть пропущены при выполнении операций с этой функцией.  
  
 Буфер, на который указывает атрибут инструкции SQL_ATTR_ROWS_FETCHED_PTR, содержит количество строк, затронутых вызовом **SQLBulkOperations**.  
  
 Если аргумент *операции* имеет SQL_ADD или SQL_UPDATE_BY_BOOKMARK и список SELECT-List спецификации запроса, связанного с курсором, содержит несколько ссылок на один и тот же столбец, он определяется драйвером независимо от того, формируется ли ошибка, или драйвер игнорирует дублирующиеся ссылки и выполняет запрошенные операции.  
  
 Дополнительные сведения об использовании **SQLBulkOperations**см. в разделе [Обновление данных с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).  
  
## <a name="performing-bulk-inserts"></a>Выполнение операций с массовыми вставками  
 Чтобы вставить данные с помощью **SQLBulkOperations**, приложение выполняет следующую последовательность действий:  
  
1.  Выполняет запрос, возвращающий результирующий набор.  
  
2.  Устанавливает атрибут инструкции SQL_ATTR_ROW_ARRAY_SIZE в число строк, которое необходимо вставить.  
  
3.  Вызывает **SQLBindCol** для привязки данных, которые необходимо вставить. Данные привязаны к массиву с размером, равным значению SQL_ATTR_ROW_ARRAY_SIZE.  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут инструкции SQL_ATTR_ROW_STATUS_PTR, должен быть равен SQL_ATTR_ROW_ARRAY_SIZE или SQL_ATTR_ROW_STATUS_PTR должен быть пустым указателем.  
  
4.  Вызывает **SQLBulkOperations**(*статеменсандле,* SQL_ADD) для выполнения вставки.  
  
5.  Если приложение установило атрибут инструкции SQL_ATTR_ROW_STATUS_PTR, он может проверить этот массив, чтобы увидеть результат операции.  
  
 Если приложение привязывает столбец 0 перед вызовом **SQLBulkOperations** с аргументом *операции* SQL_ADD, драйвер обновляет привязанные буферы 0 с помощью значений закладок для вновь вставленной строки. Чтобы это происходило, приложение должно задать атрибуту инструкции SQL_ATTR_USE_BOOKMARKS значение SQL_UB_VARIABLE перед выполнением инструкции. (Это не работает с ODBC 2. драйвер *x* .)  
  
 Данные типа long можно добавлять в части с помощью SQLBulkOperations, используя вызовы метод SQLParamData и SQLPutData. Дополнительные сведения см. в подразделе "предоставление длинных данных для выполнения операций вставки и обновления" Далее в этой ссылке на эту функцию.  
  
 Не требуется, чтобы приложение вызывало **SQLFetch** или **SQLFetchScroll** перед вызовом **SQLBulkOperations** (за исключением случаев перехода к ODBC 2).* драйвер x* ; см. раздел [обратная совместимость и соответствие стандартам](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)).  
  
 Поведение определяется драйвером, если **SQLBulkOperations**с аргументом *операции* SQL_ADD, вызывается для курсора, который содержит дублирующиеся столбцы. Драйвер может возвращать определенное драйвером значение SQLSTATE, добавлять данные в первый столбец, который появляется в результирующем наборе, или выполнять другие действия, определяемые драйвером.  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>Выполнение массовых обновлений с помощью закладок  
 Для выполнения пакетного обновления с помощью закладок с **SQLBulkOperations**приложение последовательно выполняет следующие действия.  
  
1.  Задает для атрибута SQL_ATTR_USE_BOOKMARKS инструкции значение SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, возвращающий результирующий набор.  
  
3.  Устанавливает атрибут инструкции SQL_ATTR_ROW_ARRAY_SIZE в число строк, которое требуется обновить.  
  
4.  Вызывает **SQLBindCol** для привязки данных, которые требуется обновить. Данные привязаны к массиву с размером, равным значению SQL_ATTR_ROW_ARRAY_SIZE. Он также вызывает **SQLBindCol** для привязки столбца 0 (столбец закладки).  
  
5.  Копирует закладки для строк, которые требуется обновить, в массив, привязанный к столбцу 0.  
  
6.  Обновляет данные в связанных буферах.  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут оператора SQL_ATTR_ROW_STATUS_PTR, должен быть равен SQL_ATTR_ROW_ARRAY_SIZE или SQL_ATTR_ROW_STATUS_PTR должен быть пустым указателем.  
  
7.  Вызывает **SQLBulkOperations**(*статеменсандле,* SQL_UPDATE_BY_BOOKMARK).  
  
    > [!NOTE]  
    >  Если приложение установило атрибут инструкции SQL_ATTR_ROW_STATUS_PTR, он может проверить этот массив, чтобы увидеть результат операции.  
  
8.  При необходимости вызывает **SQLBulkOperations**(*статеменсандле*, SQL_FETCH_BY_BOOKMARK) для выборки данных в привязанных буферах приложения для проверки того, что произошло обновление.  
  
9. Если данные были обновлены, драйвер изменяет значение в массиве состояния строк для соответствующих строк на SQL_ROW_UPDATED.  
  
 При выполнении операций с массовым обновлением, выполненных **SQLBulkOperations** , можно использовать длинные данные с помощью вызовов **метод SQLParamData** и **SQLPutData**. Дополнительные сведения см. в подразделе "предоставление длинных данных для выполнения операций вставки и обновления" Далее в этой ссылке на эту функцию.  
  
 Если закладки сохраняются между курсорами, приложению не нужно вызывать **SQLFetch** или **SQLFetchScroll** перед обновлением с помощью закладок. Он может использовать закладки, сохраненные в предыдущем курсоре. Если закладки не сохраняются между курсорами, приложение должно вызвать **SQLFetch** или **SQLFetchScroll** для получения закладок.  
  
 Поведение определяется драйвером, если **SQLBulkOperations**с аргументом *операции* SQL_UPDATE_BY_BOOKMARK, вызывается для курсора, который содержит дублирующиеся столбцы. Драйвер может возвращать определенное драйвером значение SQLSTATE, обновлять первый столбец, который отображается в результирующем наборе, или выполнять другие действия, определенные драйвером.  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>Выполнение групповой выборки с помощью закладок  
 Для выполнения групповой выборки с помощью закладок с **SQLBulkOperations**приложение последовательно выполняет следующие действия.  
  
1.  Задает для атрибута SQL_ATTR_USE_BOOKMARKS инструкции значение SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, возвращающий результирующий набор.  
  
3.  Устанавливает атрибут инструкции SQL_ATTR_ROW_ARRAY_SIZE в число строк, которое требуется получить.  
  
4.  Вызывает **SQLBindCol** для привязки данных, которые требуется получить. Данные привязаны к массиву с размером, равным значению SQL_ATTR_ROW_ARRAY_SIZE. Он также вызывает **SQLBindCol** для привязки столбца 0 (столбец закладки).  
  
5.  Копирует закладки для строк, которые заинтересовались при выборке в массив, привязанный к столбцу 0. (Предполагается, что приложение уже получило закладки отдельно.)  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут оператора SQL_ATTR_ROW_STATUS_PTR, должен быть равен SQL_ATTR_ROW_ARRAY_SIZE или SQL_ATTR_ROW_STATUS_PTR должен быть пустым указателем.  
  
6.  Вызывает **SQLBulkOperations**(*статеменсандле,* SQL_FETCH_BY_BOOKMARK).  
  
7.  Если приложение установило атрибут инструкции SQL_ATTR_ROW_STATUS_PTR, он может проверить этот массив, чтобы увидеть результат операции.  
  
 Если закладки сохраняются между курсорами, приложению не нужно вызывать **SQLFetch** или **SQLFetchScroll** перед получением по закладкам. Он может использовать закладки, сохраненные в предыдущем курсоре. Если закладки не сохраняются между курсорами, приложение должно вызвать **SQLFetch** или **SQLFetchScroll** один раз для получения закладок.  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>Выполнение операций удаления с помощью закладок  
 Чтобы выполнить групповое удаление с помощью закладок с **SQLBulkOperations**, приложение последовательно выполняет следующие действия.  
  
1.  Задает для атрибута SQL_ATTR_USE_BOOKMARKS инструкции значение SQL_UB_VARIABLE.  
  
2.  Выполняет запрос, возвращающий результирующий набор.  
  
3.  Устанавливает атрибут инструкции SQL_ATTR_ROW_ARRAY_SIZE в число строк, которое требуется удалить.  
  
4.  Вызывает **SQLBindCol** , чтобы привязать столбец 0 (столбец закладки).  
  
5.  Копирует закладки для строк, которые требуется удалить, в массив, привязанный к столбцу 0.  
  
    > [!NOTE]  
    >  Размер массива, на который указывает атрибут оператора SQL_ATTR_ROW_STATUS_PTR, должен быть равен SQL_ATTR_ROW_ARRAY_SIZE или SQL_ATTR_ROW_STATUS_PTR должен быть пустым указателем.  
  
6.  Вызывает **SQLBulkOperations**(*статеменсандле,* SQL_DELETE_BY_BOOKMARK).  
  
7.  Если приложение установило атрибут инструкции SQL_ATTR_ROW_STATUS_PTR, он может проверить этот массив, чтобы увидеть результат операции.  
  
 Если закладки сохраняются между курсорами, приложению не нужно вызывать **SQLFetch** или **SQLFetchScroll** перед удалением с помощью закладок. Он может использовать закладки, сохраненные в предыдущем курсоре. Если закладки не сохраняются между курсорами, приложение должно вызвать **SQLFetch** или **SQLFetchScroll** один раз для получения закладок.  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>Предоставление длинных данных для выполнения операций вставки и обновления  
 Для выполнения операций с массовыми вставками и обновлениями, выполняемыми вызовами **SQLBulkOperations**, можно указать данные большого объема. Чтобы вставить или обновить данные большого объема, приложение выполняет следующие действия в дополнение к действиям, описанным в разделах «выполнение операций вставки и выполнение массовых обновлений с помощью закладок» ранее в этом разделе.  
  
1.  При привязке данных с помощью **SQLBindCol**приложение помещает определяемое приложением значение, например номер столбца, в буфер * \*таржетвалуептр* для столбцов с данными в процессе выполнения. Значение можно использовать позже для задания столбца.  
  
     Приложение помещает результат макроса SQL_LEN_DATA_AT_EXEC (*length*) в буфер * \*StrLen_or_IndPtr* . Если тип данных SQL столбца имеет значение SQL_LONGVARBINARY, SQL_LONGVARCHAR или тип данных Long, зависящий от источника данных, а драйвер возвращает значение "Y" для SQL_NEED_LONG_DATA_LENого типа данных в **SQLGetInfo**, то *Длина* — это число байтов данных, отправляемых для параметра. в противном случае он должен быть неотрицательным значением и игнорироваться.  
  
2.  При вызове **SQLBulkOperations** , если имеются столбцы данных на этапе выполнения, функция возвращает SQL_NEED_DATA и переходит к шагу 3, который приведен ниже. (Если нет столбцов данных на этапе выполнения, процесс завершен.)  
  
3.  Приложение вызывает **метод SQLParamData** , чтобы получить адрес буфера * \*таржетвалуептр* для первого обрабатываемого столбца данных. **Метод SQLParamData** возвращает SQL_NEED_DATA. Приложение получает значение, определяемое приложением, из буфера * \*таржетвалуептр* .  
  
    > [!NOTE]  
    >  Несмотря на то, что параметры данных во время выполнения похожи на столбцы данных в ходе выполнения, значение, возвращаемое функцией **метод SQLParamData** , отличается для каждого из них.  
  
     Столбцы данных в ходе выполнения — это столбцы в наборе строк, для которых данные будут отправляться с помощью **SQLPutData** при обновлении или вставке строки с помощью **SQLBulkOperations**. Они связаны с **SQLBindCol**. Значение, возвращаемое функцией **метод SQLParamData** , является адресом строки в буфере **таржетвалуептр* , который обрабатывается.  
  
4.  Приложение вызывает **SQLPutData** один или несколько раз для отправки данных для столбца. Если все значения данных не могут быть возвращены в буфере * \*таржетвалуептр* , указанном в **SQLPutData**, требуется более одного вызова. несколько вызовов **SQLPutData** для одного и того же столбца разрешены только при отправке символьных данных c в столбец с типом данных символьного, двоичного или конкретного источника данных, а также при отправке двоичных данных c в столбец с символьным, двоичным или определяемым источником данных типом данных.  
  
5.  Приложение вызывает **метод SQLParamData** еще раз, чтобы сообщить о том, что для столбца были отправлены все данные.  
  
    -   Если имеются дополнительные столбцы данных, то **метод SQLParamData** возвращает SQL_NEED_DATA и адрес буфера *таржетвалуептр* для следующего обрабатываемого столбца данных (в ходе выполнения). Приложение повторяет шаги 4 и 5.  
  
    -   Если больше нет столбцов данных в процессе выполнения, процесс завершится. Если инструкция была выполнена успешно, **метод SQLParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO; в случае сбоя выполнения возвращается SQL_ERROR. На этом этапе **метод SQLParamData** может возвращать любой SQLSTATE, который может быть возвращен **SQLBulkOperations**.  
  
 Если операция отменяется или возникает ошибка в **метод SQLParamData** или **SQLPutData** после того, как **SQLBulkOperations** возвращает SQL_NEED_DATA и перед отправкой данных для всех столбцов данных в ходе выполнения, приложение может вызвать только **SQLCancel**, **SQLGetDiagField**, **SQLGetDiagRec**, **SQLGetFunctions**, **метод SQLParamData**или **SQLPutData** для инструкции или соединения, связанного с инструкцией. Если вызывается любая другая функция для инструкции или соединение, связанное с инструкцией, функция возвращает SQL_ERROR и SQLSTATE HY010 (ошибка последовательности функций).  
  
 Если приложение вызывает **SQLCancel** , а драйверу по-прежнему требуются данные для столбцов данных в процессе выполнения, драйвер отменяет операцию. Затем приложение может снова вызвать **SQLBulkOperations** ; Отмена не влияет на состояние курсора или текущую позицию курсора.  
  
## <a name="row-status-array"></a>Массив статусов строк  
 Массив состояния строк содержит значения состояния для каждой строки данных в наборе строк после вызова **SQLBulkOperations**. Драйвер задает значения состояния в этом массиве после вызова **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**или **SQLBulkOperations**. Этот массив первоначально заполняется вызовом **SQLBulkOperations** , если **SQLFetch** или **SQLFetchScroll** не вызывался до **SQLBulkOperations**. На этот массив указывает атрибут инструкции SQL_ATTR_ROW_STATUS_PTR. Число элементов в массивах состояния строк должно равняться числу строк в наборе строк (как определено атрибутом оператора SQL_ATTR_ROW_ARRAY_SIZE). Сведения о массиве состояния строк см. в разделе [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере из таблицы Customers выбиралось 10 строк данных за раз. Затем пользователю предлагается выполнить действие. Чтобы сократить сетевой трафик, в примере буфера обновляются, удаляются и вставляются локально в привязанных массивах, но по смещению после данных набора строк. Когда пользователь выбирает отправку обновлений, удалений и вставок в источник данных, код устанавливает смещение привязки соответствующим образом и вызывает **SQLBulkOperations**. Для простоты пользователь не может буферизовать более 10 обновлений, удалений или вставок.  
  
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
|Привязка буфера к столбцу в результирующем наборе|[SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выборка блока данных или прокрутка результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Получение одного поля дескриптора|[Функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Получение нескольких полей дескриптора|[Функция SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Задание одного поля дескриптора|[Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Установка нескольких полей дескриптора|[Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|Размещение курсора, обновление данных в наборе строк, обновление или удаление данных в наборе строк|[Функция SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|Задание атрибута инструкции|[Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
