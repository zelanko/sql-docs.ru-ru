---
title: Получение параметров вывода с помощью S'LGetData (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c96a3f9fc81d081ce16fe8e75746aafe8962fd0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294594"
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Получение выходных параметров с помощью метода SQLGetData
До ODBC 3.8 приложение могло получить только параметры вывода запроса с пересохшным буфером вывода. Однако трудно выделить очень большой буфер, когда размер значения параметра очень большой (например, большое изображение). ODBC 3.8 вводит новый способ получения параметров вывода по частям. Теперь приложение может вызывать **S'LGetData** с небольшим буфером несколько раз, чтобы получить большое значение параметра. Это похоже на получение данных больших столбцов.  
  
 Чтобы связать параметр вывода или входним/выходным параметром, которые будут извлечены по частям, позвоните в **S'LBindParameter** с аргументом *InputOutputType,* установленным для SQL_PARAM_OUTPUT_STREAM или SQL_PARAM_INPUT_OUTPUT_STREAM. С SQL_PARAM_INPUT_OUTPUT_STREAM приложение может использовать **S'LPutData** для ввода данных в параметр, а затем использовать **S'LGetData** для получения параметра вывода. Входные данные должны быть в форме data-at-execution (DAE), используя **вместо** того, чтобы связывать их с заранее распределенным буфером.  
  
 Эта функция может быть использована приложениями ODBC 3.8 или перекомпилированными приложениями ODBC 3.x и ODBC 2.x, и эти приложения должны иметь драйвер ODBC 3.8, который поддерживает получение параметров вывода с помощью **S'LGetData** и ODBC 3.8 Driver Manager. Для получения информации о том, как включить старое приложение для использования новых функций ODBC, [см.](../../../odbc/reference/develop-app/compatibility-matrix.md)  
  
## <a name="usage-example"></a>Пример использования  
 Например, рассмотрите выполнение сохраненной **процедуры, «CALL sp_f(?,?)»,** где оба параметра связаны как SQL_PARAM_OUTPUT_STREAM, и сохраненная процедура не возвращает набор результатов (позже в этой теме вы найдете более сложный сценарий):  
  
1.  Для каждого параметра позвоните по **вызову S'LBindParameter** с *помощью InputOutputType,* установленного для SQL_PARAM_OUTPUT_STREAM и *ParameterValuePtr,* установленного на токен, таких как номер параметра, указатель на данные или указатель на структуру, которую приложение использует для связывания входных параметров. Этот пример будет использовать параметры, обычно еле в качестве маркера.  
  
2.  Выполняйте запрос с **помощью S'LExecDirect** или **S'LExecute**. SQL_PARAM_DATA_AVAILABLE будет возвращено, что указывает на наличие streamed output параметров для поиска.  
  
3.  Позвоните **в S'LParamData,** чтобы получить параметр, который доступен для поиска. **SLParamData** вернется SQL_PARAM_DATA_AVAILABLE с токеном первого доступного параметра, который установлен в **S'LBindParameter** (шаг 1). Токен возвращается в буфер, на который указывает *ValuePtrPtr.*  
  
4.  Позвоните **в S'LGetData** с аргументом *Col*_or\_*Param_Num* установлен на параметр, предусмотражаемый для получения данных первого доступного параметра. Если **S'LGetData** возвращает SQL_SUCCESS_WITH_INFO и S'LState 01004 (данные усечены), а тип имеет переменную длину как на клиенте, так и на сервере, то есть больше данных для получения из первого доступного параметра. Вы можете продолжать звонить по **вызову S'LGetData** до тех пор, пока она не вернется SQL_SUCCESS или SQL_SUCCESS_WITH_INFO с другим **s'LState**.  
  
5.  Повторите шаг 3 и шаг 4 для получения текущего параметра.  
  
6.  Позвоните **в S'LParamData** еще раз. Если он возвращает что-либо, кроме SQL_PARAM_DATA_AVAILABLE, больше нет потоковых данных параметра для извлечения, и код возврата будет кодом возврата следующего оператора, который выполняется.  
  
