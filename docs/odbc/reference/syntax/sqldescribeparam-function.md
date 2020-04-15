---
title: Функция S'LDescribeParam (англ.) Документы Майкрософт
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
ms.openlocfilehash: be6d076ca121923a4b6769c7dad5269c3fd642ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301164"
---
# <a name="sqldescribeparam-function"></a>Функция SQLDescribeParam
**Соответствия**  
 Версия Введена: Соответствие стандартам ODBC 1.0: ODBC  
  
 **Сводка**  
 **SLDescribeParam** возвращает описание параметрического маркера, связанного с подготовленной выпиской s'L. Эта информация также доступна в полях IPD.  
  
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
  
## <a name="argument"></a>Аргумент  
 *Обработка заявления*  
 (Вход) Ручка оператора.  
  
 *ParameterНомер*  
 (Вход) Номер параметра, упорядоченный последовательно в увеличивающийся порядок параметра, начиная с 1.  
  
 *DataTypePtr*  
 (Выход) Указатель на буфер, в котором можно вернуть тип параметра данных S'L. Это значение считывается из SQL_DESC_CONCISE_TYPE области записи IPD. Это будет одно из значений в разделе [Типы данных в](../../../odbc/reference/appendixes/sql-data-types.md) приложении D: Типы данных, или тип данных, специфичный для драйверов.  
  
 В ODBC 3. *x,* SQL_TYPE_DATE, SQL_TYPE_TIME или SQL_TYPE_TIMESTAMP будут возвращены в * \*DataTypePtr* для данных даты, времени или метки времени, соответственно; в ODBC 2. *x,* SQL_DATE, SQL_TIME или SQL_TIMESTAMP будут возвращены. Менеджер драйвера выполняет необходимые отображения при ODBC 2. *приложение x* работает с ODBC 3. *x* драйвер или при ODBC 3. *приложение x* работает с ODBC 2. *x* драйвер.  
  
 Когда *ColumnNumber* равен 0 (для столбца закладки), SQL_BINARY возвращается в * \*DataTypePtr* для закладок с переменной длиной. (SQL_INTEGER возвращается, если закладки используются ODBC 3. *x* приложение работает с ODBC 2. *x* драйвер или ODBC 2. *x* приложение работает с ODBC 3. *x* водитель.)  
  
 Для получения более подробной информации в приложении D: Типы [данных см.](../../../odbc/reference/appendixes/sql-data-types.md) Для получения информации о типах данных, специфичных для драйверов, просмотрите документацию водителя.  
  
 *ParameterSizePtr*  
 (Выход) Указатель на буфер, в котором можно вернуть размер в символах столбца или выражение соответствующего параметра, определяемого источником данных. Для получения дополнительной информации о размере столбца см. [Размер столбца, десятичные цифры, длина переноса Octet и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *ДесятичнаяДияпТр*  
 (Выход) Указатель на буфер, в котором можно вернуть число десятичных цифр столбца или выражение соответствующего параметра, определяемого источником данных. Для получения дополнительной информации о десятичных цифрах [см. Размер столбца, десятичные цифры, длина передачи Octet и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md).  
  
 *NullablePtr*  
 (Выход) Указатель на буфер, в котором можно вернуть значение, указывавшее, позволяет ли параметр значенияnull. Это значение читается из SQL_DESC_NULLABLE области IPD. Это может быть:  
  
-   SQL_NO_NULLS: Параметр не позволяет значения NULL (это значение по умолчанию).  
  
-   SQL_NULLABLE: Параметр позволяет значения NULL.  
  
-   SQL_NULLABLE_UNKNOWN: Драйвер не может определить, позволяет ли параметр значения NULL.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LDescribeParam** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону s'LGetDiagRec** с *помощью SQL_HANDLE_STMT* и *ручки* *выписки.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LDescribeParam,** и приведены в изъяны каждое из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|07009|Недействительный индекс дескриптора|(DM) Значение, указанное для аргумента *ParameterNumber* меньше 1.<br /><br /> Значение, указанное для аргумента *ParameterNumber,* превышало количество параметров в связанном с этим отчете S'L.<br /><br /> Параметр был частью оператора, не относящийся к DML.<br /><br /> Параметр был частью списка **SELECT.**|  
|08S01|Сбой связи|Связь между драйвером и источником данных, к которому был подключен драйвер, не сработала до завершения обработки функции.|  
|21S01|Список значений вставки не соответствует списку столбцов|Количество параметров в заявлении **INSERT** не соответствовало числу столбцов в таблице, названной в заявлении.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхлик** был вызван на *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхливнейра** был вызван на *StatementHandle* из другого потока в многопоточном приложении.|  
|HY010|Ошибка последовательности функций|(DM) Функция была вызвана перед вызовом **S'LPrepare** или **S'LExecDirect** для *StatementHandle*.<br /><br /> (DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *StatementHandle.* Эта асинхронная функция по-прежнему исполнялась, когда была вызвана функция **S'LDescribeParam.**<br /><br /> (DM) Асинхронно выполнение функции (не этот) был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** был вызван для *statementHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
|IM017|Опрос отключен в асинхронном режиме уведомления|Всякий раз, когда используется модель уведомления, опрос отключается.|  
|IM018|Для завершения предыдущей асинхронной операции на этой ручке не был вызван **S'LCompleteAsync.**|Если предыдущий вызов функции на ручке возвращается SQL_STILL_EXECUTING и если режим уведомления включен, **s'LCompleteAsync** должен быть вызван на ручку, чтобы сделать пост-обработку и завершить операцию.|  
  
## <a name="comments"></a>Комментарии  
 Параметры маркеры пронумероваются в увеличивающийся порядок параметра, начиная с 1, в порядке, они появляются в выписке S'L.  
  
 В отчете **S'LDescribeParam** не возвращается тип (вход, вход/выход или выход) параметра. За исключением вызовов к процедурам, все параметры в инструкциях S'L являются входные параметры. Чтобы определить тип каждого параметра в вызове к процедуре, приложение вызывает **S'LProcedureColumns.**  
  
 Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/describing-parameters.md)  
  
## <a name="code-example"></a>Пример кода  
 Следующий пример подсказывает пользователю заявление S'L, а затем готовит это заявление. Далее он вызывает **S'LNumParams,** чтобы определить, содержит ли заявление какие-либо параметры. Если в отчете содержатся параметры, то для описания этих параметров он называет **s'LDescribeParam,** а **s'LBindParameter** — связать их. Наконец, он подсказывает пользователю значения любых параметров, а затем выполняет оператора.  
  
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
|Отмена обработки оператора|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выполнение подготовленного заявления по S'L|[Функция «СЗЛВы»](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Подготовка выписки для исполнения|[Функция SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
