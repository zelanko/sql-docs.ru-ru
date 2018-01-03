---
title: "Функция SQLDescribeParam | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLDescribeParam
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLDescribeParam
helpviewer_keywords: SQLDescribeParam function [ODBC]
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
caps.latest.revision: "28"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: df8d1653e158f19abf92eb1a650425213cbe393d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqldescribeparam-function"></a>Функция SQLDescribeParam
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ODBC  
  
 **Сводка**  
 **SQLDescribeParam** возвращает описание маркер параметра, связанный с подготовленной инструкции SQL. Эта информация также доступна в полях IPD.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLDescribeParam(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT *   DataTypePtr,  
      SQLULEN *       ParameterSizePtr,  
      SQLSMALLINT *   DecimalDigitsPtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="argument"></a>Аргумент  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *ParameterNumber*  
 [Вход] Номер маркера параметра упорядоченный последовательно в порядке возрастания параметра, начиная с 1.  
  
 *DataTypePtr*  
 [Выход] Указатель на буфер, в которую будет возвращен тип данных SQL параметра. Это значение считывается из поля записи SQL_DESC_CONCISE_TYPE в IPD. Это будет иметь одно из значений в [типов данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) раздел типы данных приложение D: или типа данных SQL специфические для драйвера.  
  
 В ODBC 3. *x*, будут возвращены в SQL_TYPE_DATE SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP  *\*DataTypePtr* для даты, времени или данных timestamp соответственно; в ODBC 2. *x*, SQL_DATE, SQL_TIME или SQL_TIMESTAMP будет возвращен. Диспетчер драйверов выполняет необходимые сопоставления при ODBC 2. *x* при работе с ODBC 3. *x* драйвера или когда ODBC 3. *x* при работе с ODBC 2. *x* драйвера.  
  
 Когда *ColumnNumber* равен 0 (для столбца закладки) SQL_BINARY возвращается в  *\*DataTypePtr* для закладок переменной длины. (SQL_INTEGER возвращается, если закладки, используемые ODBC 3. *x* приложения, работа с ODBC 2. *x* драйвера или ODBC 2. *x* приложения, работа с ODBC 3. *x* драйвера.)  
  
 Дополнительные сведения см. в разделе [типов данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) в типах данных приложение D:. Сведения о типах данных драйвера SQL см. в документации драйвера.  
  
 *ParameterSizePtr*  
 [Выход] Указатель на буфер, в котором для получения размера, в символах, столбца или выражения соответствующего маркера параметра в соответствии с определением источника данных. Дополнительные сведения о размере столбца см. в разделе [размер столбца, десятичных цифр, длина в октетах передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *DecimalDigitsPtr*  
 [Выход] Указатель на буфер, в который возвращается число десятичных знаков столбца или выражения, соответствующего параметра в соответствии с определением источника данных. Дополнительные сведения о десятичных цифр см. в разделе [размер столбца, десятичных цифр, длина в октетах передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *NullablePtr*  
 [Выход] Указатель на буфер, в которую будет возвращено значение, указывающее, допускает ли параметр значения NULL. Это значение считывается из поля SQL_DESC_NULLABLE IPD. Это может быть:  
  
-   SQL_NO_NULLS: Параметр не допускает значений NULL (значение по умолчанию).  
  
-   SQL_NULLABLE: Параметр допускает значения NULL.  
  
-   SQL_NULLABLE_UNKNOWN: Драйвер не может определить, допускает ли параметр значения NULL.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLDescribeParam** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из Значение SQL_HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLDescribeParam** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07009|Недопустимый индекс дескриптора|(DM) значение, указанное для аргумента *ParameterNumber* меньше 1.<br /><br /> Значение, указанное для аргумента *ParameterNumber* превышает число параметров в соответствующей инструкции SQL.<br /><br /> Маркер параметра входил в состав не DML-инструкции.<br /><br /> Маркер параметра входил в состав **ВЫБЕРИТЕ** списка.|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|21S01|Список вставляемых значений не соответствует списку столбцов|Число параметров в **вставить** инструкция не соответствует числу столбцов в таблице, указанной в инструкции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, который необходим для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY010|Ошибка последовательности функций|(DM) вызове функции перед вызовом **SQLPrepare** или **SQLExecDirect** для *StatementHandle*.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом асинхронной функция **SQLDescribeParam** была вызвана функция.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|В режиме асинхронное уведомление отключена опроса|При использовании модели уведомление опроса отключен.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущего вызова функции с дескриптором возвращает SQL_STILL_EXECUTING и уведомлений в режиме **SQLCompleteAsync** должен вызываться для этого после обработки и выполнения операции с дескриптором.|  
  
## <a name="comments"></a>Комментарии  
 Маркеры параметров нумеруются в порядке возрастания параметра, начиная с 1, в порядке, в котором они появляются в инструкции SQL.  
  
 **SQLDescribeParam** не возвращает тип параметра (вход, ввода вывода или выходной) в инструкции SQL. За исключением в вызовах процедур, все параметры в инструкции SQL являются входными параметрами. Чтобы определить тип каждого параметра в вызове процедуры, приложение вызывает **SQLProcedureColumns**.  
  
 Дополнительные сведения см. в разделе [описания параметров](../../../odbc/reference/develop-app/describing-parameters.md).  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере пользователю для инструкции SQL, а затем подготавливает инструкцию. Затем он вызывает **SQLNumParams** для определения, является ли инструкция содержит все параметры. Если инструкция содержит параметры, он вызывает **SQLDescribeParam** для описания этих параметров и **SQLBindParameter** для их привязки. Наконец он запрашивает у значения всех параметров пользователя и затем выполняет инструкцию.  
  
```  
SQLCHAR       Statement[100];  
SQLSMALLINT   NumParams, i, DataType, DecimalDigits, Nullable;  
SQLUINTEGER   ParamSize;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement and prepare it.  
GetSQLStatement(Statement);  
SQLPrepare(hstmt, Statement, SQL_NTS);  
  
// Check to see if there are any parameters. If so, process them.  
SQLNumParams(hstmt, &NumParams);  
if (NumParams) {  
   // Allocate memory for three arrays. The first holds pointers to buffers in which  
   // each parameter value will be stored in character form. The second contains the  
   // length of each buffer. The third contains the length/indicator value for each  
   // parameter.  
   SQLPOINTER * PtrArray = (SQLPOINTER *) malloc(NumParams * sizeof(SQLPOINTER));  
   SQLINTEGER * BufferLenArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));  
   SQLINTEGER * LenOrIndArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));  
  
   for (i = 0; i < NumParams; i++) {  
   // Describe the parameter.  
   SQLDescribeParam(hstmt, i + 1, &DataType, &ParamSize, &DecimalDigits, &Nullable);  
  
   // Call a helper function to allocate a buffer in which to store the parameter  
   // value in character form. The function determines the size of the buffer from  
   // the SQL data type and parameter size returned by SQLDescribeParam and returns  
   // a pointer to the buffer and the length of the buffer.  
   AllocParamBuffer(DataType, ParamSize, &PtrArray[i], &BufferLenArray[i]);  
  
   // Bind the memory to the parameter. Assume that we only have input parameters.  
   SQLBindParameter(hstmt, i + 1, SQL_PARAM_INPUT, SQL_C_CHAR, DataType, ParamSize,  
         DecimalDigits, PtrArray[i], BufferLenArray[i],  
         &LenOrIndArray[i]);  
  
   // Prompt the user for the value of the parameter and store it in the memory  
   // allocated earlier. For simplicity, this function does not check the value  
   // against the information returned by SQLDescribeParam. Instead, the driver does  
   // this when the statement is executed.  
   GetParamValue(PtrArray[i], BufferLenArray[i], &LenOrIndArray[i]);  
   }  
}  
  
// Execute the statement.  
SQLExecute(hstmt);  
  
// Process the statement further, such as retrieving results (if any) and closing the  
// cursor (if any). Code not shown.  
  
// Free the memory allocated for each parameter and the memory allocated for the arrays  
// of pointers, buffer lengths, and length/indicator values.  
for (i = 0; i < NumParams; i++) free(PtrArray[i]);  
free(PtrArray);  
free(BufferLenArray);  
free(LenOrIndArray);  
```  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка буфер к параметру|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выполнения подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Подготовка инструкции для выполнения|[Функция SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
