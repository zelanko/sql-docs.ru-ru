---
title: Картирование функций замены для совместимости приложений - ODBC Документы Майкрософт
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
ms.openlocfilehash: b18669fe9b6edbd39859166e382ad18d1b04a99a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301094"
---
# <a name="mapping-replacement-functions-for-backward-compatibility-of-applications"></a>Сопоставление замещающих функций для обеспечения обратной совместимости приложений
Приложение ODBC *3.x,* работая через менеджер драйвера ODBC *3.x,* будет работать против драйвера ODBC *2.x* до тех пор, пока не будут использованы новые функции. Однако как дублированные функциональные возможности, так и изменения в поведении влияют на то, как приложение ODBC *3.x* работает на драйвере ODBC *2.x.* При работе с драйвером ODBC *2.x* менеджер драйвера отображает следующие функции ODBC *3.x,* которые заменили одну или несколько функций ODBC *2.x,* на соответствующие функции ODBC *2.x.*  
  
|Функция ODBC *3.x*|Функция ODBC *2.x*|  
|-------------------------|-------------------------|  
|**СЗЛАллокХэндл**|**СЗЛАллокЕнВ,** **СЗЛАллокКоннект**, или **S'LAllocStmt**|  
|**СЗЛБалКОперации**|**функция SQLSetPos;**|  
|**SQLColAttribute**|**СЗЛКолАтрибуты**|  
|**SQLEndTran**|**СЗЛТрансакт**|  
|**SQLFetch**|**Sqlextendedfetch**|  
|**SQLFetchScroll**|**Sqlextendedfetch**|  
|**SQLFreeHandle**|**СЗЛФРИЕнв,** **СЗЛФриКоннект**, или **СЗЛФриСтмт**|  
|**SQLGetConnectAttr**|**СЗЛГетКоннектОпция**|  
|**Функции SQLGetDiagRec**|**Sqlerror**|  
|**SQLGetStmtAttr**|**СЗЛГетСтмтOption**|  
|**SQLSetConnectAttr**|**СЗЛЕтКоннектОпция**|  
|**SQLSetStmtAttr**|**СЗЛСетСтмтOption**|  
  
 Другие действия также могут быть предприняты, в зависимости от запрашиваемого атрибута.  
  
## <a name="sqlallochandle"></a>СЗЛАллокХэндл  
 Менеджер драйверов нанес это на данный упор на **s'LAllocEnv,** **S'LAllocConnect**или **S'LAllocStmt.** Следующий звонок в **S'LAllocHandle:**  
  
```  
SQLAllocHandle(HandleType, InputHandle, OutputHandlePtr);  
```  
  
 приведет к тому, что менеджер драйвера будет выполнять следующее (концептуальное, без проверки ошибок) отображение:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLAllocEnv(OutputHandlePtr));  
   case SQL_HANDLE_DBC: return (SQLAllocConnect (InputHandle, OutputHandlePtr));  
   case SQL_HANDLE_STMT: return (SQLAllocStmt (InputHandle, OutputHandlePtr));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlbulkoperations"></a>СЗЛБалКОперации  
 Менеджер драйверов отображает это на **S'LSetPos**. Следующий звонок на **s'LBulkOperations:**  
  
```  
SQLBulkOperations(hstmt, Operation);  
```  
  
 приведет к следующей последовательности шагов:  
  
1.  Если аргумент операции SQL_ADD, менеджер драйвера вызывает **S'LSetPos** следующим образом:  
  
    ```  
    SQLSetPos (hstmt, 0, SQL_ADD, SQL_LOCK_NO_CHANGE);  
    ```  
  
2.  Если аргумент операции не SQL_ADD, то драйвер возвращает S'Lstate HY092 (идентификатор атрибута/опциона недействительным).  
  
3.  Если приложение пытается изменить SQL_ATTR_ROW_STATUS_PTR между вызовами на **s'LFetch** или **S'LFetchScroll** и **S'LBulkOperations,** менеджер драйвера вернет S'LSTATE HY011 (атрибут не может быть установлен сейчас).  
  
4.  Если аргумент операции является SQL_ADD, приложение должно вызвать **S'LBindCol,** чтобы связать данные, которые будут вставлены. Он не может вызвать **S'LSetDescField** или **S'LSetDescCRec,** чтобы связать данные, которые будут вставлены.  
  
