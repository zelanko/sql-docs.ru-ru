---
description: Сопоставление замещающих функций для обеспечения обратной совместимости приложений
title: Сопоставление функций замены для совместимости приложений — ODBC | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7cba29b0dda2b0d4533444fd3fa8b83eaaeae7a9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461416"
---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>Сопоставление замещающих функций для обеспечения обратной совместимости приложений
Приложение ODBC *3. x* , работающее с диспетчером драйверов ODBC *3. x* , будет работать с драйвером ODBC *2. x* , если новые функции не используются. Однако дублирование функциональных возможностей и изменений поведения влияет на способ работы приложения ODBC *3. x* в драйвере ODBC *2. x* . При работе с драйвером ODBC *2. x* диспетчер драйверов сопоставляет следующие функции ODBC *3. x* , которые заменили одну или несколько функций ODBC *2. x* , в соответствующие функции ODBC *2. x* .  
  
|ODBC *3. x,* функция|Функция ODBC *2. x*|  
|-------------------------|-------------------------|  
|**Функцию SQLAllocHandle**|**SQLAllocEnv**, **SQLAllocConnect**или **SQLAllocStmt**|  
|**SQLBulkOperations**|**функция SQLSetPos;**|  
|**SQLColAttribute**|**SQLColAttributes**|  
|**SQLEndTran**|**SQLTransact**|  
|**SQLFetch**|**SQLExtendedFetch**|  
|**SQLFetchScroll**|**SQLExtendedFetch**|  
|**SQLFreeHandle**|**SQLFreeEnv**, **SQLFreeConnect**или **SQLFreeStmt**|  
|**SQLGetConnectAttr**|**SQLGetConnectOption**|  
|**Функции SQLGetDiagRec**|**SQLError**|  
|**SQLGetStmtAttr**|**SQLGetStmtOption**[1]|  
|**SQLSetConnectAttr**|**SQLSetConnectOption**|  
|**SQLSetStmtAttr**|**SQLSetStmtOption**[1]|  
  
 [1] также могут быть предприняты другие действия в зависимости от запрашиваемого атрибута.  
  
## <a name="sqlallochandle"></a>Функцию SQLAllocHandle  
 Диспетчер драйверов сопоставляет это с **SQLAllocEnv**, **SQLAllocConnect**или **SQLAllocStmt**, как нужно. Следующий вызов **функцию SQLAllocHandle**:  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 приведет к тому, что диспетчер драйверов выполнит следующие сопоставления (основные понятия, без проверки на наличие ошибок):  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
 Диспетчер драйверов сопоставляет это с **SQLSetPos**. Следующий вызов **SQLBulkOperations**:  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 приведет к следующей последовательности действий:  
  
1.  Если аргументом операции является SQL_ADD, диспетчер драйверов вызывает функцию **SQLSetPos** следующим образом:  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  Если аргумент операции не SQL_ADD, драйвер возвращает значение SQLSTATE HY092 (недопустимый идентификатор атрибута или параметра).  
  
3.  Если приложение пытается изменить SQL_ATTR_ROW_STATUS_PTR между вызовами **SQLFetch** или **SQLFetchScroll** и **SQLBulkOperations**, диспетчер драйверов вернет значение SQLSTATE HY011 (атрибут не может быть установлен).  
  
4.  Если аргумент операции имеет SQL_ADD, приложение должно вызвать **SQLBindCol** для привязки вставляемых данных. Он не может вызвать **SQLSetDescField** или **SQLSetDescRec** для привязки вставляемых данных.  
  
5.  Если аргумент операции имеет SQL_ADD и число вставляемых строк не совпадает с текущим размером набора строк, необходимо вызвать **SQLSetStmtAttr** , чтобы задать атрибуту SQL_ATTR_ROW_ARRAY_SIZE инструкции число строк, вставляемых перед вызовом **SQLBulkOperations**. Чтобы вернуться к предыдущему размеру набора строк, приложение должно задать атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции перед вызовом **SQLFetch**, **SQLFetchScroll**или **SQLSetPos** .  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 Диспетчер драйверов сопоставляет это с **SQLColAttributes**. Следующий вызов **SQLColAttribute**:  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 приведет к следующей последовательности действий:  
  
