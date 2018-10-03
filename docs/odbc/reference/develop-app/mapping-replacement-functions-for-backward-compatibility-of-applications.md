---
title: Сопоставление замещающих функций для обеспечения совместимости приложений — ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping replacement functions [ODBC]
- upgrading applications [ODBC], mapping replacement functions
- compatibility [ODBC], mapping replacement functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], mapping replacement functions
- application upgrades [ODBC], mapping replacement functions
- backward compatibility [ODBC], mapping replacement functions
ms.assetid: f5e6d9da-76ef-42cb-b3f5-f640857df732
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6cecc7fcd5ffa7234544dd0a9bc10407b1ea5cb1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626952"
---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>Сопоставление замещающих функций для обеспечения обратной совместимости приложений
ODBC 3 *.x* приложение, которое работает через ODBC 3 *.x* диспетчера драйверов будет работать для ODBC 2. *x* драйвера, если используются нет новых функций. Оба дублирование функциональные возможности и изменения в поведении Однако, влиять на, ODBC 3. *x* приложение работает в ODBC 2. *x* драйвера. При работе с ODBC 2. *x* драйвера, диспетчер драйверов сопоставляет следующие ODBC 3. *x* функций, которые были заменены один или несколько ODBC 2. *x* функции, в соответствующие ODBC 2. *x* функции.  
  
|ODBC 3. *x* функции|ODBC 2. *x* функции|  
|-------------------------|-------------------------|  
|**SQLAllocHandle**|**SQLAllocEnv**, **SQLAllocConnect**, или **SQLAllocStmt**|  
|**SQLBulkOperations**|**SQLSetPos**|  
|**SQLColAttribute**|**SQLColAttributes**|  
|**SQLEndTran**|**SQLTransact**|  
|**SQLFetch**|**SQLExtendedFetch**|  
|**SQLFetchScroll**|**SQLExtendedFetch**|  
|**SQLFreeHandle**|**SQLFreeEnv**, **SQLFreeConnect**, или **SQLFreeStmt**|  
|**SQLGetConnectAttr**|**SQLGetConnectOption**|  
|**SQLGetDiagRec**|**SQLError**|  
|**SQLGetStmtAttr**|**SQLGetStmtOption**[1]|  
|**SQLSetConnectAttr**|**SQLSetConnectOption**|  
|**SQLSetStmtAttr**|**SQLSetStmtOption**[1]|  
  
 [1] других может также выполнить действия, в зависимости от запрашиваемого атрибута.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
 Диспетчер драйверов сопоставляет этот **SQLAllocEnv**, **SQLAllocConnect**, или **SQLAllocStmt**, соответствующим образом. Следующий вызов **SQLAllocHandle**:  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 приведет к в диспетчер драйверов, выполнив (концептуальные, проверку ошибок) сопоставления:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
 Диспетчер драйверов сопоставляет этот **SQLSetPos**. Следующий вызов **SQLBulkOperations**:  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 приведет к следующие действия:  
  
1.  Если аргумент операции является SQL_ADD, диспетчер драйверов вызывает **SQLSetPos** следующим образом:  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  Если аргумент операции не SQL_ADD, драйвер возвращает SQLSTATE HY092 (недопустимый атрибута или параметра идентификатора).  
  
3.  Если приложение пытается изменить значения SQL_ATTR_ROW_STATUS_PTR, между вызовами **SQLFetch** или **SQLFetchScroll** и **SQLBulkOperations**, будет диспетчера драйверов вернуть SQLSTATE HY011 (атрибут нельзя установить сейчас).  
  
4.  Если аргумент операции является SQL_ADD, приложение должно вызвать **SQLBindCol** для привязки данных для вставки. Он не может вызвать **SQLSetDescField** или **SQLSetDescRec** для привязки данных для вставки.  
  
