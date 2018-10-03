---
title: Функция SQLDescribeParam | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeParam
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeParam
helpviewer_keywords:
- SQLDescribeParam function [ODBC]
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62d61d43638c0ca6e3e43da83367dff461033463
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750852"
---
# <a name="sqldescribeparam-function"></a>Функция SQLDescribeParam
**Соответствие стандартам**  
 Версия была введена: ODBC 1.0 соответствует стандартам: ODBC  
  
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
 [Вход] Параметр маркера заказанного количества последовательно в порядке возрастания параметра, начиная с 1.  
  
 *DataTypePtr*  
 [Выход] Указатель на буфер, в которую будет возвращен тип данных SQL параметра. Это значение считывается из поля записи SQL_DESC_CONCISE_TYPE в IPD. Это будет иметь одно из значений в [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) раздел типы данных приложение D: или к типу данных специфические для драйвера SQL.  
  
 В ODBC 3. *x*, SQL_TYPE_DATE SQL_TYPE_TIME и SQL_TYPE_TIMESTAMP будет возвращаться в  *\*DataTypePtr* для даты, времени или данных отметки времени соответственно; в ODBC 2. *x*, SQL_DATE, SQL_TIME или SQL_TIMESTAMP будет возвращаться. Диспетчер драйверов выполняет обязательные сопоставления при ODBC 2. *x* при работе с ODBC 3. *x* драйвера или ODBC 3. *x* при работе с ODBC 2. *x* драйвера.  
  
 Когда *ColumnNumber* равен 0 (для столбца закладки) SQL_BINARY возвращается в  *\*DataTypePtr* для закладок переменной длины. (SQL_INTEGER возвращается, если закладки используются ODBC 3. *x* приложение, которое работает с ODBC 2. *x* драйвера или ODBC 2. *x* приложение, которое работает с ODBC 3. *x* драйвера.)  
  
 Дополнительные сведения см. в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) в типах данных приложение D:. Сведения о типах данных драйвера SQL см. в разделе документации по драйверу.  
  
 *ParameterSizePtr*  
 [Выход] Указатель на буфер, в которую будет возвращен размер в символах, столбца или выражения соответствующего маркера параметра, как определено в источнике данных. Дополнительные сведения о размер столбца, см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *DecimalDigitsPtr*  
 [Выход] Указатель на буфер, в котором для возврата количества десятичных разрядов, столбца или выражения, соответствующего параметра, как определено в источнике данных. Дополнительные сведения о десятичных цифр, см. в разделе [размер столбца, десятичных разрядов, длительность октета передачи и отображаемый размер](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *NullablePtr*  
 [Выход] Указатель на буфер, в которую будет возвращено значение, указывающее, допускает ли параметр значения NULL. Это значение считывается из поля SQL_DESC_NULLABLE IPD. Это может быть:  
  
-   SQL_NO_NULLS: Параметр не допускает значений NULL (значение по умолчанию).  
  
-   SQL_NULLABLE: Параметр допускает значения NULL.  
  
-   SQL_NULLABLE_UNKNOWN: Драйвер не может определить, допускает ли параметр значения NULL.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLDescribeParam** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из Значение SQL_HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые при помощи **SQLDescribeParam** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07009|Недопустимый индекс дескриптора|(DM) значение, указанное для аргумента *ParameterNumber* меньше 1.<br /><br /> Значение, указанное для аргумента *ParameterNumber* превышает число параметров в связанной инструкции SQL.<br /><br /> Маркер параметра входил в состав не DML-инструкции.<br /><br /> Маркер параметра входил в состав **ВЫБЕРИТЕ** списка.|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|21S01|Список вставляемых значений не соответствует списку столбцов|Число параметров в **вставить** инструкция не соответствует количество столбцов в таблице, указанной в инструкции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимая для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция был снова вызван для *StatementHandle*.<br /><br /> Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY010|Ошибка последовательности функций|(DM), что функция была вызвана перед вызовом **SQLPrepare** или **SQLExecDirect** для *StatementHandle*.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. Если по-прежнему выполнении асинхронной функции **SQLDescribeParam** была вызвана функция.<br /><br /> (DM) асинхронно выполняемой функции (не такой) был вызван для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|Опрос недоступен в режиме асинхронное уведомление|Каждый раз, когда используется модель уведомлений, отключен опроса.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущий вызов функции в дескриптор возвращает SQL_STILL_EXECUTING, и если включен режим уведомлений, **SQLCompleteAsync** должен вызываться с дескриптором постобработки и завершить операцию.|  
  
## <a name="comments"></a>Комментарии  
 Маркеры параметров нумеруются в порядке возрастания параметра, начиная с 1, в порядке, в котором они появляются в инструкции SQL.  
  
 **SQLDescribeParam** не возвращает типа (входной, ввода вывода или выходной) параметра в инструкции SQL. За исключением в вызовах процедуры, все параметры в инструкциях SQL являются входными параметрами. Чтобы определить тип каждого параметра в вызове процедуры, приложение вызывает **SQLProcedureColumns**.  
  
 Дополнительные сведения см. в разделе [описания параметров](../../../odbc/reference/develop-app/describing-parameters.md).  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере запрашивает у пользователя инструкции SQL, а затем подготавливает этой инструкции. Затем он вызывает **SQLNumParams** для определения, является ли инструкция содержит все параметры. Если инструкция содержит параметры, он вызывает **SQLDescribeParam** для описания этих параметров и **SQLBindParameter** для их привязки. Наконец он запрашивает у пользователя значения всех параметров, а затем выполняет инструкцию.  
  
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
|Отмена обработка инструкций|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выполнении подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Подготовка инструкции к выполнению|[Функция SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