1.  Если *фиелдидентифиер* является одним из следующих:  
  
     SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH, SQL_DESC_OCTET_LENGTH, SQL_DESC_UNNAMED, SQL_DESC_BASE_COLUMN_NAME, SQL_DESC_LITERAL_PREFIX, SQL_DESC_LITERAL_SUFFIX или SQL_DESC_LOCAL_TYPE_NAME  
  
     Диспетчер драйверов возвращает SQL_ERROR с кодом SQLSTATE HY091 (недопустимый идентификатор поля дескриптора). Дальнейшие правила этого раздела не применяются.  
  
2.  Диспетчер драйверов сопоставляет SQL_COLUMN_COUNT, SQL_COLUMN_NAME или SQL_COLUMN_NULLABLE с SQL_DESC_COUNT, SQL_DESC_NAME или SQL_DESC_NULLABLE соответственно. (Драйвер ODBC *2. x* должен поддерживать только SQL_COLUMN_COUNT, SQL_COLUMN_NAME и SQL_COLUMN_NULLABLE, а не SQL_DESC_COUNT, SQL_DESC_NAME и SQL_DESC_NULLABLE.) Вызов SQLColAttribute сопоставляется с:  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  Все остальные значения *фиелдидентифиер* передаются в драйвер, при этом **SQLColAttribute** сопоставляется с **SQLColAttributes** , как показано выше.  
  
4.  Если *BufferLength* меньше 0, диспетчер драйверов возвращает SQL_ERROR с SQLSTATE HY090 (Недопустимая строка или длина буфера). Дальнейшие правила этого раздела не применяются.  
  
5.  Если *фиелдидентифиер* имеет SQL_DESC_CONCISE_TYPE и возвращаемый тип имеет тип данных Краткая дата и время, диспетчер драйверов сопоставляет возвращаемые значения для кодов даты, времени и отметки времени.  
  
6.  Диспетчер драйверов выполняет необходимые проверки, чтобы определить, требуется ли порождение HY010а SQLSTATE (ошибка последовательности функций). Если это так, диспетчер драйверов возвращает SQL_ERROR и SQLSTATE HY010 (ошибка последовательности функций). Дальнейшие правила этого раздела не применяются.  
  
## <a name="sqlendtran"></a>SQLEndTran  
 Диспетчер драйверов сопоставляет это с **SQLTransact**. Следующий вызов **SQLEndTran**:  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 приведет к тому, что диспетчер драйверов выполнит следующие сопоставления (основные понятия, без проверки на наличие ошибок):  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 Диспетчер драйверов сопоставляет это с **SQLExtendedFetch** с аргументом *фетчориентатион* SQL_FETCH_NEXT. Следующий вызов **SQLFetch**:  
  
```  
SQLFetch (StatementHandle);  
```  
  
 приведет к вызову **SQLExtendedFetch**диспетчером драйверов, как показано ниже.  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 В этом вызове для аргумента *пкров* задается значение, которое приложение задает атрибуту инструкции SQL_ATTR_ROWS_FETCHED_PTR с помощью вызова **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Когда приложение вызывает **SQLSetStmtAttr** , чтобы задать SQL_ATTR_ROW_STATUS_PTR для указания на массив состояния, диспетчер драйверов кэширует указатель. *Ровстатусаррай* может быть равным пустому указателю.  
  
 Если драйвер не поддерживает **SQLExtendedFetch** и не загружена библиотека курсоров, диспетчер драйверов использует **SQLExtendedFetch** библиотеки курсоров для преобразования **SQLFetch** в **SQLExtendedFetch**. Если драйвер не поддерживает **SQLExtendedFetch** , а библиотека курсоров не загружена, диспетчер драйверов передает вызов **SQLFetch** через драйвер. Если приложение вызывает **SQLSetStmtAttr** для установки SQL_ATTR_ROW_STATUS_PTR, диспетчер драйверов гарантирует заполнение массива. Если приложение вызывает **SQLSetStmtAttr** для установки SQL_ATTR_ROWS_FETCHED_PTR, диспетчер драйверов устанавливает это поле в значение 1.  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 Диспетчер драйверов сопоставляет это с **SQLExtendedFetch**. Следующий вызов **SQLFetchScroll**:  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 приведет к следующей последовательности действий:  
  
