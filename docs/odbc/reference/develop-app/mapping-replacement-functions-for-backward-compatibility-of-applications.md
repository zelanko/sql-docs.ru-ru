---
title: Сопоставление замены функций для обеспечения совместимости приложений — ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14ca73aefb033580c2770da05189e3de04a424e3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>Сопоставление замены функций для обеспечения обратной совместимости приложений
ODBC 3 *.x* приложения при работе с ODBC 3 *.x* диспетчера драйверов будет работать для ODBC 2. *x* при условии, что используются не новые возможности драйвера. Оба дублирование функциональные возможности и изменения поведения тем не менее, влиять на который ODBC 3. *x* приложение работает на ODBC 2. *x* драйвера. При работе с ODBC 2. *x* драйвера, диспетчер драйверов сопоставляет следующие ODBC 3. *x* функций, которые произвели замену одного или нескольких ODBC 2. *x* функции, в соответствующие ODBC 2. *x* функции.  
  
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
  
 [1] другие действия могут также предпринять, в зависимости от запрашиваемого атрибута.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLAllocEnv**, **SQLAllocConnect**, или **SQLAllocStmt**соответствующим образом. В следующем вызове **SQLAllocHandle**:  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 приведет к диспетчера драйверов выполнив (концептуальные, проверку ошибок) сопоставления:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLSetPos**. В следующем вызове **SQLBulkOperations**:  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 приведет к следующую последовательность шагов:  
  
1.  Если аргумент операции является SQL_ADD, диспетчер драйверов вызывает **SQLSetPos** следующим образом:  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  Если аргумент операции не SQL_ADD, драйвер возвращает SQLSTATE (равным hy092) (идентификатор недопустимый атрибута или параметра).  
  
3.  Если приложение пытается изменить значения SQL_ATTR_ROW_STATUS_PTR, между вызовами **SQLFetch** или **SQLFetchScroll** и **SQLBulkOperations**, будет диспетчера драйверов Возвращает SQLSTATE HY011 (атрибут нельзя установить сейчас).  
  
4.  Если аргумент операции является SQL_ADD, приложение должно вызвать **SQLBindCol** для привязки данных для вставки. Он не может вызвать **SQLSetDescField** или **SQLSetDescRec** для привязки данных для вставки.  
  
5.  Если аргумент операции является SQL_ADD и число строк для вставки не совпадает с текущий размер набора строк **SQLSetStmtAttr** должен вызываться присваивается количество строк для атрибута SQL_ATTR_ROW_ARRAY_SIZE инструкции Перед вызовом **SQLBulkOperations**. Чтобы восстановить предыдущий размер набора строк, приложение должно установить атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции перед **SQLFetch**, **SQLFetchScroll**, или **SQLSetPos**вызывается.  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLColAttributes**. В следующем вызове **SQLColAttribute**:  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 приведет к следующую последовательность шагов:  
  
1.  Если *FieldIdentifier* является одним из следующих:  
  
     SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH, SQL_DESC_OCTET_LENGTH, SQL_DESC_UNNAMED, SQL_DESC_BASE_COLUMN_NAME, SQL_DESC_LITERAL_PREFIX, SQL_DESC_LITERAL_SUFFIX или SQL_DESC_LOCAL_TYPE_NAME  
  
     Диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE HY091 (недопустимый идентификатор поля дескриптора). Применить другим правилам этого раздела.  
  
2.  Диспетчер драйверов сопоставляет SQL_COLUMN_COUNT, SQL_COLUMN_NAME или SQL_COLUMN_NULLABLE SQL_DESC_COUNT, SQL_DESC_NAME или SQL_DESC_NULLABLE, соответственно. (ODBC 2 *.x* драйвер должен поддерживать только SQL_COLUMN_COUNT, SQL_COLUMN_NAME и SQL_COLUMN_NULLABLE, не SQL_DESC_COUNT, SQL_DESC_NAME и SQL_DESC_NULLABLE.) Вызов SQLColAttribute сопоставлено:  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  Все остальные *FieldIdentifier* значения передаются драйверу, с **SQLColAttribute** сопоставлен **SQLColAttributes** как было показано ранее.  
  