5.  Если аргумент операции является SQL_ADD и число строк для вставки не так же, как текущий размер набора строк, **SQLSetStmtAttr** должен вызываться количество строк, чтобы быть присвоено значение атрибута SQL_ATTR_ROW_ARRAY_SIZE инструкции вставить перед вызовом **SQLBulkOperations**. Чтобы вернуться к предыдущей размер набора строк, приложение должно установить атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции перед **SQLFetch**, **SQLFetchScroll**, или **SQLSetPos**вызывается.  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 Диспетчер драйверов сопоставляет этот **SQLColAttributes**. Следующий вызов **SQLColAttribute**:  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 приведет к следующие действия:  
  
1.  Если *FieldIdentifier* является одним из следующих:  
  
     SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH, SQL_DESC_OCTET_LENGTH, SQL_DESC_UNNAMED, SQL_DESC_BASE_COLUMN_NAME, SQL_DESC_LITERAL_PREFIX, SQL_DESC_LITERAL_SUFFIX или SQL_DESC_LOCAL_TYPE_NAME  
  
     Диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE HY091 (недопустимый идентификатор поля дескриптора). Применить все остальные правила в этом разделе.  
  
2.  Диспетчер драйверов сопоставляет SQL_COLUMN_COUNT, SQL_COLUMN_NAME или SQL_COLUMN_NULLABLE SQL_DESC_COUNT SQL_DESC_NAME и SQL_DESC_NULLABLE, соответственно. (ODBC 2 *.x* драйвер должен поддерживать только SQL_COLUMN_COUNT, SQL_COLUMN_NAME и SQL_COLUMN_NULLABLE, не SQL_DESC_COUNT, SQL_DESC_NAME и SQL_DESC_NULLABLE.) Вызов SQLColAttribute сопоставляется.  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  Все остальные *FieldIdentifier* значения передаются драйверу, с помощью **SQLColAttribute** сопоставляется **SQLColAttributes** как было показано ранее.  
  
4.  Если *BufferLength* меньше, чем 0, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE HY090 (Недопустимая длина строки или буфера). Применить все остальные правила в этом разделе.  
  
5.  Если *FieldIdentifier* является SQL_DESC_CONCISE_TYPE и возвращаемый тип является типом данных datetime краткими, диспетчер драйверов карты, возвращаемые значения для кодов date, time и timestamp.  
  
6.  Диспетчер драйверов выполняет необходимые проверки, чтобы увидеть ли параметром SQLSTATE HY010 (ошибка последовательности функций) должен вызываться. Диспетчер драйверов возвращает значение SQL_ERROR и параметром SQLSTATE HY010 (функционировать ошибка последовательности). Применить все остальные правила в этом разделе.  
  
## <a name="sqlendtran"></a>SQLEndTran  
 Диспетчер драйверов сопоставляет этот **SQLTransact**. Следующий вызов **SQLEndTran**:  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 приведет к в диспетчер драйверов, выполнив (концептуальные, проверку ошибок) сопоставления:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 Диспетчер драйверов сопоставляет этот **SQLExtendedFetch** с *FetchOrientation* аргумент для SQL_FETCH_NEXT. Следующий вызов **SQLFetch**:  
  
```  
SQLFetch (StatementHandle);  
```  
  
 приведет к вызывающего диспетчера драйверов **SQLExtendedFetch**, как показано ниже:  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 В этом вызове *pcRow* аргумент присвоено значение, которое приложение задает атрибут инструкции SQL_ATTR_ROWS_FETCHED_PTR для посредством вызова **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Когда приложение вызывает **SQLSetStmtAttr** для задания значения SQL_ATTR_ROW_STATUS_PTR указывал на массив состояний, диспетчер драйверов кэширует указатель. *RowStatusArray* может быть равным пустой указатель.  
  
 Если драйвер не поддерживает **SQLExtendedFetch** и загружается библиотека курсоров, диспетчер драйверов использует библиотеку курсоров **SQLExtendedFetch** для сопоставления **SQLFetch** для **SQLExtendedFetch**. Если драйвер не поддерживает **SQLExtendedFetch** и библиотека курсоров не загружается, вызов передается диспетчера драйверов **SQLFetch** через к драйверу. Если приложение вызывает **SQLSetStmtAttr** для задания значения SQL_ATTR_ROW_STATUS_PTR, диспетчер драйверов гарантирует, что массив заполняется. Если приложение вызывает **SQLSetStmtAttr** присвоить sql_attr_rows_fetched_ptr, которое указывает, диспетчер драйверов присваивают этому полю значение 1.  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 Диспетчер драйверов сопоставляет этот **SQLExtendedFetch**. Следующий вызов **SQLFetchScroll**:  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 приведет к следующие действия:  
  
