---
title: "Извлечение параметров вывода с помощью SQLGetData | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetData function [ODBC], retrieving output parameters
- output parameters [ODBC]
- retrieving output parameters [ODBC]
ms.assetid: 7a8c298a-2160-491d-a300-d36f45568d9c
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c1c4c3a857436f9b66d5aed447a6d5b47d59915a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Извлечение параметров вывода с помощью SQLGetData
Перед ODBC 3.8 приложения только удалось получить выходные параметры запроса с привязанного выходного буфера. Однако трудно выделять очень большой буфер, если размер значения параметра очень большой (например, крупное изображение). ODBC 3.8 вводит новый способ получить выходные параметры в части. Теперь можно вызвать приложение **SQLGetData** с небольшим буфером несколько раз, чтобы получить значения параметра большого объема. Это похоже на извлечение больших столбцов данных.  
  
 Чтобы привязать выходной параметр или параметр ввода вывода для получения в части, вызовите **SQLBindParameter** с *InputOutputType* аргументу присвоено SQL_PARAM_OUTPUT_STREAM или SQL_PARAM_INPUT_OUTPUT _STREAM. С SQL_PARAM_INPUT_OUTPUT_STREAM, приложение может использовать **SQLPutData** входные данные в качестве параметра, а затем использовать **SQLGetData** для получения выходного параметра. Входные данные должны быть в данных времени выполнения (DAE) форме с помощью **SQLPutData** вместо привязки к заранее выделенном буфере.  
  
 Эта функция может использоваться в приложениях ODBC 3.8 или повторно ODBC 3.x и ODBC 2.x этих приложений и должен иметь драйвер ODBC 3.8, который поддерживает получение выходных параметров с помощью **SQLGetData** и драйвер ODBC 3.8 Диспетчер. Сведения о том, как включить более старые приложения для использования новых функций ODBC см. в разделе [Матрица совместимости](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
## <a name="usage-example"></a>Пример использования  
 Например, рассмотрим выполнение хранимой процедуры **{ВЫЗОВ sp_f(?,?)} **, где оба параметра привязаны как SQL_PARAM_OUTPUT_STREAM и хранимая процедура не возвращает результирующего набора (Далее в этом разделе вы найдете более сложных сценариях):  
  
1.  Для каждого параметра вызова **SQLBindParameter** с *InputOutputType* значение SQL_PARAM_OUTPUT_STREAM и *ParameterValuePtr* значение маркера, например номер параметра , указатель на данные или указатель на структуру, которую использует приложение для привязки входных параметров. В этом примере будет использовать порядковый номер параметра в качестве маркера.  
  
2.  Выполнение запроса с **SQLExecDirect** или **SQLExecute**. Будут возвращены SQL_PARAM_DATA_AVAILABLE, о наличии доступными для получения потоковых выходных параметров.  
  
3.  Вызовите **SQLParamData** необходимо получить параметры, доступные для загрузки. **SQLParamData** вернет SQL_PARAM_DATA_AVAILABLE с маркером первый доступный параметр, установленного в **SQLBindParameter** (шаг 1). Маркер возвращается в буфере, *ValuePtrPtr* указывает.  
  
4.  Вызовите **SQLGetData** с аргументом *Col*_or\_*Param_Num* значение параметра порядковый номер для получения данных первый доступный параметр. Если **SQLGetData** возвращает SQL_SUCCESS_WITH_INFO и SQLState 01004 (данных) и тип переменной длины на клиенте и сервере, больше данных, извлекаемых из доступных первого параметра. Можно продолжать вызывать **SQLGetData** пока возвращается значение SQL_SUCCESS или SQL_SUCCESS_WITH_INFO с другим **SQLState**.  
  
5.  Повторите шаги 3 и 4, чтобы получить текущий параметр.  
  
6.  Вызовите **SQLParamData** еще раз. Если он возвращает либо, кроме SQL_PARAM_DATA_AVAILABLE, больше нет потоковых данных параметра для получения и код возврата будет следующая инструкция, которая выполняется код возврата.  
  
7.  Вызовите **SQLMoreResults** на обработку следующего набора параметров, пока не будет возвращено значение SQL_NO_DATA. **SQLMoreResults** вернет значение SQL_NO_DATA в этом примере, если атрибут инструкции SQL_ATTR_PARAMSET_SIZE было задано значение 1. В противном случае **SQLMoreResults** вернет SQL_PARAM_DATA_AVAILABLE, чтобы указать, что нет доступных для следующего набора параметров для получения потоковых выходных параметров.  
  
 Аналогично входному параметру DAE, маркер, используемый в аргументе *ParameterValuePtr* в **SQLBindParameter** (этап 1) может быть указатель на структуру данных приложения, который содержит Порядковый номер параметра и Дополнительные сведения о приложении, при необходимости.  
  
 Порядок потоковые данные, возвращенные или входных/выходных параметров конкретного драйвера и может не всегда быть таким же, как в порядке, указанном в запросе.  
  
 Если приложение не вызывает **SQLGetData** на шаге 4, значение параметра не учитывается. Аналогично Если приложение вызывает **SQLParamData** перед всеми параметра значение считанные **SQLGetData**, остальная часть значение удаляется и приложение может обрабатывать следующего параметр.  
  
 Если приложение вызывает **SQLMoreResults** перед все выходные потоковые данные обрабатываются параметры (**SQLParamData** по-прежнему возвращать SQL_PARAM_DATA_AVAILABLE), все остальные параметры не учитываются. Аналогично Если приложение вызывает **SQLMoreResults** перед всеми параметра значение считанные **SQLGetData**, остальная часть значения и все остальные параметры не учитываются и приложение может продолжать обработку следующего набора параметров.  
  
 Обратите внимание, что приложение может указать тип данных C в обоих **SQLBindParameter** и **SQLGetData**. Тип данных C, указанный с **SQLGetData** переопределения типа данных C в **SQLBindParameter**, если не указан тип данных C в **SQLGetData** — SQL_APD_TYPE.  
  
 Хотя потокового выходной параметр более полезно, когда тип данных выходного параметра типа больших двоичных ОБЪЕКТОВ, эта функция также может использоваться с любым типом данных. Типы данных, поддерживаемые потоковой выходные параметры задаются в драйвере.  
  
 При наличии параметров SQL_PARAM_INPUT_OUTPUT_STREAM обрабатываемого **SQLExecute** или **SQLExecDirect** сначала будет возвращено значение SQL_NEED_DATA. Приложение может вызвать **SQLParamData** и **SQLPutData** для отправки данных DAE параметра. При обработке всех входных параметров DAE **SQLParamData** возвращает SQL_PARAM_DATA_AVAILABLE цветом потоковых выходных параметров.  
  
 Когда передаются потоком выходные параметры и связанные выходные параметры должны быть обработаны, драйвер определяет порядок их обработке выходных параметров. Таким образом, если выходной параметр привязан к буфера ( **SQLBindParameter** параметр *InputOutputType* SQL_PARAM_INPUT_OUTPUT или SQL_PARAM_OUTPUT), буфер не могут быть заполнены до ** SQLParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO. Приложения следует прочитать границы буфера только после **SQLParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, которое загружается после того как все выходные параметры обрабатываются.  
  
 Источник данных может возвращать, предупреждение и результирующий набор, дополнительно потокового выходного параметра. Как правило, предупреждения и результирующие наборы обрабатываются отдельно из параметра потоковые выходные данные путем вызова **SQLMoreResults**. Обрабатывать предупреждения и результирующий набор до обработки потоковой выходного параметра.  
  
 Ниже перечислены различные сценарии одной команды, отправляемые сервером и работе приложения.  
  
|Сценарий|Возвращаемое значение SQLExecute или SQLExecDirect|Что делать дальше|  
|--------------|---------------------------------------------------|---------------------|  
|Данные содержат только потоковых выходных параметров|SQL_PARAM_DATA_AVAILABLE|Используйте **SQLParamData** и **SQLGetData** для получения потоковых выходных параметров.|  
|Результирующий набор включает данные и потоковых выходных параметров|SQL_SUCCESS|Получение результирующего набора с **SQLBindCol** и **SQLGetData**.<br /><br /> Вызовите **SQLMoreResults** должна начинаться обработка потоковых выходных параметров. Она должна возвращать SQL_PARAM_DATA_AVAILABLE.<br /><br /> Используйте **SQLParamData** и **SQLGetData** для получения потоковых выходных параметров.|  
|Данные, включает в себя предупреждающее сообщение и потоковых выходных параметров|SQL_SUCCESS_WITH_INFO|Используйте **SQLGetDiagRec** и **SQLGetDiagField** для обработки сообщений предупреждение.<br /><br /> Вызовите **SQLMoreResults** должна начинаться обработка потоковых выходных параметров. Она должна возвращать SQL_PARAM_DATA_AVAILABLE.<br /><br /> Используйте **SQLParamData** и **SQLGetData** для получения потоковых выходных параметров.|  
|Данные включают предупреждающее сообщение, результирующего набора и потоковых выходных параметров|SQL_SUCCESS_WITH_INFO|Используйте **SQLGetDiagRec** и **SQLGetDiagField** для обработки сообщений предупреждение. Затем вызовите **SQLMoreResults** запуск обработке результирующего набора.<br /><br /> Получить результирующий набор с **SQLBindCol** и **SQLGetData**.<br /><br /> Вызовите **SQLMoreResults** должна начинаться обработка потоковых выходных параметров. **SQLMoreResults** должен возвращать SQL_PARAM_DATA_AVAILABLE.<br /><br /> Используйте **SQLParamData** и **SQLGetData** для получения потоковых выходных параметров.|  
|DAE входными параметрами, например, потокового ввода вывода (DAE) параметр запроса|SQL NEED_DATA|Вызовите **SQLParamData** и **SQLPutData** для отправки DAE входные данные параметра.<br /><br /> После обработки всех входных параметров DAE **SQLParamData** может возвратить любой код возврата, **SQLExecute** и **SQLExecDirect** может возвращать. Затем можно применять в этой таблице случаи.<br /><br /> Если код возврата SQL_PARAM_DATA_AVAILABLE, доступны потоковых выходных параметров. Приложение должно вызвать **SQLParamData** еще раз, чтобы получить маркер для потокового выходного параметра, как описано в первой строке этой таблицы.<br /><br /> Если код возврата SQL_SUCCESS, отсутствует результирующий набор для обработки или обработка завершена.<br /><br /> Если код возврата SQL_SUCCESS_WITH_INFO, существуют предупреждающие сообщения для обработки.|  
  
 После **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** приведет к возвращает SQL_PARAM_DATA_AVAILABLE ошибка последовательности функций, если приложение вызывает функцию функция, которая не находится в следующем списке:  
  
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
  
-   **SQLFreeStmt** (параметр = SQL_CLOSE, SQL_DROP или SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **SQLDisconnect**  
  
-   **SQLFreeHandle** (HandleType = значение SQL_HANDLE_STMT)  
  
-   **SQLGetStmtAttr**  
  
 Приложения могут по-прежнему использовать **SQLSetDescField** или **SQLSetDescRec** для задания информации о привязке. Сопоставление поля не будут изменены. Однако поля внутри дескриптора может возвращать новые значения. Например SQL_DESC_PARAMETER_TYPE может возвращать SQL_PARAM_INPUT_OUTPUT_STREAM или SQL_PARAM_OUTPUT_STREAM.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Сценарии использования: Извлечение изображения в частях из результирующего набора  
 **SQLGetData** может использоваться для получения данных из частей, когда хранимая процедура возвращает результирующий набор, содержащий одной строки метаданных об образе, а изображение возвращается в больших выходной параметр.  
  
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
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Сценарии использования: Отправки и получения большого объекта как параметра потокового ввода вывода  
 **SQLGetData** может использоваться для получения и отправки данных в части, когда хранимая процедура передает больших объектов в виде параметра ввода вывода, потоковая передача значение к и из базы данных. Необходимо хранить все данные в памяти.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Параметры инструкции](../../../odbc/reference/develop-app/statement-parameters.md)

