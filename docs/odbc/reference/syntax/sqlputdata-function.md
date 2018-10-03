---
title: Функция SQLPutData | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPutData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPutData
helpviewer_keywords:
- SQLPutData function [ODBC]
ms.assetid: 9a60f004-1477-4c54-a20c-7378e1116713
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23a81ceda914bb43d4361e9c6fb8a2409bf2556e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809072"
---
# <a name="sqlputdata-function"></a>SQLPutData, функция
**Соответствие стандартам**  
 Версия была введена: ODBC 1.0 соответствует стандартам: ISO-92  
  
 **Сводка**  
 **SQLPutData** позволяет приложению отправлять данные для параметра или столбца к драйверу во время выполнения инструкции. Эта функция может использоваться для отправки символьные или двоичные данные значения в части со столбцом с типом специфического для источника данных символа, binary или данных (например, параметры типов SQL_LONGVARBINARY и SQL_LONGVARCHAR). **SQLPutData** поддерживает привязку к типу данных Юникода C, даже если основной драйвер не поддерживает данные в Юникоде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLPutData(  
      SQLHSTMT     StatementHandle,  
      SQLPOINTER   DataPtr,  
      SQLLEN       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *DataPtr*  
 [Вход] Указатель на буфер, содержащий данные для параметра или столбца. Данные должны быть в тип данных C, указанный в *ValueType* аргумент **SQLBindParameter** (для параметра данных) или *TargetType* аргумент  **SQLBindCol** (для данных столбца).  
  
 *StrLen_or_Ind*  
 [Вход] Длина \* *DataPtr*. Указывает объем данных, отправляемых в вызове **SQLPutData**. Объем данных, может различаться для каждого вызова для данного параметра или столбца. *StrLen_or_Ind* игнорируется, если он соответствует одной из следующих условий:  
  
-   *StrLen_or_Ind* SQL_NTS, SQL_NULL_DATA, или значение SQL_DEFAULT_PARAM.  
  
-   Тип данных C, указанный в **SQLBindParameter** или **SQLBindCol** SQL_C_CHAR или SQL_C_BINARY.  
  
-   Тип данных C — SQL_C_DEFAULT, а тип данных C по умолчанию для указанного типа данных SQL является SQL_C_CHAR и SQL_C_BINARY.  
  
 Для всех других типов данных C если *StrLen_or_Ind* не SQL_NULL_DATA или SQL_DEFAULT_PARAM, драйвер предполагает, что размер \* *DataPtr* буфер — это размер указан тип данных C с помощью *ValueType* или *TargetType* и отправляет значения типа данных. Дополнительные сведения см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) в типах данных приложение D:.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLPutData** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLPutData** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Усечение данных строки справа|Строка или двоичные данные, возвращаемые для выходного параметра завершилась усечение непустых символьных или двоичных данных от NULL. Если он был строковое значение, было усекаются справа. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07006|Нарушение атрибута ограниченного типа данных|Значение данных, определяемое *ValueType* аргумента в **SQLBindParameter** для привязанного параметра не удалось преобразовать в тип данных, определяемый *ParameterType*аргумента в **SQLBindParameter**.|  