1.  Когда приложение вызывает **SQLSetStmtAttr** для задания значения SQL_ATTR_ROW_STATUS_PTR (который устанавливает поле SQL_DESC_ARRAY_STATUS_PTR в IRD) для указания массив состояний, диспетчер драйверов кэширует этот указатель. Разрешить этот указатель быть *RowStatusArray*; в противном случае let *RowStatusArray* совпадать с пустым указателем. Если *RowStatusArray* аргумент имеет значение является пустым указателем, диспетчер драйверов создает массив состояния строк.  
  
2.  Если *FetchOrientation* не является одним из SQL_FETCH_NEXT, SQL_FETCH_PRIOR, SQL_FETCH_ABSOLUTE, SQL_FETCH_RELATIVE, SQL_FETCH_FIRST, SQL_FETCH_LAST или sql_fetch_bookmark аргумента, диспетчер драйверов возвращает значение SQL_ERROR и SQLSTATE HY106 (тип выборки за пределами диапазона). Применить все остальные правила в этом разделе.  
  
3.  Вариант.  
  
-   Если *FetchOrientation* равен sql_fetch_bookmark аргумента, затем:  
  
    -   Если **SQLSetStmtAttr** был вызван ранее, чтобы задать значение SQL_ATTR_FETCH_BOOKMARK_PTR, после чего *Bmk* быть значение, полученное путем разыменования указателя SQL_DESC_FETCH_BOOKMARK_PTR.  
  
    -   В противном случае возвращает значение SQL_ERROR с SQLSTATE HY111 (недопустимое значение закладки). Применить все остальные правила в этом разделе.  
  
     Диспетчер драйверов вызывает **SQLExtendedFetch**, как показано ниже:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   В противном случае диспетчер драйверов вызывает **SQLExtendedFetch**, как показано ниже:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     В этих вызовов *pcRow* аргумент присвоено значение, которое приложение задает атрибут инструкции SQL_ATTR_ROWS_FETCHED_PTR для посредством вызова **SQLSetStmtAttr**.  
  
-   SQL_ATTR_ROW_ARRAY_SIZE сопоставляется SQL_ROWSET_SIZE.  
  
-   Если *rc* равно SQL_SUCCESS или SQL_SUCCESS_WITH_INFO и если *FetchOrientation* равен sql_fetch_bookmark аргумента и *FetchOffset* является не равно 0, то драйвер Manager отправляет предупреждение, SQLSTATE 01S10 (попытка получить смещением закладки, учитывается значение смещения) и возвращает значение SQL_SUCCESS_WITH_INFO.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 Диспетчер драйверов сопоставляет этот **SQLFreeEnv**, **SQLFreeConnect**, или **SQLFreeStmt** соответствующим образом. Следующий вызов **SQLFreeHandle**:  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 приведет к в диспетчер драйверов, выполнив (концептуальные, проверку ошибок) сопоставления:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 Диспетчер драйверов сопоставляет этот **SQLGetConnectOption**. Следующий вызов **SQLGetConnectAttr**:  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 приведет к следующие действия:  
  
1.  Если *атрибут* не определенное драйвером атрибутом соединения или инструкции и не является атрибутом, определенным в ODBC 2. *x*, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE HY092 (недопустимый атрибута или параметра идентификатора). Применить все остальные правила в этом разделе.  
  
2.  Если *атрибута* равно SQL_ATTR_AUTO_IPD или SQL_ATTR_METADATA_ID, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE HY092 (недопустимый атрибута или параметра идентификатора).  
  