4.  Если *BufferLength* меньше, чем 0, диспетчер драйверов возвращает SQL_ERROR с SQLSTATE HY090 (Недопустимая длина строки или буфера). Применить другим правилам этого раздела.  
  
5.  Если *FieldIdentifier* является SQL_DESC_CONCISE_TYPE и возвращаемый тип четкими тип datetime, диспетчер драйверов maps, возвращаемые значения для кодов даты, времени и отметок времени.  
  
6.  Диспетчер драйверов выполняет необходимые проверяет ли SQLSTATE HY010 (ошибка последовательности функций) должен вызываться. Таким образом, диспетчер драйверов возвращает значение SQL_ERROR и SQLSTATE HY010 (функция ошибка последовательности). Применить другим правилам этого раздела.  
  
## <a name="sqlendtran"></a>SQLEndTran  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLTransact**. В следующем вызове **SQLEndTran**:  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 приведет к диспетчера драйверов выполнив (концептуальные, проверку ошибок) сопоставления:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLExtendedFetch** с *FetchOrientation* аргумент для SQL_FETCH_NEXT. В следующем вызове **SQLFetch**:  
  
```  
SQLFetch (StatementHandle);  
```  
  
 приведет к вызова диспетчера драйверов **SQLExtendedFetch**, как показано ниже:  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 В этом вызове *pcRow* аргументу присвоено значение, которое приложение устанавливает атрибут инструкции SQL_ATTR_ROWS_FETCHED_PTR для посредством вызова **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Когда приложение вызывает **SQLSetStmtAttr** для задания значения SQL_ATTR_ROW_STATUS_PTR, чтобы она указывала на массив состояний, диспетчер драйверов кэширует указателя. *RowStatusArray* может быть равно пустой указатель.  
  
 Если драйвер не поддерживает **SQLExtendedFetch** и загрузить библиотеку курсоров, диспетчер драйверов использует библиотеку курсоров **SQLExtendedFetch** для сопоставления **SQLFetch** для **SQLExtendedFetch**. Если драйвер не поддерживает **SQLExtendedFetch** и не загружается библиотека курсоров, диспетчер драйверов вызов передается **SQLFetch** посредством драйвера. Если приложение вызывает **SQLSetStmtAttr** для задания значения SQL_ATTR_ROW_STATUS_PTR, диспетчер драйверов гарантирует, что массив заполняется. Если приложение вызывает **SQLSetStmtAttr** Чтобы задать SQL_ATTR_ROWS_FETCHED_PTR, диспетчер драйверов присваивает это поле 1.  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLExtendedFetch**. В следующем вызове **SQLFetchScroll**:  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 приведет к следующую последовательность шагов:  
  
1.  Когда приложение вызывает **SQLSetStmtAttr** для задания значения SQL_ATTR_ROW_STATUS_PTR (которая задает поле SQL_DESC_ARRAY_STATUS_PTR в IRD) для указания массив состояний, диспетчер драйверов кэширует этот указатель. Разрешить этот указатель быть *RowStatusArray*; в противном случае — позволяют *RowStatusArray* равняться указатель null. Если *RowStatusArray* аргумент имеет значение является пустым указателем, диспетчер драйверов создает массив состояния строк.  
  
2.  Если *FetchOrientation* не является одним из SQL_FETCH_NEXT, SQL_FETCH_PRIOR, SQL_FETCH_ABSOLUTE, SQL_FETCH_RELATIVE, SQL_FETCH_FIRST, SQL_FETCH_LAST или SQL_FETCH_BOOKMARK, диспетчер драйверов возвращает значение SQL_ERROR и SQLSTATE HY106 (тип выборки за пределами диапазона). Применить другим правилам этого раздела.  
  
3.  Вариант.  
  