|07S01|Недопустимое использование параметра по умолчанию|Задайте значение параметра с **SQLBindParameter**был SQL_DEFAULT_PARAM и значение по умолчанию не было соответствующего параметра.|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|22001|Строковые данные, усечение справа|Назначение символьное или двоичное значение в столбец завершилась усечение непустым (символ), отличное от null (двоичных) символов или байтов.<br /><br /> Тип данных SQL_NEED_LONG_DATA_LEN в **SQLGetInfo** был «Y», и дополнительные данные были отправлены параметра long (тип данных был SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных long специфического для источника данных), чем было указано с помощью *StrLen_or_IndPtr* аргумента в **SQLBindParameter**.<br /><br /> Тип данных SQL_NEED_LONG_DATA_LEN в **SQLGetInfo** был «Y», и больше данных был отправлен для длинного столбца (тип данных был SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных long специфического для источника данных), чем было указано в Длина буфера, соответствующего столбцу в строку данных, который был добавлен или обновлен с **SQLBulkOperations** или обновлено с помощью **SQLSetPos**.|  
|22003|Численное значение вне допустимого диапазона|Данные отправлены для привязанного числовой параметр или столбец вызвало целиком (в отличие от долей) часть номера будет усечен при назначении столбцу связанные таблицы.<br /><br /> Возвращает числовое значение (в виде строк или чисел) для одного или нескольких параметров ввода вывода или выходной вызвало бы всего (в отличие от долей) часть усекаемое число.|  
|22007|Формат недопустимые даты и времени|Данные, отправляемые для параметра или столбца, который был привязан к даты, времени или структура отметки времени было, соответственно, при обнаружении неверной даты, времени или метки времени.<br /><br /> Является параметром ввода вывода или вывода был привязан к даты, времени или структура отметки времени C, а значение в параметре возвращаемый было, соответственно, при обнаружении неверной даты, времени или метки времени. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|22008|Переполнение поля даты и времени|Выражение даты и времени, рассчитанное для ввода вывода или выходной параметр привело к даты, времени или C отметку времени, был недопустимым.|  
|22012|Деление на ноль|Арифметическое выражение вычисляется для ввода вывода или выходной параметр привело к деления на ноль.|  
|22015|Переполнение поля интервала|Для столбца точное числовое или интервал отправки данных или параметр к типу данных SQL интервал привело к потере значащих цифр.<br /><br /> Данных был отправлен для интервала столбца или параметра с более чем одним полем, был преобразован в числовой тип данных и имел нет представления в числовой тип данных.<br /><br /> Данные, отправляемые для столбца или параметра данных был назначен период, в тип SQL, и возникла не представление значения типа C в интервале тип SQL.<br /><br /> Данные, отправляемые для точного числового или интервал C столбца или параметра в тип интервала C привело к потере значащих цифр.<br /><br /> Данные, отправляемые для столбца или параметра данных был назначен в структуру интервала C, и было нет представления данных в структуре данных интервала.|  
|22018|Недопустимое символьное значение для спецификации приведения|Тип C был точное или Приблизительное числовое, datetime или тип интервала данных; тип SQL столбца был в символьный тип данных; и значение в столбец или параметр не является допустимым литералом связанного типа C.<br /><br /> Тип SQL был точное или Приблизительное числовое, datetime или тип интервала данных; Тип C был SQL_C_CHAR; и значение в столбец или параметр не является допустимым литералом связанного типа SQL.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция был снова вызван для *StatementHandle*.<br /><br /> Функция была вызвана, и до его завершения выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY009|Недопустимое использование пустого указателя|(DM) аргумент *DataPtr* был пустым указателем, а аргумент *StrLen_or_Ind* не 0, значение SQL_DEFAULT_PARAM, или значение SQL_NULL_DATA.|  
|HY010|Ошибка последовательности функций|(DM) предыдущего вызова функции не был выполнен вызов **SQLPutData** или **SQLParamData**.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. При вызове функции SQLPutData по-прежнему выполнении асинхронной функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.<br /><br /> (DM) асинхронно выполняемой функции (не такой) был вызван для *StatementHandle* и еще выполнялась при вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY019|Несимвольные и недвоичные данные отправлены по частям|**SQLPutData** был вызываемой больше, чем один раз для параметра или столбца, и он был не используется для отправки C символьных данных со столбцом с типом специфического для источника данных символа, binary или данных или передача двоичных данных C в столбец с символом , двоичный файл, или тип данных специфического для источника данных.|  
|HY020|Попытка присоединить пустое значение|**SQLPutData** был вызван несколько раз с момента вызова метода, который вернул значение SQL_NEED_DATA и в одном из этих вызовов *StrLen_or_Ind* аргумент содержится значение SQL_NULL_DATA, или значение SQL_DEFAULT_PARAM.|  
|HY090|Недопустимая длина строки или буфера|Аргумент *DataPtr* не является пустым указателем, а аргумент *StrLen_or_Ind* меньше, чем 0, но не равно SQL_NTS или SQL_NULL_DATA.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|Опрос недоступен в режиме асинхронное уведомление|Каждый раз, когда используется модель уведомлений, отключен опроса.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущий вызов функции в дескриптор возвращает SQL_STILL_EXECUTING, и если включен режим уведомлений, **SQLCompleteAsync** должен вызываться с дескриптором постобработки и завершить операцию.|  
  
 Если **SQLPutData** вызывается при попытке отправки данных для параметра в инструкции SQL, он может возвращать любой SQLSTATE, которые могут быть возвращены, функция, вызываемая для выполнения инструкции (**SQLExecute** или **SQLExecDirect**). Если он вызывается при попытке отправки данных для столбца, обновляемых или добавлены с классом **SQLBulkOperations** или обновляется значением **SQLSetPos**, он может возвращать любой SQLSTATE, которые могут быть возвращены с  **SQLBulkOperations** или **SQLSetPos**.  
  
