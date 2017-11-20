---
title: "Функция SQLPutData | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fac078be865e13dc2a216c8c0610d15be0b2e373
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlputdata-function"></a>SQLPutData, функция
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLPutData** позволяет приложению отправлять данные для параметра или столбца в драйвере во время выполнения инструкции. Эта функция может использоваться для отправки символьные или двоичные данные значения в частях к столбцу с типом данных, определяемые источником символьных, двоичных и данные (например, параметры типов SQL_LONGVARBINARY и SQL_LONGVARCHAR). **SQLPutData** поддерживает привязку к типу данных Юникода C, даже если основной драйвер не поддерживает данные в Юникоде.  
  
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
 [Вход] Указатель на буфер, содержащий данные для параметра или столбца. Данные должны быть в тип данных C, указанный в *ValueType* аргумент **SQLBindParameter** (для параметра данных) или *TargetType* аргумент  **SQLBindCol** (для столбца данных).  
  
 *StrLen_or_Ind*  
 [Вход] Длина \* *DataPtr*. Указывает объем данных, передаваемых при вызове **SQLPutData**. Объем данных, может различаться для каждого вызова для данного параметра или столбца. *StrLen_or_Ind* игнорируется, если он соответствует одному из следующих условий:  
  
-   *StrLen_or_Ind* SQL_NTS, SQL_NULL_DATA или SQL_DEFAULT_PARAM.  
  
-   Тип данных C, указанный в **SQLBindParameter** или **SQLBindCol** SQL_C_CHAR или SQL_C_BINARY.  
  
-   Тип данных C — SQL_C_DEFAULT, а тип данных C по умолчанию для указанного типа данных SQL является SQL_C_CHAR и SQL_C_BINARY.  
  
 Для всех других типов данных C если *StrLen_or_Ind* не SQL_NULL_DATA или SQL_DEFAULT_PARAM, драйвер предполагает, что размер \* *DataPtr* буфера — это размер указанного типа данных C с *ValueType* или *TargetType* и отправляет значения типа данных. Дополнительные сведения см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) в типах данных приложение D:.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLPutData** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLPutData** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Строка справа усечение данных|Строка или двоичные данные, возвращаемые для выходного параметра привело к усечению непустых символьных или двоичных данных от NULL. Если он был строковое значение, было усечено справа. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07006|Нарушение атрибута ограниченного типа данных|Значение определяется *ValueType* аргумент в **SQLBindParameter** для связанных параметров не удалось преобразовать в тип данных, определяемый *ParameterType*аргумент в **SQLBindParameter**.|  
