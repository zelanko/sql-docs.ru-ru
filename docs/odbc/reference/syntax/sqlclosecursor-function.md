---
title: Функция S'LCloseCursor (ru) Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCloseCursor
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLCloseCursor
helpviewer_keywords:
- SQLCloseCursor function [ODBC]
ms.assetid: 05b0a054-e28d-4e16-b5b0-07418486b372
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f2703af46e6043fbadb7d3ceb5c00c565c1f6777
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301304"
---
# <a name="sqlclosecursor-function"></a>Функция SQLCloseCursor
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 3.0: ISO 92  
  
 **Сводка**  
 **S'LCloseCursor** закрывает курсор, который был открыт на выписке и отбрасывает ожидающие результатов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLCloseCursor(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *Обработка заявления*  
 (Вход) Ручка оператора.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LCloseCursor** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE может быть получено, позвонив по **телефону s'LGetDiagRec** с *помощью SQL_HANDLE_STMT* и *ручки* *statementHandle.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LCloseCursor,** и разъясняются каждое из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|24 000|Недопустимое состояние курсора|Ни один курсор не был открыт на *StatementHandle*. (Это возвращается только ODBC 3. *x* водитель.)|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) Асинхронно выполнение функции был вызван для ручки соединения, связанные с *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) Асинхронно выполнение функции был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** был вызван для *statementHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 **S'LCloseCursor** возвращает S'LSTATE 24000 (состояние недействительного курсора), если курсор не открыт. Вызов **S'LCloseCursor** эквивалентен вызову **S'LFreeStmt** с SQL_CLOSE опцией, за исключением того, что **S'LFreeStmt** с SQL_CLOSE не влияет на приложение, если в заявлении нет курсора, в то время как **S'LCloseCursor** возвращает S'LSTATE 24000 (недействительный курсор состояния).  
  
> [!NOTE]  
>  Если ODBC 3. *x* приложение работает с ODBC 2. *x* драйвер вызывает **S'LCloseCursor,** когда курсор не открыт, S'LSTATE 24000 (недействительное состояние курсора) не возвращается, потому что менеджер драйвера карты **S'LCloseCursor** в **S'LFreeStmt** с SQL_CLOSE.  
  
 Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/closing-the-cursor.md)  
  
## <a name="code-example"></a>Пример кода  
 См [с функцияю S'LBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) и [функцией S'LConnect.](../../../odbc/reference/syntax/sqlconnect-function.md)  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Отмена обработки оператора|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Освобождение ручки|[SQLFreeHandle, функция](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Обработка нескольких наборов результатов|[SQLMoreResults, функция](../../../odbc/reference/syntax/sqlmoreresults-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