1.  Когда приложение вызывает **SQLSetStmtAttr** для установки SQL_ATTR_ROW_STATUS_PTR (которое задает SQL_DESC_ARRAY_STATUS_PTR поле в IRD) для указания на массив состояния, диспетчер драйверов кэширует этот указатель. Пусть этот указатель должен быть *ровстатусаррай*; в противном случае Let *ровстатусаррай* должен быть равным пустому указателю. Если для аргумента *ровстатусаррай* задан пустой указатель, диспетчер драйверов формирует массив строкового состояния.  
  
2.  Если *фетчориентатион* не является одним из SQL_FETCH_NEXT, SQL_FETCH_PRIOR, SQL_FETCH_ABSOLUTE, SQL_FETCH_RELATIVE, SQL_FETCH_FIRST, SQL_FETCH_LAST или SQL_FETCH_BOOKMARK, диспетчер драйверов возвращает с SQL_ERROR и SQLSTATE HY106 (тип выборки за пределами диапазона). Дальнейшие правила этого раздела не применяются.  
  
3.  Регистр:  
  
-   Если *фетчориентатион* равен SQL_FETCH_BOOKMARK, то:  
  
    -   Если **SQLSetStmtAttr** был вызван ранее для установки значения SQL_ATTR_FETCH_BOOKMARK_PTR, то Let *БМК* будет иметь значение, полученное путем разыменования SQL_DESC_FETCH_BOOKMARK_PTR указателя.  
  
    -   В противном случае возвращается SQL_ERROR с SQLSTATE HY111 (недопустимое значение закладки). Дальнейшие правила этого раздела не применяются.  
  
     Теперь диспетчер драйверов вызывает **SQLExtendedFetch**следующим образом:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   В противном случае диспетчер драйверов вызывает **SQLExtendedFetch**следующим образом:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     В этих вызовах для аргумента *пкров* задается значение, которое приложение задает атрибуту инструкции SQL_ATTR_ROWS_FETCHED_PTR с помощью вызова **SQLSetStmtAttr**.  
  
-   SQL_ATTR_ROW_ARRAY_SIZE сопоставляется с SQL_ROWSET_SIZE.  
  
-   Если значение *RC* равно SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, а если *фетчориентатион* равно SQL_FETCH_BOOKMARK и *Фетчоффсет* не равно 0, диспетчер драйверов отправляет предупреждение, SQLSTATE 01S10 (попытка получить значение смещения закладки, игнорируется) и возвращает SQL_SUCCESS_WITH_INFO.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 Диспетчер драйверов сопоставляет это с **SQLFreeEnv**, **SQLFreeConnect**или **SQLFreeStmt** соответствующим образом. Следующий вызов **SQLFreeHandle**:  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 приведет к тому, что диспетчер драйверов выполнит следующие сопоставления (основные понятия, без проверки на наличие ошибок):  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 Диспетчер драйверов сопоставляет это с **SQLGetConnectOption**. Следующий вызов **SQLGetConnectAttr**:  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 приведет к следующей последовательности действий:  
  
1.  Если *атрибут* не является определяемым драйвером соединением или атрибутом инструкции и не является атрибутом, определенным в ODBC *2. x*, диспетчер драйверов возвращает SQL_ERROR с параметром SQLSTATE HY092 (недопустимый идентификатор атрибута или параметра). Дальнейшие правила в этом разделе не применяются.  
  
2.  Если *атрибут* равен SQL_ATTR_AUTO_IPD или SQL_ATTR_METADATA_ID, диспетчер драйверов возвращает SQL_ERROR с параметром SQLSTATE HY092 (недопустимый идентификатор атрибута или параметра).  
  
3.  Диспетчер драйверов выполняет необходимые проверки, чтобы определить, нужно ли вызывать SQLSTATE 08003 (соединение не открыто) или SQLSTATE HY010 (ошибка последовательности функций). Если это так, диспетчер драйверов возвращает SQL_ERROR и отправляет соответствующее сообщение об ошибке. Дальнейшие правила этого раздела не применяются.  
  
4.  Диспетчер драйверов вызывает **SQLGetConnectOption** следующим образом:  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     Обратите внимание, что *BufferLength* и *стрингленгсптр* игнорируются.  
  
## <a name="sqlgetdata"></a>SQLGetData  
 Когда приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , вызывает **SQLGetData** с аргументом *columnNumber* , равным 0, диспетчер драйверов ODBC *3. x* сопоставляет это с вызовом **SQLGetStmtOption** с атрибутом *Option* , имеющим значение SQL_GET_BOOKMARK.  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
 Диспетчер драйверов сопоставляет это с **SQLGetStmtOption**. Следующий вызов **SQLGetStmtAttr**:  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 приведет к следующей последовательности действий:  
  
