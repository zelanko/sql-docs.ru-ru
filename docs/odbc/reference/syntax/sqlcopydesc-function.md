---
title: "Функция SQLCopyDesc | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLCopyDesc
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCopyDesc
helpviewer_keywords:
- SQLCopyDesc function [ODBC]
ms.assetid: d5450895-3824-44c4-8aa4-d4f9752a9602
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8e7383a16b40a966612784e864594588cc37199
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcopydesc-function"></a>Функция SQLCopyDesc
**Соответствия**  
 Появился в версии: ODBC 3.0 нормативных требований: ISO-92  
  
 **Сводка**  
 **SQLCopyDesc** копирует один дескриптор данные дескриптора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *SourceDescHandle*  
 [Вход] Дескриптор источника.  
  
 *TargetDescHandle*  
 [Вход] Целевой дескриптора. *TargetDescHandle* аргумент может иметь дескриптор дескриптор приложения или IPD. *TargetDescHandle* не может быть присвоено дескриптор IRD или **SQLCopyDesc** вернет HY016 SQLSTATE (не удается изменить дескриптор строки реализации).  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLCopyDesc** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_DESC и *обработки* из *TargetDescHandle*. Если задан недопустимый *SourceDescHandle* был передан в вызов, будет возвращена SQL_INVALID_HANDLE, но не SQLSTATE будут возвращены. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLCopyDesc** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
 Если возвращается сообщение об ошибке, вызов **SQLCopyDesc** немедленно прерывается и содержимое полей в *TargetDescHandle* дескриптора не определены.  
  
 Поскольку **SQLCopyDesc** может быть реализована путем вызова **SQLGetDescField** и **SQLSetDescField**, **SQLCopyDesc** может вернуть Атрибуты SQLSTATE, возвращенный **SQLGetDescField** или **SQLSetDescField**.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY007|Нужная инструкция не подготовлена|*SourceDescHandle* был связан с IRD и дескриптор нужная инструкция не находилась в состоянии подготовленных или выполненных.|  
