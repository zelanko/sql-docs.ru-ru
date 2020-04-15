---
title: Функция S'LCopyDesc (ru) Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCopyDesc
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLCopyDesc
helpviewer_keywords:
- SQLCopyDesc function [ODBC]
ms.assetid: d5450895-3824-44c4-8aa4-d4f9752a9602
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef1fa5b319e8d72d5b70e6f2010e493eec6f844a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301231"
---
# <a name="sqlcopydesc-function"></a>Функция SQLCopyDesc
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 3.0: ISO 92  
  
 **Сводка**  
 **S'LCopyDesc** копирует информацию о дескрипторах с одной дескрипторной ручки на другую.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *SourceDescHandle*  
 (Вход) Ручка дескриптора источника.  
  
 *TargetDescHandle*  
 (Вход) Ручка дескриптора цели. Аргумент *TargetDescHandle* может быть ручкой для дескриптора приложения или IPD. *TargetDescHandle* не может быть установлен на ручку IRD, или **S'LCopyDesc** вернет S'LSTATE HY016 (не может изменить дескриптор строки реализации).  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LCopyDesc** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону S'LGetDiagRec** с *помощью handleType* of SQL_HANDLE_DESC и *ручки* *TargetDescHandle.* Если в вызове был принят недействительный *SourceDescHandle,* SQL_INVALID_HANDLE будет возвращен, но не будет возвращенs S'Lstate. В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LCopyDesc,** и разъясняются каждое из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
 При возврате ошибки вызов в **S'LCopyDesc** немедленно прерывается, а содержимое полей в дескрипторе *TargetDescHandle* не определено.  
  
 В связи с тем, что **S'LCopyDescc** может быть реализована по телефону **S'LGetDescField** и **S'LSetDescField,** **S'LCopyDesc** может вернуть S'LSTATEs, возвращенные **s'LGetDescField** или **S'LSetDescField**.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08S01|Сбой связи|Связь между драйвером и источником данных, к которому был подключен драйвер, не сработала до завершения обработки функции.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY007|Связанное заявление не подготовлено|*SourceDescHandle* был связан с IRD, и связанная ручка оператора не находилась в подготовленном или выполненном состоянии.|  