## <a name="comments"></a>Комментарии  
 **SQLPutData** может вызываться для предоставления данных данные во время выполнения для двух целей: данные параметр для использования в вызове **SQLExecute** или **SQLExecDirect**, или столбец данных, используемый при обновлении строки или добавлены с помощью вызова **SQLBulkOperations** или обновляется путем вызова **SQLSetPos**.  
  
 Если приложение вызывает **SQLParamData** чтобы определить, какие данные необходимо отправлять, драйвер возвращает индикатор, приложение может использовать, чтобы определить, какие данные параметра для отправки или где находятся данные столбца. Он также возвращает значение SQL_NEED_DATA, который показывает, к приложению, он должен вызывать **SQLPutData** для отправки данных. В *DataPtr* аргумент **SQLPutData**, приложение передает указатель на буфер, содержащий данные для параметра или столбца.  
  
 Если драйвер возвращает значение SQL_SUCCESS, указывая для **SQLPutData**, приложение вызывает **SQLParamData** еще раз. **SQLParamData** возвращает SQL_NEED_DATA, если больше данных требуется отправить, в этом случае приложение вызывает **SQLPutData** еще раз. Он возвращает SQL_SUCCESS, если все данные во время выполнения данные были переданы. Затем приложение вызывает **SQLParamData** еще раз. Если драйвер возвращает SQL_NEED_DATA и другого индикатора в  *\*ValuePtrPtr*, это требует данных для другого параметра или столбца и **SQLPutData** вызывается снова. Если драйвер возвращает значение SQL_SUCCESS, затем все данные во время выполнения данные были переданы, и можно выполнить инструкцию SQL или **SQLBulkOperations** или **SQLSetPos** вызова могут быть обработаны.  
  
 Дополнительные сведения о том, как данные времени выполнения параметр данных передается во время выполнения инструкции, см. в разделе «Передача значения параметра» в [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) и [отправки длинных данных](../../../odbc/reference/develop-app/sending-long-data.md). Дополнительные сведения о том, как данные времени выполнения столбца данных является обновляемого или добавляемого, см. в разделе «С помощью SQLSetPos» в [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), «Выполнения массового обновления с помощью закладок» в [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), и [Длинных данных и функции SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
> [!NOTE]  
>  Приложение может использовать **SQLPutData** для отправки данных в частях только в том случае, при отправке данных символа C к столбцу с типом специфического для источника данных символа, binary или данных, или при отправке двоичных данных C для столбца с символом, двоичных данных, или данных Тип специфического для источника данных. Если **SQLPutData** вызывается более одного раза при других условиях, возвращается значение SQL_ERROR и SQLSTATE HY019 (несимвольные и недвоичные данные отправлены по частям).  
  
## <a name="example"></a>Пример  
 В следующем образце предполагается имя источника данных, именем Test. Связанная база данных должна иметь таблицу, можно создать, следующим образом:  
  
```  
CREATE TABLE emp4 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)  
```  
  
```  
// SQLPutData.cpp  
// compile with: odbc32.lib user32.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define TEXTSIZE  12000  
#define MAXBUFLEN 256  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // SQLBindParameter variables.  
   SQLLEN cbTextSize, lbytes;  
  
   // SQLParamData variable.  
   PTR pParmID;  
  
   // SQLPutData variables.  
   UCHAR  Data[] =   
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyz";  
  
   SDWORD cbBatch = (SDWORD)sizeof(Data) - 1;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set parameters based on total data to send.  
   lbytes = (SDWORD)TEXTSIZE;  
   cbTextSize = SQL_LEN_DATA_AT_EXEC(lbytes);  
  
   // Bind the parameter marker.  
   retcode = SQLBindParameter (hstmt1,           // hstmt  
                               1,                // ipar  
                               SQL_PARAM_INPUT,  // fParamType  
                               SQL_C_CHAR,       // fCType  
                               SQL_LONGVARCHAR,  // FSqlType  
                               lbytes,           // cbColDef  
                               0,                // ibScale  
                               (VOID *)1,        // rgbValue  
                               0,                // cbValueMax  
                               &cbTextSize);     // pcbValue  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the command.  
   retcode =   
      SQLExecDirect(hstmt1, (UCHAR*)"INSERT INTO emp4 VALUES('Paul Borm', 46,'1950-11-12 00:00:00', ?)", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_NEED_DATA) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Check to see if NEED_DATA; if yes, use SQLPutData.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if (retcode == SQL_NEED_DATA) {  
      while (lbytes > cbBatch) {  
         SQLPutData(hstmt1, Data, cbBatch);  
         lbytes -= cbBatch;  
      }  
      // Put final batch.  
      retcode = SQLPutData(hstmt1, Data, lbytes);   
   }  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Make final SQLParamData call.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("Final SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clean up.  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка буфер к параметру|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Отмена обработка инструкций|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнении подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Возвращает следующий параметр для отправки данных|[Функция SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