-   Если *FetchOrientation* равен SQL_FETCH_BOOKMARK, затем:  
  
    -   Если **SQLSetStmtAttr** был вызван ранее, чтобы задать значение SQL_ATTR_FETCH_BOOKMARK_PTR, после чего *Bmk* быть значение, полученное путем разыменования указателя SQL_DESC_FETCH_BOOKMARK_PTR.  
  
    -   В противном случае возвращает значение SQL_ERROR с SQLSTATE HY111 (недопустимую закладку значение). Применить другим правилам этого раздела.  
  
     Диспетчер драйверов вызывает **SQLExtendedFetch**, как показано ниже:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   В противном случае, диспетчер драйверов вызывает **SQLExtendedFetch**, как показано ниже:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     В этих вызовов *pcRow* аргументу присвоено значение, которое приложение устанавливает атрибут инструкции SQL_ATTR_ROWS_FETCHED_PTR для посредством вызова **SQLSetStmtAttr**.  
  
-   SQL_ROWSET_SIZE сопоставляется SQL_ATTR_ROW_ARRAY_SIZE.  
  
-   Если *rc* равен SQL_SUCCESS или SQL_SUCCESS_WITH_INFO и если *FetchOrientation* равен SQL_FETCH_BOOKMARK и *FetchOffset* является не равно 0, затем драйвер Manager отправляет предупреждение, SQLSTATE 01S10 (пытаются получить по смещению закладки, учитывается значение смещения) и возвращает значение SQL_SUCCESS_WITH_INFO.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLFreeEnv**, **SQLFreeConnect**, или **SQLFreeStmt** соответствующим образом. В следующем вызове **SQLFreeHandle**:  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 приведет к диспетчера драйверов выполнив (концептуальные, проверку ошибок) сопоставления:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLGetConnectOption**. В следующем вызове **SQLGetConnectAttr**:  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 приведет к следующую последовательность шагов:  
  
1.  Если *атрибута* не является определяемым драйвером соединение или оператор атрибутом и не является атрибутом, определенным в ODBC 2. *x*, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE (равным hy092) (идентификатор недопустимый атрибута или параметра). Дополнительные правила в этом разделе не применяются.  
  
2.  Если *атрибута* равно SQL_ATTR_AUTO_IPD или SQL_ATTR_METADATA_ID, диспетчер драйверов возвращает SQL_ERROR с SQLSTATE (равным hy092) (идентификатор недопустимый атрибута или параметра).  
  
3.  Диспетчер драйверов выполняет необходимые проверки на предмет SQLSTATE 08003 (соединение не открыто) или параметром SQLSTATE HY010 должен вызываться (ошибка последовательности функций). В этом случае диспетчер драйверов возвращает значение SQL_ERROR и отправляет соответствующее сообщение об ошибке. Применить другим правилам этого раздела.  
  
4.  Диспетчер драйверов вызывает **SQLGetConnectOption** следующим образом:  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     Обратите внимание, что *BufferLength* и *StringLengthPtr* игнорируются.  
  
## <a name="sqlgetdata"></a>SQLGetData  
 Когда ODBC 3. *x* приложения, работа с ODBC 2 *.x* драйвер вызывает **SQLGetData** с *ColumnNumber* аргумент равен 0, а ODBC 3 *.x* диспетчера драйверов сопоставляется это вызов **SQLGetStmtOption** с *параметр* SQL_GET_BOOKMARK значение атрибута.  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLGetStmtOption**. В следующем вызове **SQLGetStmtAttr**:  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 приведет к следующую последовательность шагов:  
  
1.  Если *атрибута* не является определяемым драйвером соединение или оператор атрибутом и не является атрибутом, определенным в ODBC 2. *x*, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE (равным hy092) (идентификатор недопустимый атрибута или параметра). Дополнительные правила в этом разделе не применяются.  
  
2.  Если *атрибута* является одним из следующих:  
  
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
  
     Диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE (равным hy092) (идентификатор недопустимый атрибута или параметра). Применить другим правилам этого раздела.  
  
3.  Диспетчер драйверов выполняет необходимые проверяет ли SQLSTATE HY010 (ошибка последовательности функций) должен вызываться. Таким образом, диспетчер драйверов возвращает значение SQL_ERROR и SQLSTATE HY010 (функция ошибка последовательности). Применить другим правилам этого раздела.  
  