1.  Если *атрибут* не является определяемым драйвером соединением или атрибутом инструкции и не является атрибутом, определенным в ODBC *2. x*, диспетчер драйверов возвращает SQL_ERROR с параметром SQLSTATE HY092 (недопустимый идентификатор атрибута или параметра). Дальнейшие правила в этом разделе не применяются.  
  
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
  
     Диспетчер драйверов возвращает SQL_ERROR с параметром SQLSTATE HY092 (недопустимый идентификатор атрибута или параметра). Дальнейшие правила этого раздела не применяются.  
  
3.  Диспетчер драйверов выполняет необходимые проверки, чтобы определить, требуется ли порождение HY010а SQLSTATE (ошибка последовательности функций). Если это так, диспетчер драйверов возвращает SQL_ERROR и SQLSTATE HY010 (ошибка последовательности функций). Дальнейшие правила этого раздела не применяются.  
  
4.  Если *атрибут* равен SQL_ATTR_ROWS_FETCHED_PTR, диспетчер драйверов возвращает указатель на внутреннюю переменную диспетчера драйверов *CRowset*, которая использовалась или будет использоваться в вызове **SQLExtendedFetch**. Дальнейшие правила этого раздела не применяются.  
  
5.  Если *атрибут* равен SQL_DESC_FETCH_BOOKMARK_PTR, диспетчер драйверов возвращает соответствующий указатель, кэшированный во время вызова **SQLSetStmtAttr**.  
  
6.  Если *атрибут* равен SQL_ATTR_ROW_STATUS_PTR, диспетчер драйверов возвращает соответствующий указатель, кэшированный во время вызова **SQLSetStmtAttr**.  
  
7.  Диспетчер драйверов вызывает **SQLGetStmtOption** следующим образом:  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     где *хстмт*, *параметром fOption*и *Пвпарам* будут установлены в значения *статеменсандле*, *Attribute*и *ValuePtr*соответственно. *BufferLength* и *стрингленгсптр* игнорируются.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Диспетчер драйверов сопоставляет это с **SQLSetConnectOption**. Следующий вызов **SQLSetConnectAttr**:  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 приведет к следующей последовательности действий:  
  
1.  Если *атрибут* не является определяемым драйвером соединением или атрибутом инструкции и не является атрибутом, определенным в ODBC *2. x*, диспетчер драйверов возвращает SQL_ERROR с параметром SQLSTATE HY092 (недопустимый идентификатор атрибута или параметра). Дальнейшие правила в этом разделе не применяются.  
  
2.  Если *атрибут* равен SQL_ATTR_AUTO_IPD, диспетчер драйверов возвращает SQL_ERROR с параметром SQLSTATE HY092 (недопустимый идентификатор атрибута или параметра).  
  
3.  Диспетчер драйверов выполняет необходимые проверки, чтобы определить, требуется ли вызывать SQLSTATE 08003 (соединение не открыто) или SQLSTATE HY010 (ошибка последовательности функций). Если возникает одна из этих ошибок, диспетчер драйверов возвращает SQL_ERROR и отправляет соответствующее сообщение об ошибке. Дальнейшие правила этого раздела не применяются.  
  
4.  Диспетчер драйверов вызывает **SQLSetConnectOption** следующим образом:  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     где *хдбк*, *параметром fOption*и *Впарам* будут установлены в значения *коннектионхандле*, *Attribute*и *ValuePtr*соответственно. *Стрингленгсптр* игнорируется.  
  
> [!NOTE]  
>  Возможность задавать атрибуты инструкций на уровне соединения не рекомендуется. Не следует задавать атрибуты инструкции на уровне соединения с помощью приложения ODBC *3. x* .  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Диспетчер драйверов сопоставляет это с **SQLSetStmtOption**. Следующий вызов **SQLSetStmtAttr**:  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 приведет к следующей последовательности действий:  
  
1.  Если *атрибут* не является определяемым драйвером соединением или атрибутом инструкции и не является атрибутом, определенным в ODBC *2. x*, диспетчер драйверов возвращает SQL_ERROR с параметром SQLSTATE HY092 (недопустимый идентификатор атрибута или параметра). Дальнейшие правила в этом разделе не применяются.  
  
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
  
     Диспетчер драйверов возвращает SQL_ERROR с параметром SQLSTATE HY092 (недопустимый идентификатор атрибута или параметра). Дальнейшие правила этого раздела не применяются.  
  
