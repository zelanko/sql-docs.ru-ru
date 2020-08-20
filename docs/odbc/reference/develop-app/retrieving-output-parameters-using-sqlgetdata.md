---
description: Получение выходных параметров с помощью метода SQLGetData
title: Получение выходных параметров с помощью SQLGetData | Документация Майкрософт
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
ms.openlocfilehash: a31cb6baa015e2a90977d0112e770ce66fa8e62f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461386"
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Получение выходных параметров с помощью метода SQLGetData
До ODBC 3,8 приложение может получить только выходные параметры запроса с привязанным выходным буфером. Однако очень сложно выделить очень большой буфер, если размер значения параметра очень большой (например, большое изображение). В ODBC 3,8 появился новый способ получения выходных параметров в частях. Приложение теперь может вызвать **SQLGetData** с небольшим буфером несколько раз, чтобы получить значение большого значения параметра. Это похоже на получение данных больших столбцов.  
  
 Чтобы привязать выходной параметр или входной/выходной параметр, который необходимо получить в частях, вызовите **SQLBindParameter** , указав для аргумента *инпутаутпуттипе* значение SQL_PARAM_OUTPUT_STREAM или SQL_PARAM_INPUT_OUTPUT_STREAM. С SQL_PARAM_INPUT_OUTPUT_STREAM приложение может использовать **SQLPutData** для ввода данных в параметр, а затем использовать **SQLGetData** для получения выходного параметра. Входные данные должны находиться в форме "данные во время выполнения" (DAE) с использованием **SQLPutData** вместо привязки их к предварительно выделенному буферу.  
  
 Эта функция может использоваться приложениями ODBC 3,8 или перекомпилированными приложениями ODBC 3. x и ODBC 2. x, и эти приложения должны иметь драйвер ODBC 3,8, поддерживающий получение выходных параметров с помощью **SQLGetData** и ДИСПЕТЧЕРА драйверов ODBC 3,8. Сведения о том, как включить более старое приложение для использования новых функций ODBC, см. в разделе [Таблица совместимости](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
## <a name="usage-example"></a>Пример использования  
 Например, рассмотрим исполнение хранимой процедуры **{CALL sp_f (?,?)}**, где оба параметра привязаны как SQL_PARAM_OUTPUT_STREAM, а хранимая процедура не возвращает результирующий набор (далее в этом разделе вы найдете более сложный сценарий):  
  
1.  Для каждого параметра вызовите **SQLBindParameter** с параметром *инпутаутпуттипе* , для которого задано значение SQL_PARAM_OUTPUT_STREAM, а *параметервалуептр* — маркер, например номер параметра, указатель на данные или указатель на структуру, которую приложение использует для привязки входных параметров. В этом примере в качестве токена будет использоваться порядковый номер параметра.  
  
2.  Выполните запрос с помощью **SQLExecDirect** или **SQLExecute**. Будет возвращено SQL_PARAM_DATA_AVAILABLE, указывающее, что для получения доступны потоковые выходные параметры.  
  
3.  Вызовите **метод SQLParamData** , чтобы получить параметр, доступный для извлечения. **Метод SQLParamData** возвратит SQL_PARAM_DATA_AVAILABLE с маркером первого доступного параметра, который задан в **SQLBindParameter** (шаг 1). Токен возвращается в буфере, на который указывает *валуептрптр* .  
  
4.  Вызовите **SQLGetData** с аргументом *Col*_or \_ *Param_Num* задайте порядковый номер параметра, чтобы получить данные первого доступного параметра. Если **SQLGetData** возвращает SQL_SUCCESS_WITH_INFO и SQLSTATE 01004 (усечение данных), а тип имеет переменную длину как на клиенте, так и на сервере, то дополнительные данные можно получить из первого доступного параметра. Вы можете по-прежнему вызывать **SQLGetData** , пока не вернет SQL_SUCCESS или SQL_SUCCESS_WITH_INFO с другим **SQLSTATE**.  
  
5.  Повторите шаги 3 и 4, чтобы получить текущий параметр.  
  
6.  Снова вызовите **метод SQLParamData** . Если он возвращает все, кроме SQL_PARAM_DATA_AVAILABLE, то больше нет потоковых данных параметров для извлечения, а код возврата будет кодом возврата следующего выполняемого оператора.  
  
7.  Вызовите **SQLMoreResults** для обработки следующего набора параметров, пока он не вернет SQL_NO_DATA. **SQLMoreResults** будет возвращать SQL_NO_DATA в этом примере, если атрибуту инструкции SQL_ATTR_PARAMSET_SIZE было присвоено значение 1. В противном случае **SQLMoreResults** возвратит SQL_PARAM_DATA_AVAILABLE, чтобы указать, что для следующего набора параметров доступны потоковые выходные параметры.  
  
 Как и входной параметр DAE, токен, используемый в аргументе *параметервалуептр* в **SQLBindParameter** (шаг 1), может быть указателем, указывающим на структуру данных приложения, которая содержит порядковый номер параметра и дополнительные сведения о приложении, если это необходимо.  
  
 Порядок возвращаемых потоковых выходных данных или входных и выходных параметров зависит от конкретного драйвера и может не всегда совпадать с порядком, указанным в запросе.  
  
 Если приложение не вызывает **SQLGetData** на шаге 4, значение параметра отбрасывается. Аналогично, если приложение вызывает **метод SQLParamData** до того, как в **SQLGetData**будет считано все значение параметра, оставшаяся часть значения отбрасывается, и приложение может обработать следующий параметр.  
  
 Если приложение вызывает **SQLMoreResults** перед обработкой всех потоковых выходных параметров (**метод SQLParamData** по-прежнему возвращает SQL_PARAM_DATA_AVAILABLE), все оставшиеся параметры отбрасываются. Аналогично, если приложение вызывает **SQLMoreResults** до того, как в **SQLGetData**будет считано все значение параметра, оставшаяся часть значения и все оставшиеся параметры отбрасываются, и приложение может продолжить обработку следующего набора параметров.  
  
 Обратите внимание, что приложение может указать тип данных C в **SQLBindParameter** и **SQLGetData**. Тип данных C, указанный в параметре **SQLGetData** , переопределяет тип данных c, указанный в **SQLBindParameter**, если только тип данных c, указанный в **SQLGetData** , не SQL_APD_TYPE.  
  
 Хотя потоковый выходной параметр более удобен, если тип данных выходного параметра имеет тип BLOB, эта функция также может использоваться с любым типом данных. Типы данных, поддерживаемые потоковыми выходными параметрами, указываются в драйвере.  
  
 При наличии SQL_PARAM_INPUT_OUTPUT_STREAM параметров для обработки **SQLExecute** или **SQLExecDirect** сначала возвратит SQL_NEED_DATA. Приложение может вызывать **метод SQLParamData** и **SQLPutData** для отправки данных параметров DAE. Когда обрабатываются все входные параметры DAE, **метод SQLParamData** возвращает SQL_PARAM_DATA_AVAILABLE для указания доступных потоковых выходных параметров.  
  
 При наличии потоковых выходных параметров и связанных выходных параметров драйвер определяет порядок обработки выходных параметров. Таким образом, если выходной параметр привязан к буферу (параметр **SQLBindParameter** *инпутаутпуттипе* имеет значение SQL_PARAM_INPUT_OUTPUT или SQL_PARAM_OUTPUT), буфер может не заполняться до тех пор, пока **метод sqlparamdata** не возвратит SQL_SUCCESS или SQL_SUCCESS_WITH_INFO. Приложение должно считывать связанный буфер только после того, как **метод SQLParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO, когда обрабатываются все потоковые выходные параметры.  
  
 В дополнение к потоковому выходному параметру источник данных может возвращать предупреждение и результирующий набор. Как правило, предупреждения и результирующие наборы обрабатываются отдельно от потокового выходного параметра путем вызова **SQLMoreResults**. Обработка предупреждений и результирующего набора перед обработкой потокового параметра вывода.  
  
 В следующей таблице описаны различные сценарии одной команды, отправленной на сервер, и способ работы приложения.  
  
|Сценарий|Возвращаемое значение из SQLExecute или SQLExecDirect|Дальнейшие действия|  
|--------------|---------------------------------------------------|---------------------|  
|Данные содержат только потоковые выходные параметры|SQL_PARAM_DATA_AVAILABLE|Для получения потоковых выходных параметров используйте **метод SQLParamData** и **SQLGetData** .|  
|Данные включают результирующий набор и потоковые выходные параметры|SQL_SUCCESS|Получите результирующий набор с помощью **SQLBindCol** и **SQLGetData**.<br /><br /> Вызовите **SQLMoreResults** , чтобы начать обработку потоковых выходных параметров. Он должен возвращать SQL_PARAM_DATA_AVAILABLE.<br /><br /> Для получения потоковых выходных параметров используйте **метод SQLParamData** и **SQLGetData** .|  
|Данные содержат предупреждающее сообщение и выходные параметры потоковой передачи|SQL_SUCCESS_WITH_INFO|Используйте **SQLGetDiagRec** и **SQLGetDiagField** для обработки предупреждающих сообщений.<br /><br /> Вызовите **SQLMoreResults** , чтобы начать обработку потоковых выходных параметров. Он должен возвращать SQL_PARAM_DATA_AVAILABLE.<br /><br /> Для получения потоковых выходных параметров используйте **метод SQLParamData** и **SQLGetData** .|  
|Данные включают в себя предупреждающее сообщение, результирующий набор и потоковые выходные параметры.|SQL_SUCCESS_WITH_INFO|Используйте **SQLGetDiagRec** и **SQLGetDiagField** для обработки предупреждающих сообщений. Затем вызовите **SQLMoreResults** , чтобы начать обработку результирующего набора.<br /><br /> Получение результирующего набора с помощью **SQLBindCol** и **SQLGetData**.<br /><br /> Вызовите **SQLMoreResults** , чтобы начать обработку потоковых выходных параметров. **SQLMoreResults** должен возвращать SQL_PARAM_DATA_AVAILABLE.<br /><br /> Для получения потоковых выходных параметров используйте **метод SQLParamData** и **SQLGetData** .|  
|Запрос с входными параметрами DAE, например с помощью потокового параметра ввода-вывода (DAE)|NEED_DATA SQL|Вызовите **метод SQLParamData** и **SQLPutData** для отправки данных входного параметра DAE.<br /><br /> После обработки всех входных параметров DAE **метод SQLParamData** может вернуть любой код возврата, который может возвращать **SQLExecute** и **SQLExecDirect** . Затем можно применить варианты в этой таблице.<br /><br /> Если код возврата SQL_PARAM_DATA_AVAILABLE, то доступны потоковые выходные параметры. Приложение должно вызвать **метод SQLParamData** еще раз, чтобы получить маркер для потокового выходного параметра, как описано в первой строке этой таблицы.<br /><br /> Если код возврата SQL_SUCCESS, то либо существует результирующий набор для обработки, либо обработка завершена.<br /><br /> Если код возврата SQL_SUCCESS_WITH_INFO, то для обработки будут выдаваться предупреждающие сообщения.|  
  
 После того как **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** возвращает SQL_PARAM_DATA_AVAILABLE, ошибка последовательности функций будет вызвана тем, что приложение вызывает функцию, которая отсутствует в следующем списке:  
  
-   **Функцию SQLAllocHandle**  /  **Склаллочандлестд**  
  
-   **SQLDataSources**  /  **SQLDrivers**  
  
-   **SQLGetInfo**  /  **SQLGetFunctions**  
  
-   **SQLGetConnectAttr**  /  **SQLGetEnvAttr**  /  **SQLGetDescField**  /  **SQLGetDescRec**  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **SQLGetDiagField**  /  **SQLGetDiagRec**  
  
-   **SQLCancel**  
  
-   **Склканцелхандле** (с маркером инструкции)  
  
-   **SQLFreeStmt** (параметр with = SQL_CLOSE, SQL_DROP или SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **SQLDisconnect**  
  
-   **SQLFreeHandle** (с параметром handletype = SQL_HANDLE_STMT)  
  
-   **SQLGetStmtAttr**  
  
 Приложения по-прежнему могут использовать **SQLSetDescField** или **SQLSetDescRec** для установки сведений о привязке. Сопоставление полей не изменится. Однако поля внутри дескриптора могут возвращать новые значения. Например, SQL_DESC_PARAMETER_TYPE может возвращать SQL_PARAM_INPUT_OUTPUT_STREAM или SQL_PARAM_OUTPUT_STREAM.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Сценарий использования: получение изображения в частях из результирующего набора  
 **SQLGetData** можно использовать для получения данных в частях, когда хранимая процедура возвращает результирующий набор, содержащий одну строку метаданных об изображении, а изображение возвращается в большом выходном параметре.  
  
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
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Сценарий использования: отправка и получение большого объекта в виде потокового входного или выходного параметра  
 **SQLGetData** можно использовать для получения и отправки данных в частях, когда хранимая процедура передает большой объект в качестве входного или выходного параметра, потоковая передача значения в базу данных и из нее. Нет необходимости хранить все данные в памяти.  
  
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