5.  Если аргумент операции является SQL_ADD и количество вставленных строк не совпадает с текущим размером строк, необходимо вызвать атрибут **SQL_ATTR_ROW_ARRAY_SIZE** оператора на количество строк, которые будут вставлены, прежде чем вызывать **S'LBulkOperations.** Чтобы вернуться к предыдущему размеру строки, приложение должно установить атрибут SQL_ATTR_ROW_ARRAY_SIZE оператора до того, как будет вызвано **s-LFetchScroll,** **S'LFetchScroll**или **S'LSetPos.**  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
 Менеджер драйверов отображает это на **S'LColAttributes.** Следующий звонок в **S'LColAttribute:**  
  
```  
SQLColAttribute(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
```  
  
 приведет к следующей последовательности шагов:  
  
1.  Если *FieldIdentifier* является одним из следующих:  
  
     SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH, SQL_DESC_OCTET_LENGTH, SQL_DESC_UNNAMED, SQL_DESC_BASE_COLUMN_NAME, SQL_DESC_LITERAL_PREFIX, SQL_DESC_LITERAL_SUFFIX или SQL_DESC_LOCAL_TYPE_NAME  
  
     Менеджер драйвера возвращает SQL_ERROR с помощью s'LSTATE HY091 (идентификатор полей недействительных дескрипторов). Никакие дополнительные правила этого раздела не применяются.  
  
2.  Менеджер драйверов отображает SQL_COLUMN_COUNT, SQL_COLUMN_NAME или SQL_COLUMN_NULLABLE SQL_DESC_COUNT, SQL_DESC_NAME или SQL_DESC_NULLABLE соответственно. (Водитель ODBC *2.x* нуждается только в поддержке SQL_COLUMN_COUNT, SQL_COLUMN_NAME и SQL_COLUMN_NULLABLE, а не SQL_DESC_COUNT, SQL_DESC_NAME и SQL_DESC_NULLABLE.) Призыв к S'LColAttribute отображается по:  
  
    ```  
    SQLColAttributes(StatementHandle, ColumnNumber, FieldIdentifier, CharacterAttributePtr, BufferLength, StringLengthPtr, NumericAttributePtr);  
    ```  
  
3.  Все остальные значения *FieldIdentifier* передаются драйверу, а **S'LColAttribute** отображаются в **S'LColAttributes,** как показано ранее.  
  
4.  Если *BufferLength* меньше 0, менеджер драйвера возвращается SQL_ERROR с S'LSTATE HY090 (Недействительная длина строки или длины буфера). Никакие дополнительные правила этого раздела не применяются.  
  
5.  Если *FieldIdentifier* является SQL_DESC_CONCISE_TYPE а возвращенный тип — это краткий тип данных о дате, менеджер драйвера отображает значения возврата для кода даты, времени и метки времени.  
  
6.  Менеджер драйвера проводит необходимые проверки, чтобы выяснить необходимость поднятия ошибки s'LSTATE HY010 (ошибка последовательности функций). Если это так, менеджер драйвера возвращает SQL_ERROR и S'Lstate HY010 (ошибка последовательности функций). Никакие дополнительные правила этого раздела не применяются.  
  
## <a name="sqlendtran"></a>SQLEndTran  
 Менеджер драйверов отображает это на **s'LTransact**. Следующий звонок в **S'LEndTran:**  
  