|HY010|Ошибка последовательности функций|(DM) дескриптора обрабатывать *SourceDescHandle* или *TargetDescHandle* была связана с *StatementHandle* которого асинхронно выполняемой функции (не Это один) был вызван и все еще выполняется, при вызове этой функции.<br /><br /> (DM) дескриптора обрабатывать *SourceDescHandle* или *TargetDescHandle* была связана с *StatementHandle* которого **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *SourceDescHandle* или *TargetDescHandle*. Выполняется при этом асинхронной функция **SQLCopyDesc** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для одного из дескрипторов инструкций, связанных с *SourceDescHandle* или *TargetDescHandle* и возвращается SQL_PARAM_DATA_AVAILABLE. До получения данных для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY016|Не удается изменить дескриптор строки реализации|*TargetDescHandle* был связан с IRD.|  
|HY021|Неправильные сведения о дескрипторе|Сведения о дескрипторе, проверяется в ходе проверки согласованности не было идентичным. Дополнительные сведения см. в разделе «Проверка согласованности» в **SQLSetDescField**.|  
|HY092|Недопустимый атрибут идентификатор или параметра|Вызов **SQLCopyDesc** запрос вызов **SQLSetDescField**, но  *\*ValuePtr* не подходит для *FieldIdentifier* аргумент в *TargetDescHandle*.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *SourceDescHandle* или *TargetDescHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Вызов **SQLCopyDesc** копирует дескриптор дескриптор дескриптор целевого поля дескриптора источника. Поля могут быть скопированы только дескриптор приложения или IPD, но не IRD. Поля могут быть скопированы из приложения или дескриптор реализации.  
  
 Поля можно скопировать из IRD только в том случае, если дескриптор инструкции находится в состоянии подготовленных или выполненных; в противном случае функция возвращает SQLSTATE HY007 (связанная инструкция не подготовлена).  
  
 Поля могут быть скопированы из IPD ли оператор был подготовлен. Если инструкция SQL с динамических параметров был подготовлен и автоматическое заполнение IPD поддерживается и включен, IPD заполняется драйвером. Когда **SQLCopyDesc** вызывается с IPD как *SourceDescHandle*, заполненных полей, копируются. Если драйвер не заполняется IPD, копируются содержимое полей изначально в IPD.  
  
 Все поля дескриптора, за исключением SQL_DESC_ALLOC_TYPE (который указывает, является ли дескриптор автоматически или явно передан), копируются ли это поле определено для дескриптора назначения. Скопированные поля перезаписать существующие поля.  
  
 Драйвер копирует все поля дескриптора, если *SourceDescHandle* и *TargetDescHandle* аргументы связаны с помощью того же драйвера, даже если драйверы находятся на двух разных подключений или сред. Если *SourceDescHandle* и *TargetDescHandle* аргументы, сопоставленных с различными драйверами, диспетчер драйверов копирует полей, определенных для ODBC, но не копирует поля, определяемые драйвером или полей в ODBC для дескриптора типа, не определены.  
  
 Вызов **SQLCopyDesc** немедленно прерывается при возникновении ошибки.  
  
 При копировании поля SQL_DESC_DATA_PTR проверка согласованности выполняется по дескриптору целевой. Если проверка согласованности завершается сбоем, SQLSTATE HY021 возвращается (неправильные сведения о дескрипторе) и вызов **SQLCopyDesc** немедленно прерывается. Дополнительные сведения о проверки согласованности см. в разделе «Проверка согласованности» в [SQLSetDescRec, функция](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Дескриптора через подключения могут быть скопированы, даже если подключения в различных средах. Если диспетчер драйверов обнаруживает источника и назначения дескриптора дескрипторов не принадлежат то же соединение и двух подключений принадлежат разделения драйверы, он реализует **SQLCopyDesc** , выполняя поле, поле копирование с помощью **SQLGetDescField** и **SQLSetDescField**.  
  
 Когда **SQLCopyDesc** вызывается с *SourceDescHandle* на один драйвер и *TargetDescHandle* от другого драйвера, ошибка очереди  *SourceDescHandle* очищается. Это происходит потому, что **SQLCopyDesc** в этом случае реализуется путем вызова метода **SQLGetDescField** и **SQLSetDescField**.  
  
> [!NOTE]  
>  Приложение может иметь возможность связать явно выделенного дескриптора с *StatementHandle*, вместо вызова **SQLCopyDesc** скопировать один дескриптор поля. Явно выделенный дескриптор может быть связан с другим *StatementHandle* на том же *ConnectionHandle* , задав оператора SQL_ATTR_APP_ROW_DESC или SQL_ATTR_APP_PARAM_DESC атрибут к дескриптору явным образом выделенного дескриптора. Если это сделано, **SQLCopyDesc** не должен вызываться, чтобы скопировать один дескриптор значения поля дескриптора. Дескриптор не может быть связано с *StatementHandle* на другом *ConnectionHandle*, но при этом; использовать те же значения поля дескриптора на *StatementHandles*другой *ConnectionHandles*, **SQLCopyDesc** должна быть вызвана.  
  
 Описание поля заголовка дескриптора или записи, см. в разделе [функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Дополнительные сведения о дескрипторах см. в разделе [дескрипторы](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="copying-rows-between-tables"></a>Копирование строк из таблиц  
 Приложение может скопировать данные из одной таблицы в другую без копирования данных на уровне приложения. Чтобы сделать это, приложение связывает же буферов данных и сведения о дескрипторе инструкцию, которая выполняет выборку данных и инструкцию, которая вставляет данные в копии. Это можно сделать, предоставив дескриптор приложения (привязке явно выделенный дескриптор как Отменить для одного оператора и APD в другой) или с помощью **SQLCopyDesc** копирование привязки между Отменить и APD два оператора. Если операторы находятся на разных подключений **SQLCopyDesc** необходимо использовать. Кроме того **SQLCopyDesc** должна быть вызвана для копирования привязки между IRD и IPD из двух инструкций. При копировании на инструкции по тому же подключению сведения SQL_ACTIVE_STATEMENTS тип, возвращенный драйвер для вызова **SQLGetInfo** должно быть больше 1 для выполнения данной операции. (Это не так при копировании через подключения.)  
  
### <a name="code-example"></a>Пример кода  
 В следующем примере дескриптора операции используются для копирования в таблицу PartsCopy поля в таблице PartsSource. Содержимое таблицы PartsSource, выбранные в буферы строк в *hstmt0*. Эти значения используются в качестве параметров инструкции INSERT на *hstmt1* для заполнения столбцов таблицы PartsCopy. Чтобы сделать это, полях IRD из *hstmt0* копируются в полях IPD из *hstmt1*и поля Отменить из *hstmt0* копируются в поля APD *hstmt1*. Используйте **SQLSetDescField** для задания атрибута SQL_DESC_PARAMETER_TYPE в IPD SQL_PARAM_INPUT при копировании полях IRD к полям IPD, которые должны быть входными параметрами инструкции с выходными параметрами.  
  
```  
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
|Настройка одного дескриптора поля|[Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Задание нескольких полей дескриптора|[Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)