|HY010|Ошибка последовательности функций|(DM) Ручка дескриптора в *SourceDescHandle* или *TargetDescHandle* была связана с *функцией statementHandle,* для которой была вызвана асинхронно исполнительная функция (не эта) и все еще исполнялась, когда эта функция была вызвана.<br /><br /> (DM) Ручка дескриптора в *SourceDescHandle* или *TargetDescHandle* была связана с *выпиской,* для которой **s'L'LExecute,** **S'LBulkOperations**, или **S'LSetPos** был вызван и возвращен SQL_NEED_DATA. **SQLExecDirect** Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.<br /><br /> (DM) Асинхронно выполнение функции был вызван для ручки соединения, которая связана с *SourceDescHandle* или *TargetDescHandle*. Эта асинхронная функция по-прежнему исполнялась, когда была вызвана функция **S'LCopyDesc.**<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для одной из декораторов оператора, связанных с *SourceDescHandle* или *TargetDescHandle* и возвращенных SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY016|Не удается изменить дескриптор строки реализации|*TargetDescHandle* был связан с IRD.|  
|HY021|Несогласованная информация о дескрипторе|Информация о дескрипторе, проверенная во время проверки согласованности, не соответствовала. Для получения дополнительной информации, см. **SQLSetDescField**|  
|HY092|Недействительный идентификатор атрибута/опциона|Звонок в **S'LCopyDesc** вызвал звонок в **S'LSetDescField**, но * \*ValuePtr* не был действителен для аргумента *FieldIdentifier* на *TargetDescHandle.*|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *SourceDescHandle* или *TargetDescHandle,* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Вызов на **sLCopyDesc** копирует поля ручки исходного дескриптора на ручку целевого дескриптора. Поля могут быть скопированы только на дескриптор приложения или IPD, но не в IRD. Поля могут быть скопированы либо из приложения, либо из дескриптора реализации.  
  
 Поля могут быть скопированы из IRD только в том случае, если ручка оператора находится в подготовленном или выполненном состоянии; в противном случае функция возвращает S'LSTATE HY007 (Ассоциированное заявление не подготовлено).  
  
 Поля могут быть скопированы из IPD независимо от того, было ли подготовлено заявление. Если была подготовлена выписка с динамическими параметрами и поддерживается и включена автоматическая популяция IPD, то IPD заполняется водителем. При том, что **S'LCopyDesc** называется СИДП в качестве *SourceDescHandle,* заполненные поля копируются. Если IPD не засеяна драйвером, содержимое полей, первоначально наданных в IPD, копируется.  
  
 Все поля дескриптора, за исключением SQL_DESC_ALLOC_TYPE (в котором указывается, была ли ручка дескриптора автоматически или явно распределена), копируются, независимо от того, определено ли поле для дескриптора назначения. Копированные поля перезаписывают существующие поля.  
  
 Драйвер копирует все поля дескриптора, если аргументы *SourceDescHandle* и *TargetDescHandle* связаны с тем же драйвером, даже если драйверы находятся на двух разных соединениях или средах. Если аргументы *SourceDescHandle* и *TargetDescHandle* связаны с различными драйверами, менеджер драйверов копирует поля, определяемые ODBC, но не копирует поля или поля, определяемые драйверами, которые не определены ODBC для типа дескриптора.  
  
 При возникновении ошибки вызов на вызов в **S'LCopyDesc** немедленно прерывается.  
  
 При копировании SQL_DESC_DATA_PTR поля на целевом дескрипторе выполняется проверка согласованности. Если проверка согласованности не удается, s'LSTATE HY021 (несогласованная информация о дескрипторах) возвращается, и вызов в **S'LCopyDesc** немедленно прерывается. Для получения дополнительной информации о проверках согласованности, см. [SQLSetDescRec Function](../../../odbc/reference/syntax/sqlsetdescrec-function.md)  
  
 Ручки дескриптора можно скопировать через соединения, даже если соединения находятся в разных средах. Если менеджер драйвера обнаруживает, что ручки дескриптора источника и назначения не принадлежат к одному и тому же соединению, а два соединения принадлежат отдельным драйверам, он реализует **S'LCopyDesc,** выполняя копию попой с использованием **S'LGetDescField** и **S'LSetDescField.**  
  
 При вызове **S'LCopyDesc** с *помощью SourceDescHandle* на одном драйвере и *TargetDescHandle* на другом драйвере, очередь ошибок *SourceDescHandle* очищается. Это происходит в связи с тем, что в данном случае **S'LCopyDesc** реализуется по вызовам в **S'LGetDescField** и **S'LSetDescField.**  
  
> [!NOTE]  
>  Приложение может связать явно выделенную ручку дескриптора с *ручкой StatementHandle,* вместо того, чтобы вызывать **S'LCopyDesc** для копирования полей от одного дескриптора к другому. Явно выделенный дескриптор может быть связан с другим *statementHandle* на том же *ConnectionHandle,* установив атрибут SQL_ATTR_APP_ROW_DESC или SQL_ATTR_APP_PARAM_DESC оператора на ручку явно выделенного дескриптора. Когда это делается, **S'LCopyDesc** не должны вызываться для копирования значений полей дескриптора от одного дескриптора к другому. Ручка дескриптора не может быть связана с *statementHandle* на другом *ConnectionHandle*, однако; использовать одни и те же значения полей дескриптора на *выписках* на различных *соединениях,* **s'LCopyDesc** должен быть вызван.  
  
 Для описания полей в заголовке или записи [SQLSetDescField Function](../../../odbc/reference/syntax/sqlsetdescfield-function.md)дескриптора см. Для получения дополнительной информации о [Descriptors](../../../odbc/reference/develop-app/descriptors.md)дескрипторах см.  
  
## <a name="copying-rows-between-tables"></a>Копирование строк между столами  
 Приложение может копировать данные из одной таблицы в другую без копирования данных на уровне приложения. Для этого приложение связывает те же буферы данных и информацию о дескрипторе с заявлением, которое получает данные и заявление, которое вставляет данные в копию. Это может быть достигнуто либо путем обмена дескриптором приложения (связывая явно выделенный дескриптор как ARD к одному заявлению и APD в другом), либо с помощью **S'LCopyDesc** для копирования привязок между ARD и APD двух инструкций. Если операторы находятся на разных соединениях, необходимо использовать **S'LCopyDesc.** Кроме того, для копирования привязок между IRD и IPD этих двух заявлений необходимо вызвать **СЗЛКопиДеск.** При копировании по следующим заявлениям на одном и том же подключении SQL_ACTIVE_STATEMENTS тип информации, возвращенный водителем для вызова в **S'LGetInfo,** должен быть больше 1 для успеха этой операции. (Это не тот случай, когда копирование через соединения.)  
  
