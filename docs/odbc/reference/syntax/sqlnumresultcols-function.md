---
title: Функция S'LNumResultCols Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLNumResultCols
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLNumResultCols
helpviewer_keywords:
- SQLNumResultCols function [ODBC]
ms.assetid: d863179f-12a9-4b55-ac6b-7d84202d3da3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07274a8664a6909af0a4ae8d9b165fdd0676d7f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306935"
---
# <a name="sqlnumresultcols-function"></a>SQLNumResultCols, функция
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 1.0: ISO 92  
  
 **Сводка**  
 **S'LNumResultCols** возвращает количество столбцов в наборе результатов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLNumResultCols(  
     SQLHSTMT        StatementHandle,  
     SQLSMALLINT *   ColumnCountPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *Обработка заявления*  
 (Вход) Ручка оператора.  
  
 *КолонкаCountPtr*  
 (Выход) Указатель на буфер, в котором можно вернуть количество столбцов в наборе результатов. Этот подсчет не включает в себя связанную колонку закладок.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **s'LNumResultCols** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону S'LGetDiagRec** с *помощью HandleType* of SQL_HANDLE_STMT и *ручки* *statementHandle.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LNumResultCols,** и разъясняются каждое из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08S01|Сбой связи|Связь между драйвером и источником данных, к которому был подключен драйвер, не сработала до завершения обработки функции.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхлик** был вызван на *StatementHandle;* функция была вызвана снова на *StatementHandle*.<br /><br /> Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхливнейра** был вызван на *StatementHandle* из другого потока в многопоточном приложении.|  
|HY010|Ошибка последовательности функций|(DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *StatementHandle.* Эта асинхронная функция по-прежнему исполнялась при вызове функции **S'LNumResultsCols.**<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для *statementHandle* и вернулся SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.<br /><br /> (DM) Функция была вызвана до вызова **S'LPrepare** или **S'LExecDirect** для *StatementHandle*.<br /><br /> (DM) Асинхронно выполнение функции (не этот) был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** был вызван для *statementHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.<br /><br /> Подробнее о том, когда может быть освобождена ручка оператора, читайте в материале [«Функция «SLPrepare»](../../../odbc/reference/syntax/sqlprepare-function.md) для получения подробной информации.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
|IM017|Опрос отключен в асинхронном режиме уведомления|Всякий раз, когда используется модель уведомления, опрос отключается.|  
|IM018|Для завершения предыдущей асинхронной операции на этой ручке не был вызван **S'LCompleteAsync.**|Если предыдущий вызов функции на ручке возвращается SQL_STILL_EXECUTING и если режим уведомления включен, **s'LCompleteAsync** должен быть вызван на ручку, чтобы сделать пост-обработку и завершить операцию.|  
  
 **В** зависимости от того, когда источник данных оценивает заявление, связанное с заявлением, можно вернуть любой S'LSTATE, который может быть возвращен с **помощью S'LPrepare** или **S'LExecute,** когда он будет вызван после **S'LPrepare** и до **s'LExecute.**  
  
## <a name="comments"></a>Комментарии  
 **Успешно** вызываться только тогда, когда заявление находится в подготовленном, выполненном или позиционированном состоянии.  
  
 Если выписка, связанная с *statementHandle,* не возвращает столбцы, **S'LNumResultCols** устанавливает*колонкуCountPtr* до 0.  
  
 Количество столбцов, возвращенных **S'LNumResultCols,** является тем же значением, что и SQL_DESC_COUNT поле IRD.  
  
 Для получения дополнительной информации см. [Был создан набор результатов?](../../../odbc/reference/develop-app/was-a-result-set-created.md) и [как используются метаданные?](../../../odbc/reference/develop-app/how-is-metadata-used.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка буфера к столбцовику в наборе результатов|[SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки оператора|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возвращение информации о столбце в наборе результатов|[Функция SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Возвращение информации о столбце в наборе результатов|[Функция SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|Выполнение оператора S'L|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнение подготовленного заявления по S'L|[Функция «СЗЛВы»](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Получение блока данных или прокрутка набора результатов|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Получение одной строки или блока данных в направлении только вперед|[Функция S'LFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Получение части или всего столбца данных|[Функция SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|Подготовка оператора S'L к исполнению|[Функция SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Настройка параметров прокрутки курсора|[Функция SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
