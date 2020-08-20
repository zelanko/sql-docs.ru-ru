---
description: Функция SQLDescribeParam
title: Функция SQLDescribeParam | Документация Майкрософт
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeParam
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeParam
helpviewer_keywords:
- SQLDescribeParam function [ODBC]
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0e6209f4e3145e55dfd94a9ff1375013ae5c7a85
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491317"
---
# <a name="sqldescribeparam-function"></a>Функция SQLDescribeParam
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: ODBC  
  
 **Сводка**  
 **SQLDescribeParam** Возвращает описание маркера параметра, связанного с подготовленной инструкцией SQL. Эти сведения также доступны в полях класса IPD.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLDescribeParam(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT *   DataTypePtr,  
      SQLULEN *       ParameterSizePtr,  
      SQLSMALLINT *   DecimalDigitsPtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции.  
  
 *параметернумбер*  
 Входной Номер маркера параметра, упорядоченный последовательно в порядке возрастания параметров, начиная с 1.  
  
 *дататипептр*  
 Проверки Указатель на буфер, в котором возвращается тип данных SQL параметра. Это значение считывается из поля записи SQL_DESC_CONCISE_TYPE IPD. Это одно из значений в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) приложения D: типы данных или тип данных SQL, зависящий от драйвера.  
  
 В ODBC 3. *x*, SQL_TYPE_DATE, SQL_TYPE_TIME или SQL_TYPE_TIMESTAMP будут возвращены в * \* дататипептр* для данных о дате, времени или отметке времени соответственно; в ODBC 2.* *будут возвращены x, SQL_DATE, SQL_TIME или SQL_TIMESTAMP. Диспетчер драйверов выполняет необходимые сопоставления при использовании ODBC 2. Приложение *x* работает с ODBC 3. драйвер *x* или при использовании ODBC 3. Приложение *x* работает с ODBC 2. драйвер *x* .  
  
 Если *columnNumber* равен 0 (для столбца закладки), SQL_BINARY возвращается в * \* дататипептр* для закладок переменной длины. (SQL_INTEGER возвращается, если закладки используются ODBC 3. Приложение *x* , работающее с ODBC 2. драйвер *x* или ODBC 2. Приложение *x* , работающее с ODBC 3. драйвер *x* .)  
  
 Дополнительные сведения см. в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) в приложении г: типы данных. Дополнительные сведения о типах данных SQL, относящихся к драйверам, см. в документации по драйверу.  
  
 *параметерсизептр*  
 Проверки Указатель на буфер, в котором возвращается размер столбца или выражения соответствующего маркера параметра в соответствии с определением источника данных. Дополнительные сведения о размере столбцов см. в разделе [размер столбца, десятичные цифры, длина октета и размер отображаемого](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)данных.  
  
 *деЦималдигитсптр*  
 Проверки Указатель на буфер, в котором возвращается число десятичных разрядов столбца или выражения соответствующего параметра в соответствии с определением в источнике данных. Дополнительные сведения о десятичных цифрах см. в разделе [размер столбца, десятичные цифры, длина октета и размер отображаемого](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)данных.  
  
 *нуллаблептр*  
 Проверки Указатель на буфер, в котором возвращается значение, указывающее, допускает ли параметр значения NULL. Это значение считывается из поля SQL_DESC_NULLABLE IPD. Это может быть:  
  
-   SQL_NO_NULLS: параметр не допускает значений NULL (это значение по умолчанию).  
  
-   SQL_NULLABLE: параметр допускает значения NULL.  
  
-   SQL_NULLABLE_UNKNOWN: драйвер не может определить, допускает ли параметр значения NULL.  
  
## <a name="returns"></a>Возвращаемое значение  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLDescribeParam** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLDescribeParam** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|07009|Недопустимый индекс дескриптора|(DM) значение, указанное для аргумента *параметернумбер* , меньше 1.<br /><br /> Значение, указанное для аргумента *параметернумбер* , больше числа параметров в связанной инструкции SQL.<br /><br /> Маркер параметра был частью инструкции языка, отличной от DML.<br /><br /> Маркер параметра был частью списка **выбора** .|  
|08S01|Сбой канала связи|Канал связи между драйвером и источником данных, к которому был подключен драйвер, был неудачен до завершения обработки функции.|  
|21S01|Список вставляемых значений не соответствует списку столбцов|Количество параметров в инструкции **INSERT** не соответствует числу столбцов в таблице, названной в инструкции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \* MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка включена для *статеменсандле*. Функция была вызвана, и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** для *статеменсандле*. Затем функция была вызвана в *статеменсандле*.<br /><br /> Функция была вызвана и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** в *статеменсандле* из другого потока многопоточного приложения.|  
|HY010|Ошибка последовательности функций|(DM) функция была вызвана до вызова **SQLPrepare** или **SQLExecDirect** для *статеменсандле*.<br /><br /> (DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове функции **SQLDescribeParam** .<br /><br /> (DM) вызывается асинхронно исполняемая функция (не эта одна) для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
|IM017|Опрос отключен в режиме асинхронного уведомления|При использовании модели уведомления опрос отключен.|  
|IM018|**Склкомплетеасинк** не был вызван для завершения предыдущей асинхронной операции с этим обработчиком.|Если предыдущий вызов функции в обработчике возвращает SQL_STILL_EXECUTING и если включен режим уведомления, то для обработки после обработки и завершения операции необходимо вызвать **склкомплетеасинк** .|  
  
## <a name="comments"></a>Комментарии  
 Маркеры параметров нумеруются в порядке возрастания порядка параметров, начиная с 1, в порядке их появления в инструкции SQL.  
  
 **SQLDescribeParam** не возвращает тип (ввод, ввод, выход или выход) параметра в инструкции SQL. За исключением вызовов процедур, все параметры в инструкциях SQL являются входными параметрами. Чтобы определить тип каждого параметра в вызове процедуры, приложение вызывает **SQLProcedureColumns**.  
  
 Дополнительные сведения см. в разделе [Описание параметров](../../../odbc/reference/develop-app/describing-parameters.md).  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере пользователю предлагается ввести инструкцию SQL, а затем подготовить эту инструкцию. Затем он вызывает **SQLNumParams** , чтобы определить, содержит ли инструкция какие бы то ни было параметры. Если инструкция содержит параметры, она вызывает **SQLDescribeParam** для описания этих параметров и **SQLBindParameter** для их привязки. Наконец, он запрашивает у пользователя значения всех параметров, а затем выполняет инструкцию.  
  
```cpp  
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
|Привязка буфера к параметру|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Исполнение подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Подготовка инструкции к выполнению|[Функция SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