7.  Позвоните **в S'LMoreResults,** чтобы обработать следующий набор параметров до тех пор, пока он не вернется SQL_NO_DATA. **В** этом примере SQL_NO_DATA, если атрибут SQL_ATTR_PARAMSET_SIZE оператора был установлен до 1. В противном случае, **S'LMoreResults** вернется SQL_PARAM_DATA_AVAILABLE, чтобы указать, что есть потоковые параметры вывода, доступные для следующего набора параметров для извлечения.  
  
 Подобно параметру ввода DAE, токен, используемый в аргументе *ParameterValuePtr* в **S'LBindParameter** (шаг 1), может быть указателем, который указывает на структуру данных приложения, которая содержит обыденную параметр и более конкретную информацию, если это необходимо.  
  
 Порядок возвращенных потоковых выходных или параметров ввода/вывода является конкретным драйвером и не всегда может быть таким же, как порядок, указанный в запросе.  
  
 Если приложение не вызывает **S'LGetData** в шаге 4, значение параметра отбрасывается. Аналогичным образом, если приложение вызывает **S'LParamData** до того, как все значение параметра будет прочитано **S'LGetData,** остальная часть значения отбрасывается, и приложение может обработать следующий параметр.  
  
 Если приложение вызывает **S'LMoreResults** до того, как будут обработаны все потоковые параметры вывода **(S'LParamData** все еще возвращается SQL_PARAM_DATA_AVAILABLE), все остальные параметры отбрасываются. Аналогичным образом, если приложение вызывает **S'LMoreResults** до того, как все параметрное значение будет прочитано **S'LGetData,** остальная часть значения и все остальные параметры отбрасываются, и приложение может продолжить обработку следующего набора параметров.  
  
 Обратите внимание, что приложение может указать тип данных C как в **S'LBindParameter,** так и в **S'LGetData.** Тип данных C, указанный в **S'LGetData,** переопределяет тип данных C, указанный в **S'LBindParameter,** если тип данных C, указанный в **S'LGetData,** не является SQL_APD_TYPE.  
  
 Хотя потоковой параметр вывода является более полезным, когда тип данных параметра вывода является типом BLOB, эта функциональность также может быть использована с любым типом данных. Типы данных, поддерживаемые streamed параметрами вывода, указаны в драйвере.  
  
 Если есть SQL_PARAM_INPUT_OUTPUT_STREAM параметров, которые должны быть обработаны, **S'LExecute** или **S'LExecDirect** вернется SQL_NEED_DATA в первую очередь. Для отправки данных параметра **SQLPutData** DAE приложение может вызывать **данные** о параметрах DAE. При обработке всех параметров ввода DAE, **SQL_PARAM_DATA_AVAILABLE,** указывающие на потоковые параметры вывода, доступны.  
  
 При обработке streamed output параметров и связанных параметров вывода драйвер определяет порядок для обработки параметров вывода. Таким образом, если параметр вывода привязан к буферу (параметр *InputOutputType* **s'LBindParameter** установлен на SQL_PARAM_INPUT_OUTPUT или SQL_PARAM_OUTPUT), буфер может быть не заселен до тех пор, пока **s'LParamData** не вернет SQL_SUCCESS или SQL_SUCCESS_WITH_INFO. Приложение должно прочитать связанный буфер только после того, как **s'LParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, то есть после обработки всех потоковых параметров вывода.  
  
 Источник данных может возвращать набор предупреждений и результатов, в дополнение к потоковому параметру вывода. В общем, предупреждения и наборы результатов обрабатываются отдельно от потокового параметра вывода, вызывая **S'LMoreResults.** Обработка предупреждений и результата, установленного перед обработкой streamed параметры вывода.  
  
 В следующей таблице описаны различные сценарии одной команды, отправленной на сервер, и как приложение должно работать.  
  
|Сценарий|Значение возврата от S'LExecute или S'LExecDirect|Дальнейшие действия|  
|--------------|---------------------------------------------------|---------------------|  
|Данные включают только streamed параметры вывода|SQL_PARAM_DATA_AVAILABLE|Для получения streamed параметров вывода используйте **S'LParamData** и **S'LGetData.**|  
|Данные включают набор результатов и streamed параметры вывода|SQL_SUCCESS|Извлеките набор результатов с **помощью S'LBindCol** и **S'LGetData**.<br /><br /> Вызов **S'LMoreResults,** чтобы начать обработку потоковых параметров вывода. Он должен вернуть SQL_PARAM_DATA_AVAILABLE.<br /><br /> Для получения streamed параметров вывода используйте **S'LParamData** и **S'LGetData.**|  
|Данные включают в себя предупреждающее сообщение и streamed параметры вывода|SQL_SUCCESS_WITH_INFO|Для обработки предупреждающих сообщений используйте **s'LGetDiagRec** и **S'LGetDiagField.**<br /><br /> Вызов **S'LMoreResults,** чтобы начать обработку потоковых параметров вывода. Он должен вернуть SQL_PARAM_DATA_AVAILABLE.<br /><br /> Для получения streamed параметров вывода используйте **S'LParamData** и **S'LGetData.**|  
|Данные включают в себя предупреждающее сообщение, набор результатов и streamed параметры вывода|SQL_SUCCESS_WITH_INFO|Для обработки предупреждающих сообщений используйте **s'LGetDiagRec** и **S'LGetDiagField.** Затем позвоните в **S'LMoreResults,** чтобы начать обработку набора результатов.<br /><br /> Извлекайте набор результатов с **помощью S'LBindCol** и **S'LGetData.**<br /><br /> Вызов **S'LMoreResults,** чтобы начать обработку потоковых параметров вывода. **S'LMoreResults** должен вернуться SQL_PARAM_DATA_AVAILABLE.<br /><br /> Для получения streamed параметров вывода используйте **S'LParamData** и **S'LGetData.**|  
|Запрос с параметрами ввода DAE, например, перетекаемый ввод/выход (DAE) параметр|NEED_DATA СЗЛ|Для отправки данных ввода параметров DAE для отправки данных ввода dAE позвоните в **S'LParamData** и **S'LPutData.**<br /><br /> После обработки всех параметров ввода DAE, **S'LParamData** может вернуть любой возвратный код, который могут **вернутьs S'LLExecute** и **S'LExecDirect.** Случаи в этой таблице могут быть применены.<br /><br /> Если код возврата SQL_PARAM_DATA_AVAILABLE, доступны streamed выходные параметры. Для получения токена для потокового параметра вывода, как описано в первом ряду этой таблицы, приложение должно снова вызвать **s'LParamData.**<br /><br /> Если код возврата SQL_SUCCESS, либо есть набор результатов для обработки или обработка завершена.<br /><br /> Если код возврата SQL_SUCCESS_WITH_INFO, необходимо обработать предупреждающие сообщения.|  
  
 После того, как **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** возвращается SQL_PARAM_DATA_AVAILABLE, ошибка последовательности функции приведет, если приложение вызывает функцию, которая не находится в следующем списке:  
  
-   **СЗЛАлокХейлс** / **СЗЛАлокХонг**  
  
-   **SLDataИсточники** / **СЗЛ**  
  
-   **СЗЛГетИнфо** / **СЗЛГетЕТФункциС**  
  
-   **СЗЛГетКоннЕТтТР** / **СЗЛГЕТЕнвтр** / **СЗЛГетдескФилд** / **СЗЛГетДескКрек**  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **СЗЛГЕДиАгФилд** / **СЗЛГетДиагРе**  
  
-   **SQLCancel**  
  
-   **S'LКансканхельстом** (с ручкой оператора)  
  
-   **СЗЛФреИстт** (с опцией SQL_CLOSE, SQL_DROP или SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **СЗЛДИСКоннект**  
  
-   **СЗЛФримбранг** (с HandleType и SQL_HANDLE_STMT)  
  
-   **SQLGetStmtAttr**  
  
 Приложения по-прежнему могут использовать **s'LSetDescField** или **S'LSetDescRec** для установки связывающей информации. Полевое картирование не будет изменено. Однако поля внутри дескриптора могут вернуть новые значения. Например, SQL_DESC_PARAMETER_TYPE может вернуться SQL_PARAM_INPUT_OUTPUT_STREAM или SQL_PARAM_OUTPUT_STREAM.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Сценарий использования: Извлечение изображения в частях из набора результатов  
 **Для** получения данных по частям можно использовать данные, когда сохраненная процедура возвращает набор результатов, содержащий один ряд метаданных об изображении и возвращается изображение в большой параметр вывода.  
  
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
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Сценарий использования: Отправка и получение крупного объекта в качестве streamed ввода /параметры вывода  
 **Для** получения и отправки данных по частям можно использовать данные по частям, когда сохраненная процедура проходит большой объект в качестве параметра ввода/вывода, потоковое значение в базу данных и из нее. Вам не нужно хранить все данные в памяти.  
  
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