4.  Если *атрибута* равен sql_attr_rows_fetched_ptr, которое указывает, возвращает диспетчера драйверов указателем внутренней переменной диспетчера драйверов *cRow*, которой он использовал или будет использовать при вызове  **SQLExtendedFetch**. Применить другим правилам этого раздела.  
  
5.  Если *атрибута* равен SQL_DESC_FETCH_BOOKMARK_PTR, диспетчер драйверов возвращает соответствующий указатель, он кэширован во время вызова **SQLSetStmtAttr**.  
  
6.  Если *атрибута* равен sql_attr_row_status_ptr, которое указывает, диспетчер драйверов возвращает соответствующий указатель, он кэширован во время вызова **SQLSetStmtAttr**.  
  
7.  Диспетчер драйверов вызывает **SQLGetStmtOption** следующим образом:  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     где *hstmt*, *fOption*, и *pvParam* будет присвоено значение *StatementHandle*, *атрибута*, и *ValuePtr*соответственно. *BufferLength* и *StringLengthPtr* игнорируются.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLSetConnectOption**. В следующем вызове **SQLSetConnectAttr**:  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 приведет к следующую последовательность шагов:  
  
1.  Если *атрибута* не является определяемым драйвером соединение или оператор атрибутом и не является атрибутом, определенным в ODBC 2. *x*, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE (равным hy092) (идентификатор недопустимый атрибута или параметра). Дополнительные правила в этом разделе не применяются.  
  
2.  Если *атрибута* равен SQL_ATTR_AUTO_IPD, диспетчер драйверов возвращает SQL_ERROR с SQLSTATE (равным hy092) (идентификатор недопустимый атрибута или параметра).  
  
3.  Диспетчер драйверов выполняет необходимые проверяет ли SQLSTATE 08003 (соединение не открыто) или параметром SQLSTATE HY010 возникать необходимости (ошибка последовательности функций). Если одна из этих ошибок должен вызываться, диспетчер драйверов возвращает значение SQL_ERROR и отправляет соответствующее сообщение об ошибке. Применить другим правилам этого раздела.  
  
4.  Диспетчер драйверов вызывает **SQLSetConnectOption** следующим образом:  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     где *hdbc*, *fOption*, и *vParam* будет присвоено значение *ConnectionHandle*, *атрибута*, и *ValuePtr*соответственно. *StringLengthPtr* учитывается.  
  
> [!NOTE]  
>  Возможность установки атрибутов инструкции на уровне соединения является устаревшим. Атрибуты инструкции, никогда не должно задаваться на уровне соединения ODBC 3. *x* приложения.  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Диспетчер драйверов сопоставляет этот параметр, чтобы **SQLSetStmtOption**. В следующем вызове **SQLSetStmtAttr**:  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 приведет к следующую последовательность шагов:  
  
1.  Если *атрибута* не является определяемым драйвером соединение или оператор атрибутом и не является атрибутом, определенным в ODBC 2. *x*, диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE (равным hy092) (идентификатор недопустимый атрибута или параметра). Дополнительные правила в этом разделе не применяются.  
  
2.  Если *атрибута* является одним из следующих:  
  
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
  
     Диспетчер драйверов возвращает ошибку SQL_ERROR с SQLSTATE (равным hy092) (идентификатор недопустимый атрибута или параметра). Применить другим правилам этого раздела.  
  
3.  Диспетчер драйверов выполняет необходимые проверки для просмотра ли возникать необходимости SQLSTATE HY010 (ошибка последовательности функций). Таким образом, диспетчер драйверов возвращает значение SQL_ERROR и SQLSTATE HY010 (функция ошибка последовательности). Применить другим правилам этого раздела.  
  
4.  Если *атрибута* — равно SQL_ATTR_PARAMSET_SIZE или SQL_ATTR_PARAMS_PROCESSED_PTR, см. в разделе «Сопоставления для обработки массивы параметров,» далее в этом разделе. Применить другим правилам этого раздела.  
  