3.  Диспетчер драйверов выполняет необходимые проверки, чтобы определить, требуется ли порождение HY010а SQLSTATE (ошибка последовательности функций). Если это так, диспетчер драйверов возвращает SQL_ERROR и SQLSTATE HY010 (ошибка последовательности функций). Дальнейшие правила этого раздела не применяются.  
  
4.  Если *атрибут* равен SQL_ATTR_PARAMSET_SIZE или SQL_ATTR_PARAMS_PROCESSED_PTR, см. раздел "сопоставления для обработки массивов параметров" Далее в этом разделе. Дальнейшие правила этого раздела не применяются.  
  
5.  Если *атрибут* равен SQL_ATTR_ROWS_FETCHED_PTR, диспетчер драйверов кэширует значение указателя для последующего использования с **SQLFetchScroll**.  
  
6.  Если *атрибут* равен SQL_ATTR_ROW_STATUS_PTR, диспетчер драйверов кэширует значение указателя для последующего использования с **SQLFetchScroll** или **SQLSetPos**. Дальнейшие правила этого раздела не применяются.  
  
7.  Если *атрибут* равен SQL_ATTR_FETCH_BOOKMARK_PTR, диспетчер драйверов кэширует *ValuePtr* и будет использовать кэшированное значение позже при вызове **SQLFetchScroll**. Дальнейшие правила этого раздела не применяются.  
  
8.  Диспетчер драйверов вызывает **SQLSetStmtOption** следующим образом:  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     где *хстмт*, *параметром fOption*и *Впарам* будут установлены в значения *статеменсандле*, *Attribute*и *ValuePtr*соответственно. Аргумент *StringLength* игнорируется.  
  
     Если драйвер ODBC *2. x* поддерживает параметры символьной строки, инструкции для конкретного драйвера, приложение ODBC *3. x* должно вызывать **SQLSetStmtOption** для установки этих параметров.  
  
## <a name="mappings-for-handling-parameter-arrays"></a>Сопоставления для обработки массивов параметров  
 Когда приложение вызывает:  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 Диспетчер драйверов вызывает:  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 Позже диспетчер драйверов возвращает указатель на эту переменную, когда приложение вызывает **SQLGetStmtAttr** для получения SQL_ATTR_PARAMS_PROCESSED_PTR. Диспетчеру драйверов не удается изменить эту внутреннюю переменную, пока не вернется маркер инструкции в состояние "подготовлено" или "выделено".  
  
 Приложение ODBC *3. x* может вызывать **SQLGetStmtAttr** для получения значения SQL_ATTR_PARAMS_PROCESSED_PTR даже несмотря на то, что в APD не задано явно поле SQL_DESC_ARRAY_SIZE. Такая ситуация может возникнуть, например, если приложение имеет универсальную подпрограммы, которая проверяет текущую "строку" обрабатываемых параметров, когда **SQLExecute** возвращает SQL_NEED_DATA. Эта подпрограммы вызывается независимо от того, равен ли SQL_DESC_ARRAY_SIZE 1 или больше 1. Для этого диспетчеру драйверов необходимо определить эту внутреннюю переменную, если приложение вызывает **SQLSetStmtAttr** , чтобы задать поле SQL_DESC_ARRAY_SIZE в APD. Если SQL_DESC_ARRAY_SIZE не задан, диспетчер драйверов должен убедиться, что эта переменная содержит значение 1 перед возвратом из **SQLExecDirect** или **SQLExecute**.  
  