### <a name="code-example"></a>Пример кода  
 В следующем примере операции дескриптора используются для копирования полей таблицы PartsSource в таблицу PartsCopy. Содержимое таблицы PartsSource извлекается в рядные буферы в *hstmt0.* Эти значения используются в качестве параметров оператора INSERT на *hstmt1* для заполнения столбцов таблицы PartsCopy. Для этого поля IRD *hstmt0* копируются на поля IPD *hstmt1,* а поля ARD *hstmt0* копируются на поля APD *hstmt1.* Используйте **S'LSetDescField** для установки атрибута SQL_DESC_PARAMETER_TYPE IPD SQL_PARAM_INPUT при копировании IRD-полей из оператора с параметрами вывода в поля IPD, которые должны быть параметрами ввода.  
  
```cpp  
#define ROWS 100  
#define DESC_LEN 50  
#define SQL_SUCCEEDED(rc) (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO)  
  
// Template for a row  
typedef struct {  
   SQLINTEGER   sPartID;  
   SQLINTEGER   cbPartID;  
   SQLUCHAR     szDescription[DESC_LENGTH];  
   SQLINTEGER   cbDescription;  
   REAL         sPrice;  
   SQLINTEGER   cbPrice;  
} PartsSource;  
  
PartsSource    rget[ROWS];          // rowset buffer  
SQLUSMALLINT   sts_ptr[ROWS];       // status pointer  
SQLHSTMT       hstmt0, hstmt1;  
SQLHDESC       hArd0, hIrd0, hApd1, hIpd1;  
  
// ARD and IRD of hstmt0  
SQLGetStmtAttr(hstmt0, SQL_ATTR_APP_ROW_DESC, &hArd0, 0, NULL);  
SQLGetStmtAttr(hstmt0, SQL_ATTR_IMP_ROW_DESC, &hIrd0, 0, NULL);  
  
// APD and IPD of hstmt1  
SQLGetStmtAttr(hstmt1, SQL_ATTR_APP_PARAM_DESC, &hApd1, 0, NULL);  
SQLGetStmtAttr(hstmt1, SQL_ATTR_IMP_PARAM_DESC, &hIpd1, 0, NULL);  
  
// Use row-wise binding on hstmt0 to fetch rows  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER) sizeof(PartsSource), 0);  
  
// Set rowset size for hstmt0  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
  
// Execute a select statement  
SQLExecDirect(hstmt0, "SELECT PARTID, DESCRIPTION, PRICE FROM PARTS ORDER BY 3, 1, 2"",  
               SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt0, 1, SQL_C_SLONG, rget[0].sPartID, 0,   
   &rget[0].cbPartID);  
SQLBindCol(hstmt0, 2, SQL_C_CHAR, &rget[0].szDescription, DESC_LEN,   
   &rget[0].cbDescription);  
SQLBindCol(hstmt0, 3, SQL_C_FLOAT, rget[0].sPrice,   
   0, &rget[0].cbPrice);  
  
// Perform parameter bindings on hstmt1.   
SQLCopyDesc(hArd0, hApd1);  
SQLCopyDesc(hIrd0, hIpd1);  
  
// Set the array status pointer of IRD  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_STATUS_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the ARRAY_STATUS_PTR field of APD to be the same  
// as that in IRD.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_PARAM_OPERATION_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the hIpd1 records as input parameters  
rc = SQLSetDescField(hIpd1, 1, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 2, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 3, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
  
// Prepare an insert statement on hstmt1. PartsCopy is a copy of  
// PartsSource  
SQLPrepare(hstmt1, "INSERT INTO PARTS_COPY VALUES (?, ?, ?)", SQL_NTS);  
  
// In a loop, fetch a rowset, and copy the fetched rowset to PARTS_COPY  
  
rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
while (SQL_SUCCEEDED(rc)) {  
  
   // After the call to SQLFetchScroll, the status array has row   
   // statuses. This array is used as input status in the APD  
   // and hence determines which elements of the rowset buffer  
   // are inserted.  
   SQLExecute(hstmt1);  
  
   rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
} // while  
```  
  
### <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Получение нескольких полей дескриптора|[Функция SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Установка одного поля дескриптора|[Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Установка нескольких полей дескриптора|[Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