5.  Если *атрибута* равен SQL_ATTR_ROWS_FETCHED_PTR, кэши диспетчера драйверов, значение указателя для последующего использования с **SQLFetchScroll**.  
  
6.  Если *атрибута* равен sql_attr_row_status_ptr, которое указывает, кэши диспетчера драйверов, значение указателя для последующего использования с **SQLFetchScroll** или **SQLSetPos**. Применить другим правилам этого раздела.  
  
7.  Если *атрибута* равен SQL_ATTR_FETCH_BOOKMARK_PTR, диспетчер драйверов кэши *ValuePtr* и использует кэшированное значение позже в вызов **SQLFetchScroll**. Применить другим правилам этого раздела.  
  
8.  Диспетчер драйверов вызывает **SQLSetStmtOption** следующим образом:  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     где *hstmt*, *fOption*, и *vParam* будет присвоено значение *StatementHandle*, *атрибута*, и *ValuePtr*соответственно. *StringLength* аргумент учитывается.  
  
     Если ODBC 2. *x* драйвер поддерживает параметры инструкции символьной строки, относящиеся к драйверу ODBC 3. *x* приложение должно вызывать **SQLSetStmtOption** для задания этих параметров.  
  
## <a name="mappings-for-handling-parameter-arrays"></a>Сопоставления для обработки массивы параметров  
 Когда приложение вызывает метод:  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 вызов диспетчера драйверов:  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 Диспетчер драйверов позже возвращает указатель на эту переменную при вызове приложением **SQLGetStmtAttr** для извлечения SQL_ATTR_PARAMS_PROCESSED_PTR. Диспетчер драйверов нельзя изменить эта внутренняя переменная, пока дескриптора инструкции возвращается в состояние, подготовленный и выделенный.  
  
 ODBC 3. *x* приложение может вызвать **SQLGetStmtAttr** для получения значения SQL_ATTR_PARAMS_PROCESSED_PTR, даже если оно не задано явным образом поле SQL_DESC_ARRAY_SIZE в дескрипторе параметра приложения. Такая ситуация может возникнуть, например, если приложение имеет универсальный подпрограмму, которая проверяет наличие текущего «строка» параметров при обработке **SQLExecute** возвращает SQL_NEED_DATA. Эта процедура вызывается ли SQL_DESC_ARRAY_SIZE-1 или больше 1. С учетом этого диспетчера драйверов потребуется определить эта внутренняя переменная ли приложение вызывало **SQLSetStmtAttr** требуется задать для поля SQL_DESC_ARRAY_SIZE в APD. Если SQL_DESC_ARRAY_SIZE не указан, диспетчер драйверов должен убедитесь в том, что эта переменная содержит значение от 1 до возврата из **SQLExecDirect** или **SQLExecute**.  
  
## <a name="error-handling"></a>Обработка ошибок  
 В ODBC 3. *x*, вызов **SQLFetch** или **SQLFetchScroll** заполняет SQL_DESC_ARRAY_STATUS_PTR в IRD, а в поле SQL_DIAG_ROW_NUMBER данной записи диагностики содержит номер строки в наборе строк, относящиеся к элементам данной записи. С помощью этого приложения можно сопоставить сообщение об ошибке с позиции строки.  
  
 ODBC 2. *x* драйвера будут недоступны для поддержки этой функции. Однако он предоставляет определение границ ошибка с кодом SQLSTATE 01S01 (ошибка в строке). ODBC 3. *x* приложение, использующее **SQLFetch** или **SQLFetchScroll** при переходит в ODBC 2. *x* драйвер должен быть этот факт. Обратите внимание, что такое приложение будет невозможно вызвать **SQLGetDiagField** фактически все равно получить SQL_DIAG_ROW_NUMBER поля. ODBC 3. *x* приложения, работа с ODBC 2. *x* драйвер будет вызывать **SQLGetDiagField** только с *DiagIdentifier* аргумент SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_RETURNCODE или SQL_DIAG_ SQLSTATE. ODBC 3 *.x* диспетчера драйверов поддерживается структура диагностических данных, при работе с ODBC 2. *x* драйвер, но ODBC 2. *x* драйвер возвращает только эти четыре поля.  
  
 Когда ODBC 2. *x* при работе с ODBC 2. *x* драйвера, если операция может вызвать несколько ошибок, возвращаемых диспетчером драйверов, различные ошибки могут быть возвращены ODBC 3 *.x* диспетчера драйверов, чем ODBC 2. *x* диспетчера драйверов.  
  