3.  Диспетчер драйверов выполняет необходимые проверки на предмет SQLSTATE 08003 (соединение не открыто) или параметром SQLSTATE HY010 (ошибка последовательности функций) должен вызываться. Если Да, диспетчер драйверов возвращает значение SQL_ERROR и отправляет соответствующее сообщение об ошибке. Применить все остальные правила в этом разделе.  
  
4.  Диспетчер драйверов вызывает **SQLGetConnectOption** следующим образом:  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     Обратите внимание, что *BufferLength* и *StringLengthPtr* игнорируются.  
  
## <a name="sqlgetdata"></a>SQLGetData  
 Когда ODBC 3. *x* приложение, которое работает с ODBC 2 *.x* драйвер вызывает **SQLGetData** с *ColumnNumber* аргумента равно 0, а ODBC 3 *.x* диспетчера драйверов сопоставляется это вызов **SQLGetStmtOption** с *параметр* SQL_GET_BOOKMARK значение атрибута.  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
 Диспетчер драйверов сопоставляет этот **SQLGetStmtOption**. Следующий вызов **SQLGetStmtAttr**:  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 приведет к следующие действия:  
  
1.  Если *атрибут* не определенное драйвером атрибутом соединения или инструкции и не является атрибутом, определенным в ODBC 2. *x*, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE HY092 (недопустимый атрибута или параметра идентификатора). Применить все остальные правила в этом разделе.  
  
2.  Если *атрибут* является одним из следующих:  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_AUTO_IPD  
  
     SQL_ATTR_ROW_BIND_TYPE  
  
     SQL_ATTR_IMP_ROW_DESC  
  
     SQL_ATTR_IMP_PARAM_DESC  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PREDICATE_PTR  
  
     SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     Возвращает значение SQL_ERROR с SQLSTATE HY092, диспетчер драйверов (недопустимый атрибута или параметра идентификатора). Применить все остальные правила в этом разделе.  
  
3.  Диспетчер драйверов выполняет необходимые проверки, чтобы увидеть ли параметром SQLSTATE HY010 (ошибка последовательности функций) должен вызываться. Диспетчер драйверов возвращает значение SQL_ERROR и параметром SQLSTATE HY010 (функционировать ошибка последовательности). Применить все остальные правила в этом разделе.  
  
4.  Если *атрибут* равен sql_attr_rows_fetched_ptr, которое указывает, диспетчер драйверов возвращает указатель на внутреннюю переменную диспетчера драйверов *cRow*, которой он использовал или будет использовать в вызове  **SQLExtendedFetch**. Применить все остальные правила в этом разделе.  
  
5.  Если *атрибут* равен SQL_DESC_FETCH_BOOKMARK_PTR, диспетчер драйверов возвращает соответствующий указатель, который он кэширован во время вызова **SQLSetStmtAttr**.  
  
6.  Если *атрибут* равен значения SQL_ATTR_ROW_STATUS_PTR, диспетчер драйверов возвращает соответствующий указатель, который он кэширован во время вызова **SQLSetStmtAttr**.  
  
7.  Диспетчер драйверов вызывает **SQLGetStmtOption** следующим образом:  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     где *hstmt*, *fOption*, и *pvParam* будет присвоено значение *StatementHandle*, *атрибут*, и *ValuePtr*, соответственно. *BufferLength* и *StringLengthPtr* игнорируются.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Диспетчер драйверов сопоставляет этот **SQLSetConnectOption**. Следующий вызов **SQLSetConnectAttr**:  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 приведет к следующие действия:  
  
1.  Если *атрибут* не определенное драйвером атрибутом соединения или инструкции и не является атрибутом, определенным в ODBC 2. *x*, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE HY092 (недопустимый атрибута или параметра идентификатора). Применить все остальные правила в этом разделе.  
  
2.  Если *атрибут* равен SQL_ATTR_AUTO_IPD, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE HY092 (недопустимый атрибута или параметра идентификатора).  
  