|07S01|Недопустимое использование параметра по умолчанию|Задайте значение параметра с **SQLBindParameter**был SQL_DEFAULT_PARAM и соответствующего параметра отсутствует значение по умолчанию.|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|22001|Строковые данные, усечение справа|Назначение символьное или двоичное значение в столбец завершилась усечение непустым (символ) или ненулевой (двоичный) символов или байтов.<br /><br /> Тип данных SQL_NEED_LONG_DATA_LEN в **SQLGetInfo** была «Y» и дополнительные данные были отправлены для параметра long (тип данных был SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных long, определяемые источником данных) не был указан с *StrLen_or_IndPtr* аргумент в **SQLBindParameter**.<br /><br /> Тип данных SQL_NEED_LONG_DATA_LEN в **SQLGetInfo** была «Y» и дополнительные данные были отправлены для длинного столбца (тип данных был SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных long, определяемые источником данных) было указано в Длина буфера, соответствующий столбец в строке данных, которые были добавлены или обновлены с **SQLBulkOperations** или обновлено с **SQLSetPos**.|  
|22003|Численное значение вне допустимого диапазона|Данные отправлены для связанных числовой параметр или столбец за весь (в отличие от доли) часть номера будут усечены при назначении столбцу связанные таблицы.<br /><br /> Возвращает числовое значение (как числовое или строковое) для одного или нескольких параметров ввода вывода или вывода могло привести целиком (в отличие от доли) часть усекаемое число.|  
|22007|Формат недопустимые даты и времени|Данные, отправленные для параметра или столбца, который был привязан к даты, времени или структура отметки времени было, соответственно, неверной даты, времени или отметки времени.<br /><br /> Ввода вывода или выходного параметра был привязан к даты, времени или структура отметки времени C, а значение возвращаемого параметра было, соответственно, неверной даты, времени или отметки времени. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|22008|Переполнение поля DateTime|Вычисленное выражение даты и времени для ввода вывода или завершился даты, времени или структура отметки времени C, недопустимый выходной параметр.|  
|22012|Деление на ноль|Арифметическое выражение вычисляется для ввода вывода или выходной параметр завершился деления на ноль.|  
|22015|Переполнение поля интервала|Данные отправлены для точное числовое или интервал столбца или параметра в тип данных SQL интервал привело к потере значащих разрядов.<br /><br /> Данные был отправлен для интервала столбца или параметра с более чем одним полем, был преобразован в числовой тип данных и содержал нет представления в числовой тип данных.<br /><br /> Данные, отправляемые для столбца или параметра данных был назначен тип SQL интервала и возникла не представление значения типа C, в течение интервала, тип SQL.<br /><br /> Данные, отправляемые для точного числового или интервала C столбца или параметра тип интервала C привело к потере значащих разрядов.<br /><br /> Данные, отправляемые для столбца или параметра данных был назначен структуру интервала C и возникла не представление данных в структуре данных интервала.|  
|22018|Недопустимое символьное значение для спецификации приведения|Тип C был точное или Приблизительное числовое, datetime или тип интервала; тип SQL столбца был в символьный тип данных; и значение в столбец или параметр не является допустимым литералом связанного типа C.<br /><br /> Тип SQL был точное или Приблизительное числовое, datetime или тип интервала; Тип C была SQL_C_CHAR; и значение в столбец или параметр не является допустимым литералом связанного типа SQL.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Операция отменена|Асинхронная обработка была включена для *StatementHandle*. Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция был вызван, и до выполнения, **SQLCancel** или **SQLCancelHandle** был вызван для *StatementHandle* из другого потока в многопоточные приложения.|  
|HY009|Недопустимое использование пустого указателя|(DM) аргумент *DataPtr* был пустым указателем, а аргумент *StrLen_or_Ind* не 0, значение SQL_DEFAULT_PARAM, или SQL_NULL_DATA.|  
|HY010|Ошибка последовательности функций|(DM) предыдущего вызова функции не был выполнен вызов **SQLPutData** или **SQLParamData**.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. При вызове функции SQLPutData по-прежнему выполнении асинхронной функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.<br /><br /> (DM) был вызван асинхронно выполняемой функции (не данный файл) для *StatementHandle* и все еще выполняется, при вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY019|Несимвольные и недвоичные данные отправлены по частям.|**SQLPutData** был вызван больше, чем один раз для параметра или столбца, и он не использовался для отправки C символьные данные в столбец с типом данных, определяемые источником символьных, двоичных и данных или для отправки двоичных данных C для столбца с символом , binary или типа данных, определяемые источником данных.|  
|HY020|Попытка присоединить пустое значение|**SQLPutData** был вызван несколько раз с момента вызова метода, возвращается значение SQL_NEED_DATA, а также в одном из этих вызовов *StrLen_or_Ind* аргумент содержит SQL_NULL_DATA или SQL_DEFAULT_PARAM.|  
|HY090|Недопустимая длина строки или буфера|Аргумент *DataPtr* не является пустым указателем, а аргумент *StrLen_or_Ind* было меньше, чем 0, но не равно SQL_NTS или SQL_NULL_DATA.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
|IM017|В режиме асинхронное уведомление отключена опроса|При использовании модели уведомление опроса отключен.|  
|IM018|**SQLCompleteAsync** не был вызван для завершения предыдущей асинхронной операции на этот дескриптор.|Если предыдущего вызова функции с дескриптором возвращает SQL_STILL_EXECUTING и уведомлений в режиме **SQLCompleteAsync** должен вызываться для этого после обработки и выполнения операции с дескриптором.|  
  
 Если **SQLPutData** вызывается при попытке отправки данных для параметра в инструкции SQL, она может возвращать любой SQLSTATE, которые могут быть возвращены, функция, вызываемая для выполнения инструкции (**SQLExecute** или **SQLExecDirect**). Если он вызывается при попытке отправки данных для столбца, обновляемых или добавлены с классом **SQLBulkOperations** или обновлением с использованием **SQLSetPos**, она может возвращать любой SQLSTATE, которые могут быть возвращены с  **SQLBulkOperations** или **SQLSetPos**.  
  