## <a name="mappings-for-bookmark-operations"></a>Сопоставления для операций закладки  
 ODBC 3 *.x* диспетчера драйверов осуществляет следующие сопоставления при ODBC 3. *x* приложения, работа с ODBC 2. *x* драйвер выполняет операции закладки.  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 Когда ODBC 3. *x* приложения, работа с ODBC 2. *x* драйвер вызывает **SQLBindCol** для привязки к столбцу 0 с *fCType* равно SQL_C_VARBOOKMARK ODBC 3 *.x* проверяет диспетчера драйверов ли *BufferLength* аргумента меньше 4 или больше 4 и если да, возвращает SQLSTATE HY090 (Недопустимая длина строки или буфера). Если *BufferLength* аргумент равен 4, диспетчер драйверов вызывает **SQLBindCol** в драйвере после замены *fCType* с SQL_C_BOOKMARK.  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 Когда ODBC 3. *x* приложения, работа с ODBC 2. *x* драйвер вызывает **SQLColAttribute** с *ColumnNumber* возвращает аргумента задано значение 0, диспетчер драйверов *FieldIdentifier* значения перечисленные в следующей таблице.  
  
|*FieldIdentifier*|Значение|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (пустая строка)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|Одинаковые значения, возвращенного **SQLNumResultCols**|  
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
 Когда ODBC 3. *x* приложения, работа с ODBC 2. *x* драйвер вызывает **SQLDescribeCol** с *ColumnNumber* аргумент присвоено значение 0, диспетчер драйверов возвращает значения, перечисленные в следующей таблице.  
  
|Буфер|Значение|  
|------------|-----------|  
|ColumnName|"" (пустая строка)|  
|* NameLengthPtr|0|  
|* DataTypePtr|SQL_BINARY|  
|* ColumnSizePtr|4|  
|* DecimalDigitsPtr|0|  
|* NullablePtr|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 Когда ODBC 3. *x* приложения, работа с ODBC 2. *x* драйвер производит вызов **SQLGetData** для получения закладки:  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 вызов сопоставляется **SQLGetStmtOption** с *fOption* из SQL_GET_BOOKMARK следующим образом:  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 где *hstmt* и *pvParam* присваиваются значения в *StatementHandle* и *TargetValuePtr*соответственно. Закладка возвращается в буфере, на который указывает *pvParam* (*TargetValuePtr*) аргумента. Значение в буфере, на который указывает *StrLen_or_IndPtr* аргумента в вызове **SQLGetData** установлено значение 4.  
  
 Это сопоставление необходим для учетной записи для ситуации, в которой **SQLFetch** был вызван до вызова **SQLGetData** и ODBC 2. *x* драйвер не поддерживает **SQLExtendedFetch**. В этом случае **SQLFetch** будут передаваться через ODBC 2. *x* драйвера, в котором не поддерживается получение вариантов закладки.  
  
 **SQLGetData** не может вызываться несколько раз в ODBC 2. *x* драйверу получать закладки в части, поэтому вызов **SQLGetData** с *BufferLength* аргументу присвоено значение меньше 4 и *ColumnNumber*аргумент, значение 0 будет возвращать SQLSTATE HY090 (Недопустимая длина строки или буфера). **SQLGetData** тем не менее, можно вызывать несколько раз для получения той же закладки.  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Когда ODBC 3. *x* приложения, работа с ODBC 2. *x* драйвер вызывает **SQLSetStmtAttr** для задания атрибута SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE, диспетчер драйверов устанавливает атрибут SQL_UB_ON в базовый ODBC 2. *x* драйвера.