3.  Диспетчер драйверов выполняет необходимые проверки, чтобы увидеть ли SQLSTATE 08003 (соединение не открыто) или параметром SQLSTATE HY010 необходимости (ошибка последовательности функций), вызвано. Если одна из этих ошибок должен вызываться, диспетчер драйверов возвращает значение SQL_ERROR и отправляет соответствующее сообщение об ошибке. Применить все остальные правила в этом разделе.  
  
4.  Диспетчер драйверов вызывает **SQLSetConnectOption** следующим образом:  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     где *hdbc*, *fOption*, и *vParam* будет присвоено значение *ConnectionHandle*, *атрибут*, и *ValuePtr*, соответственно. *StringLengthPtr* учитывается.  
  
> [!NOTE]  
>  Возможность устанавливать атрибуты инструкции на уровне соединения является устаревшим. Атрибуты инструкции, никогда не должно задаваться на уровне соединения ODBC 3. *x* приложения.  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Диспетчер драйверов сопоставляет этот **SQLSetStmtOption**. Следующий вызов **SQLSetStmtAttr**:  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 приведет к следующие действия:  
  
1.  Если *атрибут* не определенное драйвером атрибутом соединения или инструкции и не является атрибутом, определенным в ODBC 2. *x*, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE HY092 (недопустимый атрибута или параметра идентификатора). Применить все остальные правила в этом разделе.  
  
2.  Если *атрибут* является одним из следующих:  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_AUTO_IPD  
  
     SQL_ATTR_ROW_BIND_TYPE  
  
     SQL_ATTR_IMP_ROW_DESC  
  
     SQL_ATTR_IMP_PARAM_DESC  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PREDICATE_PTR  
  
     SQL_ATTR_PREDICATE_OCTET_LENGTH_PTR  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     Возвращает значение SQL_ERROR с SQLSTATE HY092, диспетчер драйверов (недопустимый атрибута или параметра идентификатора). Применить все остальные правила в этом разделе.  
  
3.  Диспетчер драйверов выполняет необходимые проверки, чтобы увидеть ли вызываться необходимости параметром SQLSTATE HY010 (ошибка последовательности функций). Диспетчер драйверов возвращает значение SQL_ERROR и параметром SQLSTATE HY010 (функционировать ошибка последовательности). Применить все остальные правила в этом разделе.  
  
4.  Если *атрибут* — равно SQL_ATTR_PARAMSET_SIZE или SQL_ATTR_PARAMS_PROCESSED_PTR, см. в разделе «Сопоставления для обработки массивов параметров,» далее в этом разделе. Применить все остальные правила в этом разделе.  
  
5.  Если *атрибут* равен sql_attr_rows_fetched_ptr, которое указывает, диспетчер драйверов кэши значение указателя для последующего использования с **SQLFetchScroll**.  
  
6.  Если *атрибут* равен значения SQL_ATTR_ROW_STATUS_PTR, диспетчер драйверов кэши значение указателя для последующего использования с **SQLFetchScroll** или **SQLSetPos**. Применить все остальные правила в этом разделе.  
  
7.  Если *атрибут* равен SQL_ATTR_FETCH_BOOKMARK_PTR, диспетчер драйверов кэши *ValuePtr* и использует кэшированное значение позже в вызов **SQLFetchScroll**. Применить все остальные правила в этом разделе.  
  
8.  Диспетчер драйверов вызывает **SQLSetStmtOption** следующим образом:  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     где *hstmt*, *fOption*, и *vParam* будет присвоено значение *StatementHandle*, *атрибут*, и *ValuePtr*, соответственно. *StringLength* аргумент учитывается.  
  
     Если ODBC 2. *x* драйвер поддерживает параметры инструкции символьной строки, относящиеся к драйверу ODBC 3. *x* приложение должно вызвать **SQLSetStmtOption** для задания этих параметров.  
  
