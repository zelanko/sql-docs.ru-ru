---
title: Функция SQLCopyDesc | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e91febb4b5b94b5a7f9df62347b4db5edcecf975
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259282"
---
# <a name="sqlcopydesc-function"></a>Функция SQLCopyDesc
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0 стандартов соответствия: ISO-92  
  
 **Сводка**  
 **SQLCopyDesc** копирует один дескриптор данные дескриптора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *SourceDescHandle*  
 [Вход] Дескриптор источника.  
  
 *TargetDescHandle*  
 [Вход] Целевой объект дескриптора. *TargetDescHandle* аргументом может быть дескриптор дескриптор приложений или IPD. *TargetDescHandle* не может быть присвоено дескриптор IRD, или **SQLCopyDesc** вернет HY016 SQLSTATE (не удается изменить дескриптор строки реализации).  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLCopyDesc** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_DESC и *обрабатывать* из *TargetDescHandle*. Если указан недопустимый *SourceDescHandle* был передан в вызове, будет возвращена SQL_INVALID_HANDLE, но не SQLSTATE будет возвращаться. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLCopyDesc** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
 Когда возвращается ошибка, вызов **SQLCopyDesc** немедленно прерывается и содержимое полей в *TargetDescHandle* дескриптора не определены.  
  
 Так как **SQLCopyDesc** могут быть реализованы путем вызова **SQLGetDescField** и **SQLSetDescField**, **SQLCopyDesc** может возвращать SQLSTATE, возвращенный **SQLGetDescField** или **SQLSetDescField**.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY007|Связанная инструкция не подготовлена|*SourceDescHandle* был связан с IRD, а соответствующий оператор дескриптор не был в состоянии подготовленных или выполненных.|  
|HY010|Ошибка последовательности функций|(DM) дескриптора в *SourceDescHandle* или *TargetDescHandle* был связан с параметром *StatementHandle* для которого асинхронно выполняемой функции (не Это один) был вызван и все еще выполняется, при вызове этой функции.<br /><br /> (DM) дескриптора в *SourceDescHandle* или *TargetDescHandle* был связан с параметром *StatementHandle* для которого **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *SourceDescHandle* или *TargetDescHandle*. Если по-прежнему выполнении асинхронной функции **SQLCopyDesc** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для одного из дескрипторов инструкций, связанных с *SourceDescHandle* или *TargetDescHandle* и возвращается SQL_PARAM_DATA_AVAILABLE. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY016|Не удается изменить дескриптор строки реализации|*TargetDescHandle* был связан с IRD.|  
|HY021|Несовместимые сведения дескриптора|Сведения о дескрипторе, проверяется в ходе проверки согласованности не согласован. Дополнительные сведения см. в разделе «Проверки согласованности» в **SQLSetDescField**.|  
|HY092|Недопустимый атрибут/идентификатор параметра|Вызов **SQLCopyDesc** запрос вызова **SQLSetDescField**, но  *\*ValuePtr* оказался недействительным для *FieldIdentifier* аргумент в *TargetDescHandle*.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *SourceDescHandle* или *TargetDescHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Вызов **SQLCopyDesc** дескриптор дескриптор дескриптор целевого поля дескриптора источника копий. Поля могут быть скопированы только дескриптор приложений или IPD, но не IRD. Поля могут быть скопированы из приложения или дескриптор реализации.  
  
 Поля можно скопировать из IRD, только в том случае, если дескриптор инструкции находится в состоянии подготовленных или выполненных; в противном случае функция возвращает SQLSTATE HY007 (связанная инструкция не подготовлена).  
  
 Поля можно скопировать из IPD ли оператор будет подготовлена. Если инструкции SQL с помощью динамических параметров будет подготовлена и автоматическое заполнение IPD поддерживается и включен, IPD заполняется с помощью драйвера. Когда **SQLCopyDesc** вызывается с IPD как *SourceDescHandle*, заполненных полей, копируются. Если IPD не заполняется с помощью драйвера, копируются содержимое полей изначально в IPD.  
  
 Все поля дескриптора, за исключением SQL_DESC_ALLOC_TYPE (который указывает тип дескриптора был автоматически или явно, выделяемые), копируются ли поле определено для дескриптора назначения. Скопированные поля перезаписывают существующие поля.  
  
 Драйвер копирует все поля дескриптора, если *SourceDescHandle* и *TargetDescHandle* аргументы являются связан один и тот же драйвер, даже если драйверы на двух различных подключениях или сред. Если *SourceDescHandle* и *TargetDescHandle* аргументы, сопоставленных с различными драйверами, диспетчер драйверов копирует полей, определяемых ODBC, но не копирует полей, определяемых драйвером или поля не определенные в ODBC для типа дескриптора.  
  
 Вызов **SQLCopyDesc** незамедлительно прерывается при возникновении ошибки.  
  
 При копировании поле SQL_DESC_DATA_PTR проверку согласованности выполняется на целевой объект дескриптора. Если проверка согласованности завершилась ошибкой, SQLSTATE HY021 возвращается (несовместимые сведения дескриптора) и вызов **SQLCopyDesc** немедленно прерывается. Дополнительные сведения о согласованности см. в разделе «Проверки согласованности» в [SQLSetDescRec, функция](../../../odbc/reference/syntax/sqlsetdescrec-function.md).  
  
 Указатели дескрипторов могут быть скопированы в соединениях, даже если подключения в различных средах. Если диспетчер драйверов обнаруживает, что исходный и конечный дескриптор, маркеры не принадлежат, и то же подключение и два подключения принадлежат для разделения драйверов, он реализует **SQLCopyDesc** , выполняя поле, поле копирование с помощью **SQLGetDescField** и **SQLSetDescField**.  
  
 Когда **SQLCopyDesc** вызывается с *SourceDescHandle* на один драйвер и *TargetDescHandle* на другого драйвера, ошибка очереди  *SourceDescHandle* очищается. Это происходит потому, что **SQLCopyDesc** в этом случае реализуется путем вызова **SQLGetDescField** и **SQLSetDescField**.  
  
