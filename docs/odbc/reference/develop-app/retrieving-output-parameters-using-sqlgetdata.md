---
title: Получение выходных параметров с помощью метода SQLGetData | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], retrieving output parameters
- output parameters [ODBC]
- retrieving output parameters [ODBC]
ms.assetid: 7a8c298a-2160-491d-a300-d36f45568d9c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eeb8fae9c563e675499dec47839acdd0a003765a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020512"
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Получение выходных параметров с помощью метода SQLGetData
Перед ODBC 3.8 приложение может только получить выходные параметры запроса с помощью буфера привязанного выходные данные. Тем не менее трудно выделить очень большой буфер, если размер значения параметра очень велико (например, большое изображение). ODBC 3.8 представляет собой новый метод для извлечения выходных параметров в частях. Теперь можно вызвать приложение **SQLGetData** с небольшим буфером несколько раз, чтобы извлечь значение параметра большого объема. Это похоже на получение столбца большого объема данных.  
  
 Чтобы привязать выходной параметр или параметр ввода вывода для получения в части, вызовите **SQLBindParameter** с *InputOutputType* аргумент значение SQL_PARAM_OUTPUT_STREAM и SQL_PARAM_INPUT_OUTPUT _STREAM. С помощью SQL_PARAM_INPUT_OUTPUT_STREAM, приложение может использовать **SQLPutData** входные данные в качестве параметра, а затем использовать **SQLGetData** для получения выходного параметра. Входные данные должны быть в данных времени выполнения (DAE) форме с помощью **SQLPutData** вместо привязки к предварительно буфера.  
  
 Эта функция может использоваться в приложениях ODBC 3.8 или перекомпиляции ODBC 3.x и ODBC 2.x этих приложений и должен иметь драйвером ODBC 3.8, которая поддерживает извлечение параметров вывода, с помощью **SQLGetData** и драйвер ODBC 3.8 Диспетчер. Сведения о включении старое приложение для использования новых функций ODBC, см. в разделе [Матрица совместимости](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
## <a name="usage-example"></a>Пример использования  
 Например, рассмотрим выполнение хранимой процедуры, **{ВЫЗОВ sp_f(?,?)}** , где оба параметра связываются как SQL_PARAM_OUTPUT_STREAM и хранимая процедура не возвращает результирующего набора (Далее в этом разделе вы найдете более сложный сценарий):  
  
1.  Для каждого параметра вызова **SQLBindParameter** с *InputOutputType* присвоено SQL_PARAM_OUTPUT_STREAM и *ParameterValuePtr* присвоено маркер, например номер параметра , указатель на данные, или на указатель на структуру, приложение использует для привязки входных параметров. В этом примере будет использовать порядковый номер параметра в качестве маркера.  
  
2.  Выполнение запроса с **SQLExecDirect** или **SQLExecute**. SQL_PARAM_DATA_AVAILABLE будет возвращаться, о наличии доступных для получения потоковых выходных параметров.  
  
3.  Вызовите **SQLParamData** получить параметр, который является недоступным для извлечения. **SQLParamData** вернет SQL_PARAM_DATA_AVAILABLE с токеном первый доступный параметр, который установлен в **SQLBindParameter** (шаг 1). Токен возвращается в буфере, *ValuePtrPtr* указывает.  
  
4.  Вызовите **SQLGetData** с аргументом *Col*_or\_*Param_Num* значение параметра порядковый номер для получения данных из первого параметра. Если **SQLGetData** возвращает SQL_SUCCESS_WITH_INFO и SQLState 01004 (данных) и тип переменной длины на клиенте и сервере, то больше данных, извлекаемых из первого параметра доступны. Можно продолжать вызывать **SQLGetData** пока не будет возвращено значение SQL_SUCCESS или SQL_SUCCESS_WITH_INFO с другим **SQLState**.  
  
5.  Повторите шаги 3 и 4, чтобы получить текущий параметр.  
  
6.  Вызовите **SQLParamData** еще раз. Если он возвращает какой-либо кроме SQL_PARAM_DATA_AVAILABLE, больше нет потоковых данных параметра для извлечения, и код возврата будет код возврата следующий оператор, который выполняется.  
  
7.  Вызовите **SQLMoreResults** обработать следующий набор параметров, пока не будет возвращено значение SQL_NO_DATA. **SQLMoreResults** вернет значение SQL_NO_DATA в этом примере, если атрибут инструкции SQL_ATTR_PARAMSET_SIZE равным 1. В противном случае **SQLMoreResults** вернет SQL_PARAM_DATA_AVAILABLE, чтобы указать, что существуют для следующего набора параметров для получения потоковых выходных параметров.  
  
 Аналогично входному параметру DAE, токен, используемый в аргументе *ParameterValuePtr* в **SQLBindParameter** (шаг 1) может быть указатель на структуру данных приложения, который содержит Порядковый номер параметра и Дополнительные сведения о приложении, при необходимости.  
  
 Порядок возвращаемых потоковых данных или входных и выходных параметров конкретного драйвера и может не всегда быть таким же, как order, заданному в запросе.  
  
 Если приложение не вызывает **SQLGetData** на шаге 4, значение параметра не учитывается. Аналогично Если приложение вызывает **SQLParamData** перед всеми параметра значение уже прочитал **SQLGetData**, остальная часть значение отклоняется и приложение может обработать следующий параметр.  
  
 Если приложение вызывает **SQLMoreResults** перед все выходные потоковые данные обрабатываются параметры (**SQLParamData** по-прежнему возвращать SQL_PARAM_DATA_AVAILABLE), удаляются все остальные параметры. Аналогично Если приложение вызывает **SQLMoreResults** перед всеми параметра значение уже прочитал **SQLGetData**, остальная часть значение и все остальные параметры, удаляются и приложение может продолжать обработку следующего набора параметров.  
  
 Обратите внимание, что приложение может указать тип данных C в обоих **SQLBindParameter** и **SQLGetData**. Тип данных C, указанный с помощью **SQLGetData** переопределяет тип данных C, указанный в **SQLBindParameter**, если не указан тип данных C в **SQLGetData** является SQL_APD_TYPE.  
  
 Несмотря на то, что параметр потоковые выходные данные является более полезной, если выбран тип данных выходного параметра типа BLOB-ОБЪЕКТОВ, эта функция может также использоваться с любым типом данных. Типы данных, поддерживаемые потоковой выходные параметры указываются в драйвере.  
  
 Если параметров SQL_PARAM_INPUT_OUTPUT_STREAM обрабатываемого **SQLExecute** или **SQLExecDirect** сначала будет возвращено значение SQL_NEED_DATA. Приложение может вызвать **SQLParamData** и **SQLPutData** для отправки данных параметр DAE. Если обрабатываются все входные параметры DAE, **SQLParamData** возвращает SQL_PARAM_DATA_AVAILABLE цветом потоковых выходных параметров.  
  
 При передаются потоком выходные параметры и связанные выходные параметры должны быть обработаны, драйвер определяет порядок обработки выходных параметров. Таким образом, если выходной параметр привязан к буфер ( **SQLBindParameter** параметр *InputOutputType* SQL_PARAM_INPUT_OUTPUT или SQL_PARAM_OUTPUT), буфер не могут быть заполнены до  **SQLParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO. Приложения должны считывать связанного буфера только после того, как **SQLParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, которое загружается в конце концов выходные параметры обрабатываются.  
  
 Источник данных может возвращать, что предупреждение и результат, кроме параметра потокового вывода. Как правило, предупреждения и результирующие наборы обрабатываются отдельно от параметра потоковые выходные данные путем вызова **SQLMoreResults**. Обработка предупреждений и результирующий набор, перед обработкой потоковых выходной параметр.  
  
 Ниже перечислены различные варианты одной команды отправляются на сервер, и как должна работать приложение.  
  
|Сценарий|Возвращаемое значение из SQLExecute или SQLExecDirect|Что делать дальше|  
|--------------|---------------------------------------------------|---------------------|  
|Данные включают только потоковых выходных параметров|SQL_PARAM_DATA_AVAILABLE|Используйте **SQLParamData** и **SQLGetData** для получения потоковых выходных параметров.|  
|Включает в себя результирующий набор данных и потоковых выходных параметров|SQL_SUCCESS|Получить результирующий набор с **SQLBindCol** и **SQLGetData**.<br /><br /> Вызовите **SQLMoreResults** для запуска обработки потоковых выходных параметров. Она должна возвращать SQL_PARAM_DATA_AVAILABLE.<br /><br /> Используйте **SQLParamData** и **SQLGetData** для получения потоковых выходных параметров.|  
|Данные, включает предупреждение и потоковых выходных параметров|SQL_SUCCESS_WITH_INFO|Используйте **SQLGetDiagRec** и **SQLGetDiagField** для обработки сообщений предупреждение.<br /><br /> Вызовите **SQLMoreResults** для запуска обработки потоковых выходных параметров. Она должна возвращать SQL_PARAM_DATA_AVAILABLE.<br /><br /> Используйте **SQLParamData** и **SQLGetData** для получения потоковых выходных параметров.|  
|Данные включают в себя предупреждающее сообщение, результирующего набора и потоковых выходных параметров|SQL_SUCCESS_WITH_INFO|Используйте **SQLGetDiagRec** и **SQLGetDiagField** для обработки сообщений предупреждение. Затем вызовите **SQLMoreResults** чтобы начать, обработке результирующего набора.<br /><br /> Извлечения результирующего набора с **SQLBindCol** и **SQLGetData**.<br /><br /> Вызовите **SQLMoreResults** для запуска обработки потоковых выходных параметров. **SQLMoreResults** должен возвращать SQL_PARAM_DATA_AVAILABLE.<br /><br /> Используйте **SQLParamData** и **SQLGetData** для получения потоковых выходных параметров.|  
|DAE входными параметрами, например, потокового ввода вывода (DAE) параметр запроса|SQL NEED_DATA|Вызовите **SQLParamData** и **SQLPutData** для отправки DAE входные данные параметра.<br /><br /> После обработки всех входных параметров DAE **SQLParamData** может возвращать любой код возврата, **SQLExecute** и **SQLExecDirect** может возвращать. Затем можно применить варианты в этой таблице.<br /><br /> Если возвращается значение SQL_PARAM_DATA_AVAILABLE, потоковых выходных параметров будут доступны. Приложение должно вызвать **SQLParamData** еще раз, чтобы получить маркер для параметра потокового вывода, как описано в первой строке этой таблицы.<br /><br /> Если возвращается значение SQL_SUCCESS, либо результирующего набора для обработки или обработка завершена.<br /><br /> Если код возврата SQL_SUCCESS_WITH_INFO, существуют предупреждающие сообщения для обработки.|  
  
 После **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** возвращает SQL_PARAM_DATA_AVAILABLE, ошибка последовательности функций происходит в том случае, если приложение вызывает функцию функция, которая не находится в списке ниже:  
  
-   **SQLAllocHandle** / **SQLAllocHandleStd**  
  
-   **SQLDataSources** / **SQLDrivers**  
  
-   **SQLGetInfo** / **SQLGetFunctions**  
  
-   **SQLGetConnectAttr** / **SQLGetEnvAttr** / **SQLGetDescField** / **SQLGetDescRec**  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **SQLGetDiagField** / **SQLGetDiagRec**  
  
-   **SQLCancel**  
  
-   **SQLCancelHandle** (с дескриптором инструкции)  
  
-   **SQLFreeStmt** (с параметром = SQL_CLOSE, SQL_DROP или SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **SQLDisconnect**  
  
-   **SQLFreeHandle** (HandleType = значение SQL_HANDLE_STMT)  
  
-   **SQLGetStmtAttr**  
  
 Приложения могут по-прежнему использовать **SQLSetDescField** или **SQLSetDescRec** задать сведения о привязке. Поле сопоставления не изменится. Однако поля внутри дескриптора может возвращать новые значения. Например SQL_DESC_PARAMETER_TYPE может возвращать SQL_PARAM_INPUT_OUTPUT_STREAM или SQL_PARAM_OUTPUT_STREAM.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Сценарий использования: Получить изображение из частей из результирующего набора  
 **SQLGetData** может использоваться для получения данных в части, когда хранимая процедура возвращает результирующий набор, содержащий одной строки метаданных об образе и изображение возвращается в параметре больших выходных данных.  
  
```  
// CREATE PROCEDURE SP_TestOutputPara  
//      @ID_of_picture   as int,  
//      @Picture         as varbinary(max) out  
// AS  
//     output the image data through streamed output parameter  
// GO  
BOOL displayPicture(SQLUINTEGER idOfPicture, SQLHSTMT hstmt) {  
   SQLLEN      lengthOfPicture;    // The actual length of the picture.  
   BYTE        smallBuffer[100];   // A very small buffer.  
   SQLRETURN   retcode, retcode2;  
  
   // Bind the first parameter (input parameter)  
   SQLBindParameter(  
         hstmt,  
         1,                         // The first parameter.   
         SQL_PARAM_INPUT,           // Input parameter: The ID_of_picture.  
         SQL_C_ULONG,               // The C Data Type.  
         SQL_INTEGER,               // The SQL Data Type.  
         0,                         // ColumnSize is ignored for integer.  
         0,                         // DecimalDigits is ignored for integer.  
         &idOfPicture,              // The Address of the buffer for the input parameter.  
         0,                         // BufferLength is ignored for integer.  
         NULL);                     // This is ignored for integer.  
  
   // Bind the streamed output parameter.  
   SQLBindParameter(  
         hstmt,   
         2,                         // The second parameter.  
         SQL_PARAM_OUTPUT_STREAM,   // A streamed output parameter.   
         SQL_C_BINARY,              // The C Data Type.    
         SQL_VARBINARY,             // The SQL Data Type.  
         0,                         // ColumnSize: The maximum size of varbinary(max).  
         0,                         // DecimalDigits is ignored for binary type.  
         (SQLPOINTER)2,             // ParameterValuePtr: An application-defined  
                                    // token (this will be returned from SQLParamData).  
                                    // In this example, we used the ordinal   
                                    // of the parameter.  
         0,                         // BufferLength is ignored for streamed output parameters.  
         &lengthOfPicture);         // StrLen_or_IndPtr: The status variable returned.   
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestOutputPara(?, ?)}", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Assume that the retrieved picture exists.  Use SQLBindCol or SQLGetData to retrieve the result-set.  
  
   // Process the result set and move to the streamed output parameters.  
   retcode = SQLMoreResults( hstmt );  
  
   // SQLGetData retrieves and displays the picture in parts.  
   // The streamed output parameter is available.  
   while (retcode == SQL_PARAM_DATA_AVAILABLE) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;      // #bytes remained  
      retcode = SQLParamData(hstmt, &token);   // returned token is 2 (according to the binding)  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         // A do-while loop retrieves the picture in parts.  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }  
  
   return TRUE;  
}  
```  
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Сценарий использования: Отправка и получение больших объектов как параметр потокового ввода вывода  
 **SQLGetData** может использоваться для получения и отправки данных в части, когда хранимая процедура передает большой объект как параметр ввода вывода, потоковая передача значения к и из базы данных. Вам не требуется хранить все данные в памяти.  
  
```  
// CREATE PROCEDURE SP_TestInOut  
//       @picture as varbinary(max) out  
// AS  
//    output the image data through output parameter   
// go  
  
BOOL displaySimilarPicture(BYTE* image, ULONG lengthOfImage, SQLHSTMT hstmt) {  
   BYTE smallBuffer[100];   // A very small buffer.  
   SQLRETURN retcode, retcode2;  
   SQLLEN statusOfPicture;  
  
   // First bind the parameters, before preparing the statement that binds the output streamed parameter.  
   SQLBindParameter(  
      hstmt,   
      1,                                 // The first parameter.  
      SQL_PARAM_INPUT_OUTPUT_STREAM,     // I/O-streamed parameter: The Picture.  
      SQL_C_BINARY,                      // The C Data Type.  
      SQL_VARBINARY,                     // The SQL Data Type.  
      0,                                 // ColumnSize: The maximum size of varbinary(max).  
      0,                                 // DecimalDigits is ignored.   
      (SQLPOINTER)1,                     // An application defined token.   
      0,                                 // BufferLength is ignored for streamed I/O parameters.  
      &statusOfPicture);                 // The status variable.  
  
   statusOfPicture = SQL_DATA_AT_EXEC;   // Input data in parts (DAE parameter at input).  
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestInOut(?) }", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Execute the statement.  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   if ( retcode == SQL_NEED_DATA ) {  
      // Use SQLParamData to loop through DAE input parameters.  For  
      // each, use SQLPutData to send the data to database in parts.  
  
      // This example uses an I/O parameter with streamed output.  
      // Therefore, the last call to SQLParamData should return  
      // SQL_PARAM_DATA_AVAILABLE to indicate the end of the input phrase   
      // and report that a streamed output parameter is available.  
  
      // Assume retcode is set to the return value of the last call to  
      // SQLParamData, which is equal to SQL_PARAM_DATA_AVAILABLE.  
   }  
  
   // Start processing the streamed output parameters.  
   while ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;     // #bytes remained  
      retcode = SQLParamData(hstmt, &token);  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }   
  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры инструкции](../../../odbc/reference/develop-app/statement-parameters.md)