## <a name="mappings-for-handling-parameter-arrays"></a>Сопоставления для обработки массивов параметров  
 Когда приложение вызывает:  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 Диспетчер драйверов вызывает:  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 Диспетчер драйверов позже возвращает указатель на эту переменную, когда приложение вызывает **SQLGetStmtAttr** для получения SQL_ATTR_PARAMS_PROCESSED_PTR. Диспетчер драйверов нельзя изменить этой внутренней переменной, пока не дескриптора инструкции возвращается в состояние, подготовленный и выделенный.  
  
 ODBC 3. *x* приложение может вызвать **SQLGetStmtAttr** для получения значений SQL_ATTR_PARAMS_PROCESSED_PTR, несмотря на то, что оно не задано явным образом поля SQL_DESC_ARRAY_SIZE в дескрипторе параметра приложения. Такая ситуация может возникнуть, например, если приложение имеет универсальный подпрограмму, которая проверяет наличие текущего «строка» параметров при обработке **SQLExecute** возвращает SQL_NEED_DATA. Эта подпрограмма вызывается ли SQL_DESC_ARRAY_SIZE-1 или больше, чем 1. Чтобы это учесть, диспетчер драйверов будет необходимо определить это внутренняя переменная ли приложение вызвало **SQLSetStmtAttr** настроить поле SQL_DESC_ARRAY_SIZE в APD. Если не было задано SQL_DESC_ARRAY_SIZE, диспетчер драйверов приходится убедитесь, что эта переменная содержит значение от 1 до возврата из **SQLExecDirect** или **SQLExecute**.  
  
## <a name="error-handling"></a>Обработка ошибок  
 В ODBC 3. *x*, вызов **SQLFetch** или **SQLFetchScroll** заполняет SQL_DESC_ARRAY_STATUS_PTR в IRD, а в поле SQL_DIAG_ROW_NUMBER заданного диагностические записи содержит номер строки в наборе строк, этой записи, относящиеся к элементам. С помощью этого приложения можно сопоставить сообщение об ошибке с положением данной строки.  
  
 ODBC 2. *x* драйвер будет невозможно для поддержки этой функции. Тем не менее, он предоставит разделительной ошибка с кодом SQLSTATE 01S01 (ошибка в строке). ODBC 3. *x* приложение, использующее **SQLFetch** или **SQLFetchScroll** ходе выполнения инструкций от ODBC 2. *x* драйвер должен быть этот факт установлен. Обратите внимание, что такое приложение сможет вызывать **SQLGetDiagField** для реального поле SQL_DIAG_ROW_NUMBER в любом случае. ODBC 3. *x* приложение, которое работает с ODBC 2. *x* драйвер будет иметь возможность вызывать **SQLGetDiagField** только с *DiagIdentifier* аргумент SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_RETURNCODE или SQL_DIAG_ SQLSTATE. ODBC 3 *.x* диспетчера драйверов поддерживает свою структуру диагностических данных, при работе с ODBC 2. *x* драйвер, но ODBC 2. *x* драйвер возвращает только эти четыре поля.  
  
 Когда ODBC 2. *x* при работе с ODBC 2. *x* драйвера, если операция может привести к несколько ошибок, возвращаемых диспетчером драйверов, различные ошибки могут быть возвращены ODBC 3 *.x* диспетчера драйверов, чем ODBC 2. *x* диспетчера драйверов.  
  
## <a name="mappings-for-bookmark-operations"></a>Сопоставления для операций закладки  
 ODBC 3 *.x* диспетчера драйверов осуществляет следующие сопоставления при ODBC 3. *x* приложение, которое работает с ODBC 2. *x* драйвер выполняет операции закладки.  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 Когда ODBC 3. *x* приложение, которое работает с ODBC 2. *x* драйвер вызывает **SQLBindCol** для привязки к столбцу 0 с *fCType* равным SQL_C_VARBOOKMARK ODBC 3 *.x* проверяет диспетчера драйверов ли *BufferLength* аргумент меньше 4 или больше 4 и если да, возвращает SQLSTATE HY090 (Недопустимая длина строки или буфера). Если *BufferLength* аргумент равен 4, диспетчер драйверов вызывает **SQLBindCol** в драйвере после замены *fCType* с SQL_C_BOOKMARK.  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 Когда ODBC 3. *x* приложение, которое работает с ODBC 2. *x* драйвер вызывает **SQLColAttribute** с *ColumnNumber* аргумента задано значение 0, возвращает диспетчер драйверов *FieldIdentifier* значения перечисленные в следующей таблице.  
  