> [!NOTE]  
>  Приложение может иметь возможность связать явно выделенного дескриптора с *StatementHandle*, вместо вызова метода **SQLCopyDesc** скопировать один дескриптор поля. Явно выделенные дескриптор может быть связан с другим *StatementHandle* на том же *ConnectionHandle* , задав в инструкции SQL_ATTR_APP_ROW_DESC или SQL_ATTR_APP_PARAM_DESC атрибут дескриптора явно выделенного дескриптора. Если это сделано, **SQLCopyDesc** не обязательно должен вызываться, чтобы скопировать один дескриптор значения поля дескриптора. Дескриптор не может быть связан с *StatementHandle* на другом *ConnectionHandle*, но при этом; выполнять те же значения поля дескриптора для *StatementHandles*на разных *ConnectionHandles*, **SQLCopyDesc** должен вызываться.  
  
 Описание поля заголовка дескриптора или записи, см. в разделе [функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Дополнительные сведения о дескрипторах, см. в разделе [дескрипторы](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="copying-rows-between-tables"></a>Копирование строк между таблицами  
 Приложение может копировать данные из одной таблицы в другую без копирования данных на уровне приложения. Чтобы сделать это, приложение связывает же буферов данных и сведения о дескрипторе инструкции, которая извлекает данные и оператор, который вставляет данные в копию. Это можно сделать путем совместного использования дескриптор приложений (привязка дескриптор явно выделенные как Отменить для одной инструкции, так и в дескрипторе параметра приложения в другом) или с помощью **SQLCopyDesc** Копировать привязки между Отменить и APD двух операторов. Если операторы находятся на разных подключений **SQLCopyDesc** необходимо использовать. Кроме того **SQLCopyDesc** должна быть вызвана для копирования привязки между IRD и IPD из двух операторов. При копировании между инструкций для одного соединения, тип сведений SQL_ACTIVE_STATEMENTS возвращаемых драйвером для вызова **SQLGetInfo** должно быть больше 1 для выполнения данной операции. (Это не так при копировании через подключения.)  
  
### <a name="code-example"></a>Пример кода  
 В следующем примере дескриптор операции используются для копирования поля PartsSource таблицы в таблицу PartsCopy. Содержимое таблицы PartsSource извлекаются в буферы строк в *hstmt0*. Эти значения используются в качестве параметров инструкции INSERT на *hstmt1* для заполнения столбцов таблицы PartsCopy. Чтобы сделать это, полях IRD из *hstmt0* копируются к полям IPD из *hstmt1*и полям элемента Отменить из *hstmt0* копируются в поля APD *hstmt1*. Используйте **SQLSetDescField** задать атрибут SQL_DESC_PARAMETER_TYPE в IPD SQL_PARAM_INPUT, при копировании полях IRD инструкции с выходными параметрами в полях IPD, которые должны быть входными параметрами.  
  
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
|Использование полей один дескриптор|[Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Установка нескольких полей дескриптора|[Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