## <a name="comments"></a>Комментарии  
 **SQLPutData** может вызываться для предоставления данных во время выполнения для двух целей: данные параметр для использования в вызове **SQLExecute** или **SQLExecDirect**, или столбец данных для использования в том случае, если строка обновить или добавить вызов **SQLBulkOperations** или обновляется путем вызова **SQLSetPos**.  
  
 Если приложение вызывает **SQLParamData** , чтобы определить, какие данные необходимо отправлять, драйвер возвращает индикатор, приложение может использовать, чтобы определить, какие данные параметра для отправки или где находятся данные столбца. Он также возвращает значение SQL_NEED_DATA, что является признаком к приложению, он должен вызывать **SQLPutData** для отправки данных. В *DataPtr* аргумент **SQLPutData**, приложение передает указатель на буфер, содержащий данные для параметра или столбца.  
  
 Когда драйвер возвращает SQL_SUCCESS для **SQLPutData**, приложение вызывает **SQLParamData** еще раз. **SQLParamData** возвращает SQL_NEED_DATA, если данные требуется отправить, в этом случае приложение вызывает **SQLPutData** еще раз. Он возвращает SQL_SUCCESS отправки всех данных данные во время выполнения. Затем приложение вызывает **SQLParamData** еще раз. Если драйвер возвращает SQL_NEED_DATA и другого индикатора в  *\*ValuePtrPtr*, необходимы данные другой параметр или столбец и **SQLPutData** будет вызван повторно. Если драйвер возвращает SQL_SUCCESS, затем все данные во время выполнения данные отправлены и можно выполнить инструкцию SQL или **SQLBulkOperations** или **SQLSetPos** вызова могут быть обработаны.  
  
 Дополнительные сведения о том, как данные времени выполнения параметр данных передается во время выполнения инструкции, в разделе «Передача значений параметров» в [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) и [отправки длинных данных](../../../odbc/reference/develop-app/sending-long-data.md). Для обновляется или добавить дополнительные сведения о данных столбца как данных во время выполнения, см. в разделе «Использование SQLSetPos» в [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), «Выполнение массового обновления с помощью закладок» в [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), и [Большие объемы данных и SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
> [!NOTE]  
>  Приложение может использовать **SQLPutData** для отправки данных в частях только при отправке C символьные данные в столбец с типом данных, определяемые источником символьных, двоичных и данных или при отправке двоичных данных C для столбца с символом, двоичных данных, или данные тип, определяемые источником данных. Если **SQLPutData** вызывается более одного раза в других условиях, он возвращает значение SQL_ERROR и SQLSTATE HY019 (несимвольные и недвоичные данные отправлены по частям).  
  
## <a name="example"></a>Пример  
 В следующем образце предполагается именем Test имя источника данных. Связанная база данных должна иметь таблицы, которые можно создавать, как показано ниже:  
  
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
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнения подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Возвращает следующий параметр для отправки данных|[Функция SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)