|*FieldIdentifier*|Значение|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (пустая строка)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|Же значение, возвращаемое **SQLNumResultCols**|  
|SQL_DESC_DATETIME_INTERVAL_CODE|0|  
|SQL_DESC_DISPLAY_SIZE|8|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_FALSE|  
|SQL_DESC_LABEL|"" (пустая строка)|  
|SQL_DESC_LENGTH|0|  
|SQL_DESC_LITERAL_PREFIX|"" (пустая строка)|  
|SQL_DESC_LITERAL_SUFFIX|"" (пустая строка)|  
|SQL_DESC_LOCAL_TYPE_NAME|"" (пустая строка)|  
|SQL_DESC_NAME|"" (пустая строка)|  
|SQL_DESC_NULLABLE|SQL_NO_NULLS|  
|SQL_DESC_OCTET_LENGTH|4|  
|SQL_DESC_PRECISION|4|  
|SQL_DESC_SCALE|0|  
|SQL_DESC_SCHEMA_NAME|"" (пустая строка)|  
|SQL_DESC_SEARCHABLE|SQL_PRED_NONE|  
|SQL_DESC_TABLE_NAME|"" (пустая строка)|  
|SQL_DESC_TYPE|SQL_BINARY|  
|SQL_DESC_TYPE_NAME|"" (пустая строка)|  
|SQL_DESC_UNNAMED|SQL_UNNAMED|  
|SQL_DESC_UNSIGNED|SQL_FALSE|  
|SQL_DESC_UPDATEABLE|SQL_ATTR_READ_ONLY|  
  
### <a name="sqldescribecol"></a>SQLDescribeCol  
 Когда ODBC 3. *x* приложение, которое работает с ODBC 2. *x* драйвер вызывает **SQLDescribeCol** с *ColumnNumber* аргументом, равным 0, диспетчер драйверов возвращает значения, перечисленные в следующей таблице.  
  
|Буфер|Значение|  
|------------|-----------|  
|ColumnName|"" (пустая строка)|  
|* NameLengthPtr|0|  
|* DataTypePtr|SQL_BINARY|  
|* ColumnSizePtr|4|  
|* DecimalDigitsPtr|0|  
|* NullablePtr|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 Когда ODBC 3. *x* приложение, которое работает с ODBC 2. *x* драйвер производит вызов **SQLGetData** извлекаемого закладки:  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 вызов сопоставлен с **SQLGetStmtOption** с *fOption* из SQL_GET_BOOKMARK, как показано ниже:  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 где *hstmt* и *pvParam* присваиваются значения в *StatementHandle* и *TargetValuePtr*, соответственно. Закладки возвращается в буфере, на которые указывают *pvParam* (*TargetValuePtr*) аргумента. Значение в буфере, на которые указывают *StrLen_or_IndPtr* аргумента в вызове **SQLGetData** установлено значение 4.  
  
 Это сопоставление необходим учесть случаи, когда **SQLFetch** был вызван до вызова **SQLGetData** и ODBC 2. *x* драйвер не поддерживает **SQLExtendedFetch**. В этом случае **SQLFetch** будут передаваться через ODBC 2. *x* драйвера, в котором получение вариантов закладка не поддерживается.  
  
 **SQLGetData** не может вызываться несколько раз в ODBC 2. *x* драйверу получать закладки в части, поэтому вызов **SQLGetData** с *BufferLength* аргументу присвоено значение меньше 4 и *ColumnNumber*аргумент присвоено значение 0 вернет SQLSTATE HY090 (Недопустимая длина строки или буфера). **SQLGetData** тем не менее, можно вызывать несколько раз для получения той же закладки.  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Когда ODBC 3. *x* приложение, которое работает с ODBC 2. *x* драйвер вызывает **SQLSetStmtAttr** значение атрибута SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE, диспетчер драйверов задает для атрибута SQL_UB_ON в базовый ODBC 2. *x* драйвера.