## <a name="error-handling"></a>Обработка ошибок  
 В ODBC *3. x*вызов **SQLFetch** или **SQLFetchScroll** заполняет SQL_DESC_ARRAY_STATUS_PTR в IRD, а поле SQL_DIAG_ROW_NUMBER заданной диагностической записи содержит номер строки в наборе строк, к которой относится эта запись. С помощью этого приложения можно сопоставить сообщение об ошибке с заданной позицией строки.  
  
 Драйвер ODBC *2. x* не сможет предоставить эту функцию. Однако он будет предоставлять ошибку разделительной с SQLSTATE 01S01 (ошибка в строке). Приложение ODBC *3. x* , использующее **SQLFetch** или **SQLFetchScroll** при переходе к драйверу ODBC *2. x* , должно учитывать этот факт. Обратите внимание, что такое приложение не сможет вызвать **SQLGetDiagField** для фактического получения поля SQL_DIAG_ROW_NUMBER. Приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , может вызывать **SQLGetDiagField** только с аргументом *диагидентифиер* SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_RETURNCODE или SQL_DIAG_SQLSTATE. Диспетчер драйверов ODBC *3. x* сохраняет структуру диагностических данных при работе с драйвером ODBC *2. x* , но драйвер ODBC *2. x* возвращает только эти четыре поля.  
  
 Если приложение ODBC *2. x* работает с драйвером ODBC *2. x* , если операция может привести к возвращению нескольких ошибок диспетчером драйверов, то диспетчер драйверов ODBC *3. x* может вернуть различные ошибки, чем диспетчер драйверов ODBC *2. x* .  
  
## <a name="mappings-for-bookmark-operations"></a>Сопоставления для операций с закладками  
 Диспетчер драйверов ODBC *3. x* выполняет следующие сопоставления, когда приложение ODBC 3. *x* , работающее с драйвером ODBC *2. x* , выполняет операции с закладками.  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 Когда приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , вызывает **SQLBindCol** для привязки к столбцу 0 с *фктипе* , равным SQL_C_VARBOOKMARK, диспетчер драйверов ODBC *3. x* проверяет, имеет ли аргумент *BufferLength* значение меньше 4 или больше 4, и если да, то возвращает значение SQLSTATE HY090 (Недопустимая строка или длина буфера). Если аргумент *BufferLength* равен 4, диспетчер драйверов вызывает **SQLBindCol** в драйвере после замены *фктипе* на SQL_C_BOOKMARK.  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 Когда приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , вызывает **SQLColAttribute** с аргументом *columnNumber* , установленным в 0, диспетчер драйверов возвращает значения *фиелдидентифиер* , перечисленные в следующей таблице.  
  
|*FieldIdentifier*|Значение|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (пустая строка)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|То же значение, возвращаемое функцией **SQLNumResultCols**|  
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
 Когда приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , вызывает **SQLDescribeCol** с аргументом *columnNumber* , установленным в 0, диспетчер драйверов возвращает значения, перечисленные в следующей таблице.  
  
|Буфер|Значение|  
|------------|-----------|  
|ColumnName|"" (пустая строка)|  
|* Намеленгсптр|0|  
|* Дататипептр|SQL_BINARY|  
|* Колумнсизептр|4|  
|* ДеЦималдигитсптр|0|  
|* Нуллаблептр|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 Когда приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , выполняет следующий вызов **SQLGetData** для получения закладки:  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 вызов сопоставляется с **SQLGetStmtOption** с *параметром fOption* SQL_GET_BOOKMARK следующим образом:  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 где *хстмт* и *пвпарам* установлены в значениях *статеменсандле* и *таржетвалуептр*соответственно. Закладка возвращается в буфере, на который указывает аргумент *пвпарам* (*таржетвалуептр*). Значение в буфере, на которое указывает аргумент *StrLen_or_IndPtr* в вызове **SQLGetData** , устанавливается в значение 4.  
  
 Это сопоставление необходимо для того, чтобы учитывать случаи, когда **SQLFetch** был вызван до вызова **SQLGetData** , а драйвер ODBC *2. x* не поддерживал **SQLExtendedFetch**. В этом случае **SQLFetch** будет передан драйверу ODBC *2. x* , в этом случае извлечение закладок не поддерживается.  
  
 **SQLGetData** нельзя вызывать несколько раз в драйвере ODBC *2. x* для получения закладки в частях, поэтому при вызове **SQLGetData** с аргументом *BufferLength* , для которого задано значение меньше 4, а аргумент *COLUMNNUMBER* , установленный в 0, вернет SQLSTATE HY090 (Недопустимая строка или длина буфера). Однако **SQLGetData** можно вызывать несколько раз, чтобы получить одну и ту же закладку.  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Когда приложение ODBC *3. x* , работающее с драйвером ODBC *2. x* , вызывает **SQLSetStmtAttr** для установки атрибута SQL_ATTR_USE_BOOKMARKS в значение SQL_UB_VARIABLE, диспетчер драйверов задает для атрибута значение SQL_UB_ON в соответствующем драйвере ODBC *2. x* .