```  
SQLEndTran(HandleType, Handle, CompletionType);  
```  
  
 приведет к тому, что менеджер драйвера будет выполнять следующее (концептуальное, без проверки ошибок) отображение:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV:return(SQLTransact(Handle, SQL_NULL_HDBC, CompletionType));  
   case SQL_HANDLE_DBC:return(SQLTransact(SQL_NULL_HENV, Handle, CompletionType);  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlfetch"></a>SQLFetch  
 Менеджер драйвера отображает это на **S'LExtendedFetch** с *аргументом FetchOrientation* SQL_FETCH_NEXT. Следующий звонок в **S'LFetch:**  
  
```  
SQLFetch (StatementHandle);  
```  
  
 приведет к тому, что менеджер драйверов **вызовет S'LExtendedFetch,** следующим образом:  
  
```  
rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, &RowCount, RowStatusArray);  
```  
  
 В этом вызове аргумент *pcRow* устанавливается на значение, которое приложение устанавливает атрибут SQL_ATTR_ROWS_FETCHED_PTR оператора, через вызов в **S'LSetStmtAttr.**  
  
> [!NOTE]  
>  Когда приложение вызывает **S'LSetStmtAttr,** чтобы установить SQL_ATTR_ROW_STATUS_PTR указать на массив статуса, менеджер драйверов кэши указателя. *RowStatusArray* может быть равен нулевой указатель.  
  
 Если драйвер не поддерживает **S'LExtendedFetch** и библиотека курсора загружена, менеджер драйвера использует **sLExtendedFetch** библиотеки курсора для отображения **S'LFetch** к **S'LExtendedFetch.** Если драйвер не поддерживает **S'LExtendedFetch** и библиотека курсора не загружена, менеджер драйвера передает вызов **в S'LFetch** водителю. Если приложение вызывает **S'LSetStmtAttr** для установки SQL_ATTR_ROW_STATUS_PTR, менеджер драйвера гарантирует, что массив заселен. Если приложение вызывает **S'LSetStmtAttr** для установки SQL_ATTR_ROWS_FETCHED_PTR, менеджер драйвера устанавливает это поле до 1.  
  
## <a name="sqlfetchscroll"></a>SQLFetchScroll  
 Менеджер драйверов отображает это на **S'LExtendedFetch**. Следующий звонок на **S'LFetchScroll**:  
  
```  
SQLFetchScroll(StatementHandle, FetchOrientation, FetchOffset);  
```  
  
 приведет к следующей последовательности шагов:  
  
1.  Когда приложение вызывает **S'LSetStmtAttr,** чтобы установить SQL_ATTR_ROW_STATUS_PTR (который устанавливает поле SQL_DESC_ARRAY_STATUS_PTR в IRD), чтобы указать на массив состояния, менеджер драйверов кэшает этот указатель. Пусть этот указатель будет *RowStatusArray*; в противном случае, пусть *RowStatusArray* будет равен нулевой указатель. Если аргумент *RowStatusArray* настроен на нулевой указатель, менеджер драйвера генерирует массив статуса строки.  
  
2.  Если *FetchOrientation* не является одним из SQL_FETCH_NEXT, SQL_FETCH_PRIOR, SQL_FETCH_ABSOLUTE, SQL_FETCH_RELATIVE, SQL_FETCH_FIRST, SQL_FETCH_LAST или SQL_FETCH_BOOKMARK, менеджер драйверов возвращается с SQL_ERROR и S'LSTATE HY106 (Тип Fetch вне диапазона). Никакие дополнительные правила этого раздела не применяются.  
  
3.  Регистр:  
  
-   Если *FetchOrientation* равен SQL_FETCH_BOOKMARK, то:  
  
    -   Если ранее был вызван **S'LSetStmtAttr** для установки значения SQL_ATTR_FETCH_BOOKMARK_PTR, то пусть *Bmk* будет значение, полученное путем отсылки указателя SQL_DESC_FETCH_BOOKMARK_PTR.  
  
    -   В противном случае возврат SQL_ERROR с помощью S'LSTATE HY111 (недействительная стоимость закладки). Никакие дополнительные правила этого раздела не применяются.  
  
     Менеджер драйвера теперь вызывает **S'LExtendedFetch**, следующим образом:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, Bmk, pcRow, RowStatusArray);  
    ```  
  
-   В противном случае менеджер драйвера вызывает **S'LExtendedFetch,** следующим образом:  
  
    ```  
    rc = SQLExtendedFetch(StatementHandle, FetchOrientation, FetchOffset, pcRow, RowStatusArray);  
    ```  
  
     В этих вызовах аргумент *pcRow* устанавливается на значение, которое приложение устанавливает атрибут SQL_ATTR_ROWS_FETCHED_PTR оператора, через вызов в **S'LSetStmtAttr.**  
  
-   SQL_ATTR_ROW_ARRAY_SIZE отображается до SQL_ROWSET_SIZE.  
  
-   Если *rc* равен SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, и если *FetchOrientation* равен SQL_FETCH_BOOKMARK и *FetchOffset* не равен 0, то менеджер драйвера публикует предупреждение, S'Lstate 01S10 (Попытка получить закладку смещения, смещенное значение игнорируется), и возвращает SQL_SUCCESS_WITH_INFO.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 Менеджер драйверов по мере необходимости отображает это на **s'LFreeEnv,** **S'LFreeConnect**или **S'LFreeStmt.** Следующий звонок на **S'LFreeHandle:**  
  
```  
SQLFreeHandle(HandleType, Handle);  
```  
  
 приведет к тому, что менеджер драйвера будет выполнять следующее (концептуальное, без проверки ошибок) отображение:  
  
```  
switch (HandleType) {  
   case SQL_HANDLE_ENV: return (SQLFreeEnv(Handle));  
   case SQL_HANDLE_DBC: return (SQLFreeConnect(Handle));  
   case SQL_HANDLE_STMT: return (SQLFreeStmt(Handle, SQL_DROP));  
   default: // return SQL_ERROR, SQLSTATE HY092 ("Invalid attribute/option identifier")  
}  
```  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
 Менеджер драйверов отображает это на **s'LGetConnectOption**. Следующий звонок на **S'LGetConnectAttr:**  
  
```  
SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 приведет к следующей последовательности шагов:  
  
1.  Если *Attribute* не является атрибутом соединения или оператора, определяемым драйвером, определенным в ODBC *2.x,* менеджер драйвера возвращает SQL_ERROR с помощью s'LSTATE HY092 (идентификатор недействительных атрибутов/опционов). Никакие дополнительные правила в этом разделе не применяются.  
  
2.  Если *атрибут* равен SQL_ATTR_AUTO_IPD или SQL_ATTR_METADATA_ID, менеджер драйвера возвращает SQL_ERROR с помощью S'LSTATE HY092 (идентификатор атрибута/опциона).  
  
3.  Менеджер драйвера проводит необходимые проверки, чтобы проверить, нужно ли поднимать s'LSTATE 08003 (подключение не открыто) или S'LSTATE HY010 (ошибка последовательности функций). Если это так, менеджер драйвера возвращает SQL_ERROR и публикует соответствующее сообщение об ошибке. Никакие дополнительные правила этого раздела не применяются.  
  
4.  Менеджер драйвера вызывает **S'LGetConnectOption** следующим образом:  
  
    ```  
    SQLGetConnectOption (ConnectionHandle, Attribute, ValuePtr);  
    ```  
  
     Обратите внимание, что *BufferLength* и *StringLengthPtr* игнорируются.  
  
## <a name="sqlgetdata"></a>SQLGetData  
 Когда приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* вызывает **S'LGetData** с аргументом *ColumnNumber,* равным 0, менеджер драйвера ODBC *3.x* отображает это на вызов в **S'LGetStmtOption** с атрибутом *опциона,* установленным для SQL_GET_BOOKMARK.  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
 Менеджер драйверов отображает это на **s'LGetStmtOption**. Следующий звонок на **S'LGetStmtAttr:**  
  
```  
SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, StringLengthPtr);  
```  
  
 приведет к следующей последовательности шагов:  
  
1.  Если *Attribute* не является атрибутом соединения или оператора, определяемым драйвером, определенным в ODBC *2.x,* менеджер драйвера возвращает SQL_ERROR с помощью s'LSTATE HY092 (идентификатор недействительных атрибутов/опционов). Никакие дополнительные правила в этом разделе не применяются.  
  
2.  Если *Атрибут* является одним из следующих:  
  
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
  
     Менеджер драйвера возвращает SQL_ERROR с помощью s'LSTATE HY092 (идентификатор недействительных атрибутов/опционов). Никакие дополнительные правила этого раздела не применяются.  
  
3.  Менеджер драйвера проводит необходимые проверки, чтобы выяснить необходимость поднятия ошибки s'LSTATE HY010 (ошибка последовательности функций). Если это так, менеджер драйвера возвращает SQL_ERROR и S'Lstate HY010 (ошибка последовательности функций). Никакие дополнительные правила этого раздела не применяются.  
  
4.  Если *атрибут* равен SQL_ATTR_ROWS_FETCHED_PTR, менеджер драйвера возвращает указатель на внутреннюю переменную менеджера драйвера *cRow,* которую он использовал или будет использовать в вызове на **S'LExtendedFetch.** Никакие дополнительные правила этого раздела не применяются.  
  
5.  Если *attribute* равна SQL_DESC_FETCH_BOOKMARK_PTR, менеджер драйвера возвращает соответствующий указатель, который он кэшировал во время вызова на **s'LSetStmtAttr.**  
  
6.  Если *атрибут* равен SQL_ATTR_ROW_STATUS_PTR, менеджер драйвера возвращает соответствующий указатель, который он кэшировал во время вызова на **S'LSetStmtAttr.**  
  
7.  Менеджер драйвера называет **S'LGetStmtOption** следующим образом:  
  
    ```  
    SQLGetStmtOption (hstmt, fOption, pvParam);  
    ```  
  
     где *hstmt*, *fOption*и *pvParam* будут установлены к значениям *StatementHandle,* *Attribute,* и *ValuePtr,* соответственно. *BufferLength* и *StringLengthPtr* игнорируются.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 Менеджер драйверов отображает это на **s'LSetConnectOption**. Следующий звонок на **s'LSetConnectAttr:**  
  
```  
SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, StringLength);  
```  
  
 приведет к следующей последовательности шагов:  
  
1.  Если *Attribute* не является атрибутом соединения или оператора, определяемым драйвером, определенным в ODBC *2.x,* менеджер драйвера возвращает SQL_ERROR с помощью s'LSTATE HY092 (идентификатор недействительных атрибутов/опционов). Никакие дополнительные правила в этом разделе не применяются.  
  
2.  Если *атрибут* равен SQL_ATTR_AUTO_IPD, менеджер драйвера возвращает SQL_ERROR с помощью S'LSTATE HY092 (идентификатор атрибута/опциона).  
  
3.  Менеджер драйвера проводит необходимые проверки, чтобы выяснить, нужно ли поднимать s'LSTATE 08003 (подключение не открыто) или S'LSTATE HY010 (ошибка последовательности функций). Если одна из этих ошибок должна быть поднята, менеджер драйвера возвращает SQL_ERROR и публикует соответствующее сообщение об ошибке. Никакие дополнительные правила этого раздела не применяются.  
  
4.  Менеджер драйвера вызывает **S'LSetConnectOption** следующим образом:  
  
    ```  
    SQLSetConnectOption (hdbc, fOption, vParam);  
    ```  
  
     где *hdbc*, *fOption*, и *vParam* будет установлен на значения *ConnectionHandle*, *атрибут*, и *ValuePtr*, соответственно. *StringLengthPtr* игнорируется.  
  
> [!NOTE]  
>  Возможность установки атрибутов оператора на уровне соединения была унижается. Атрибуты оператора никогда не должны устанавливаться на уровне соединения приложением ODBC *3.x.*  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Менеджер драйверов отображает это на **s'LSetStmtOption**. Следующий звонок на **S'LSetStmtAttr:**  
  
```  
SQLSetStmtAttr(StatementHandle, Attribute, ValuePtr, StringLength);  
```  
  
 приведет к следующей последовательности шагов:  
  
1.  Если *Attribute* не является атрибутом соединения или оператора, определяемым драйвером, определенным в ODBC *2.x,* менеджер драйвера возвращает SQL_ERROR с помощью s'LSTATE HY092 (идентификатор недействительных атрибутов/опционов). Никакие дополнительные правила в этом разделе не применяются.  
  
2.  Если *Атрибут* является одним из следующих:  
  
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
  
     Менеджер драйвера возвращает SQL_ERROR с помощью s'LSTATE HY092 (идентификатор недействительных атрибутов/опционов). Никакие дополнительные правила этого раздела не применяются.  
  
3.  Менеджер драйвера выполняет необходимые проверки, чтобы выяснить, нужно ли поднимать ошибку последовательности функций. Если это так, менеджер драйвера возвращает SQL_ERROR и S'Lstate HY010 (ошибка последовательности функций). Никакие дополнительные правила этого раздела не применяются.  
  
4.  Если *attribute* равен SQL_ATTR_PARAMSET_SIZE или SQL_ATTR_PARAMS_PROCESSED_PTR, см. Никакие дополнительные правила этого раздела не применяются.  
  
5.  Если *атрибут* равен SQL_ATTR_ROWS_FETCHED_PTR, менеджер драйвера кэширует значение указателя для последующего использования с **помощью S'LFetchScroll.**  
  
6.  Если *атрибут* равен SQL_ATTR_ROW_STATUS_PTR, менеджер драйвера кэширует значение указателя для последующего использования с **помощью S'LFetchScroll** или **S'LSetPos.** Никакие дополнительные правила этого раздела не применяются.  
  
7.  Если *attribute* равна SQL_ATTR_FETCH_BOOKMARK_PTR, менеджер драйвера кэширует *ValuePtr* и будет использовать кэшированное значение позже при вызове на **S'LFetchScroll.** Никакие дополнительные правила этого раздела не применяются.  
  
8.  Менеджер драйвера называет **S'LSetStmtOption** следующим образом:  
  
    ```  
    SQLSetStmtOption (hstmt, fOption, vParam);  
    ```  
  
     где *hstmt*, *fOption*и *vParam* будут установлены на значения *statementHandle,* *Attribute*и *ValuePtr,* соответственно. Аргумент *StringLength* игнорируется.  
  
     Если драйвер ODBC *2.x* поддерживает параметры оператора, основанного на конкретных для драйверов, приложение ODBC *3.x* должно вызвать **s'LSetStmtOption** для установки этих параметров.  
  
## <a name="mappings-for-handling-parameter-arrays"></a>Картирование для обработки параметров массивов  
 Когда приложение звонит:  
  
```  
SQLSetStmtAttr (StatementHandle, SQL_ATTR_PARAMSET_SIZE, Size, StringLength);  
```  
  
 менеджер драйвера звонит:  
  
```  
SQLParamOptions (StatementHandle, Size, &RowCount);  
```  
  
 Менеджер драйвера позже возвращает указатель к этой переменной, когда приложение вызывает **S'LGetStmtAttr** для получения SQL_ATTR_PARAMS_PROCESSED_PTR. Менеджер драйвера не может изменить эту внутреннюю переменную до тех пор, пока ручка оператора не будет возвращена в подготовленное или выделенное состояние.  
  
 Приложение ODBC *3.x* может вызвать **S'LGetStmtAttr,** чтобы получить значение SQL_ATTR_PARAMS_PROCESSED_PTR даже если оно явно не установило SQL_DESC_ARRAY_SIZE поле в APD. Такая ситуация может возникнуть, например, если приложение имеет общую рутину, которая проверяет текущую "строку" параметров, обрабатываемых при SQL_NEED_DATA **возвратах s'LExecute.** Эта процедура вызывается ли SQL_DESC_ARRAY_SIZE 1 или больше, чем 1. Для учета этого менеджеру драйвера необходимо будет определить эту внутреннюю переменную, действительно ли приложение вызвало **S'LSetStmtAttr,** чтобы установить поле SQL_DESC_ARRAY_SIZE в APD. Если SQL_DESC_ARRAY_SIZE не установлена, менеджер драйвера должен убедиться, что эта переменная содержит значение 1 до возвращения из **S'LExecDirect** или **S'LExecute.**  
  
## <a name="error-handling"></a>Обработка ошибок  
 В ODBC *3.x,* вызов **s'LFetch** или **S'LFetchScroll** заполняет SQL_DESC_ARRAY_STATUS_PTR в IRD, и поле SQL_DIAG_ROW_NUMBER данной диагностической записи содержит количество строки в строке, к которой относится эта запись. Используя это, приложение может соотнести сообщение об ошибке с заданной позицией строки.  
  
 Водитель ODBC *2.x* не сможет предоставить эту функциональность. Тем не менее, он обеспечит демаркацию ошибок с помощью S'LSTATE 01S01 (Ошибка в строке). Приложение ODBC *3.x,* используюеееееео **S'LFetch** или **S'LFetchScroll,** идя против драйвера ODBC *2.x,* должно быть осведомлено об этом факте. Отметим также, что такое приложение не сможет вызвать **S'LGetDiagField,** чтобы получить поле SQL_DIAG_ROW_NUMBER в любом случае. Приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* сможет звонить по **телефону s'LGetDiagField** только с *аргументом DiagIdentifier* SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_RETURNCODE или SQL_DIAG_SQLSTATE. Менеджер драйвера ODBC *3.x* поддерживает структуру диагностических данных при работе с драйвером ODBC *2.x,* но драйвер ODBC *2.x* возвращает только эти четыре поля.  
  
 Когда приложение ODBC *2.x* работает с драйвером ODBC *2.x,* если операция может привести к возврату нескольких ошибок менеджером драйвера, различные ошибки могут быть возвращены менеджером драйверов ODBC *3.x,* чем менеджером драйвера ODBC *2.x.*  
  
## <a name="mappings-for-bookmark-operations"></a>Картирование для операций с закладками  
 Менеджер драйвера ODBC *3.x* выполняет следующие отображения, когда приложение ODBC *3.x* работает с драйвером ODBC *2.x,* выполняя операции закладок.  
  
### <a name="sqlbindcol"></a>SQLBindCol  
 Когда приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* вызывает **S'LBindCol,** чтобы привязаться к столбцу 0 с *fCType,* равным SQL_C_VARBOOKMARK, менеджер драйвера ODBC *3.x* проверяет, является ли аргумент *BufferLength* менее 4 или больше, чем 4, и если да, то возвращает S'LSTATE HY090 (недействительная длина строки или буфера). Если аргумент *BufferLength* равен 4, менеджер драйвера вызывает **S'LBindCol** в драйвере, заменив *fCType* на SQL_C_BOOKMARK.  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 Когда приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* вызывает **S'LColAttribute** с аргументом *ColumnNumber,* установленным до 0, менеджер драйвера возвращает значения *FieldIdentifier,* перечисленные в следующей таблице.  
  
|*FieldIdentifier*|Значение|  
|-----------------------|-----------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_FALSE|  
|SQL_DESC_CASE_SENSITIVE|SQL_FALSE|  
|SQL_DESC_CATALOG_NAME|"" (пустая строка)|  
|SQL_DESC_CONCISE_TYPE|SQL_BINARY|  
|SQL_DESC_COUNT|Такое же значение, возвращенное **S'LNumResultCols**|  
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
 Когда приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* вызывает **S'LDescribeCol** с аргументом *ColumnNumber,* установленным на 0, менеджер драйвера возвращает значения, перечисленные в следующей таблице.  
  
|Буфер|Значение|  
|------------|-----------|  
|ColumnName|"" (пустая строка)|  
|«ИмяВидлина|0|  
|«DataTypePtr|SQL_BINARY|  
|«ColumnSizePtr»|4|  
|«ДесятичнаяДияпСПтр|0|  
|NullablePtr|SQL_NO_NULLS|  
  
### <a name="sqlgetdata"></a>SQLGetData  
 Когда приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* делает следующий звонок в **S'LGetData** для получения закладки:  
  
```  
SQLGetData(StatementHandle, 0, SQL_C_VARBOOKMARK, TargetValuePtr, BufferLength, StrLen_or_IndPtr)  
```  
  
 вызов отображается на **s'LGetStmtOption** с *fOption* SQL_GET_BOOKMARK, следующим образом:  
  
```  
SQLGetStmtOption(hstmt, SQL_GET_BOOKMARK, TargetValuePtr)  
```  
  
 где *hstmt* и *pvParam* установлены к значениям в *StatementHandle* и *TargetValuePtr*, соответственно. Закладка возвращается в буфер, на который указывает *аргумент pvParam* *(TargetValuePtr).* Значение в буфере, на который указывает *StrLen_or_IndPtr* аргумент в вызове к **S'LGetData** установлено до 4.  
  
 Это отображение необходимо для учета случая, в котором до вызова в **S'LGetData** был вызван **S'L-FetchData,** а драйвер ODBC *2.x* не поддерживал **S'LExtendedFetch.** В этом случае **поиск закладок** будет передан водителю ODBC *2.x,* и в этом случае поиск закладок не поддерживается.  
  
 **Неудается** несколько раз вызывать в драйвере ODBC *2.x* для получения закладки по частям, поэтому вызов **S'LGetData** с аргументом *BufferLength,* установленным на значение менее 4, и аргумент *ColumnNumber,* установленный для 0, вернет S'LSTATE HY090 (недействительная длина строки или буфера). **Тем** не менее, можно вызвать несколько раз, чтобы получить одну и ту же закладку.  
  
### <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
 Когда приложение ODBC *3.x,* работая с драйвером ODBC *2.x,* вызывает **s'LSetStmtAttr,** чтобы настроить атрибут SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE, менеджер драйвера драйвера драйвера Driver Manager устанавливает атрибут SQL_UB_ON в базовом драйвере ODBC *2.x.*
