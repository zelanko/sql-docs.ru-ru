---
title: Функция S'LPutData (англ.) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c4e704d96924942812904ea63d0e3d4fce8748e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300044"
---
# <a name="sqlputdata-function"></a>SQLPutData, функция
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 1.0: ISO 92  
  
 **Сводка**  
 **SLPutData** позволяет приложению отправлять данные по параметру или столбцу водителю во время выполнения оператора. Эта функция может использоваться для отправки значений символов или двоичных данных по частям в столбец с типом данных, характерный для двоичного, двоичного или исходного кода данных (например, параметры SQL_LONGVARBINARY или SQL_LONGVARCHAR типов). **SLPutData** поддерживает привязку к типу данных Unicode C, даже если базовый драйвер не поддерживает данные Unicode.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLPutData(  
      SQLHSTMT     StatementHandle,  
      SQLPOINTER   DataPtr,  
      SQLLEN       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Аргументы  
 *Обработка заявления*  
 (Вход) Ручка оператора.  
  
 *DataPtr*  
 (Вход) Указатель на буфер, содержащий фактические данные для параметра или столбца. Данные должны быть в типе данных C, указанном в аргументе *ValueType* **s'LBindParameter** (для данных параметров) или аргументе *TargetType* **s'LBindCol** (для данных столбца).  
  
 *StrLen_or_Ind*  
 (Вход) Длина \* *DataPtr*. Упоняет объем данных, отправляемых при вызове на **s'LPutData**. Объем данных может варьироваться в зависимости от каждого вызова для данного параметра или столбца. *StrLen_or_Ind* игнорируется, если только он не отвечает одному из следующих условий:  
  
-   *StrLen_or_Ind* SQL_NTS, SQL_NULL_DATA или SQL_DEFAULT_PARAM.  
  
-   Тип данных C, указанный в **S'LBindParameter** или **S'LBindCol,** является SQL_C_CHAR или SQL_C_BINARY.  
  
-   Тип данных C является SQL_C_DEFAULT, а тип данных C по умолчанию для указанного типа данных S'L SQL_C_CHAR или SQL_C_BINARY.  
  
 Для всех других типов данных C, если *StrLen_or_Ind* не SQL_NULL_DATA или \*SQL_DEFAULT_PARAM, драйвер предполагает, что размер буфера *DataPtr* представляет собой размер типа данных C, указанный в *ValueType* или *TargetType,* и отправляет все значение данных. Для получения дополнительной информации в приложении D: Типы данных можно ознакомиться на [примере преобразования данных с C в S-L.](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LPutData** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону s'LGetDiagRec** с *помощью handleType* of SQL_HANDLE_STMT и *ручки* *обработки заявлений.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LPutData,** и разъясняются каждое из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, правые усеченные|Строка или двоичные данные, возвращенные для параметра вывода, привели к усечению непустого символа или неnull двоичных данных. Если это было значение строки, то оно было правильно усечено. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|07006|Нарушение атрибута типа ограниченного доступа|Значение данных, идентифицированное аргументом *ValueType* в **sLBindParameter** для связанного параметра, не может быть преобразовано в тип данных, определенный аргументом *ParameterType* в **S'LBindParameter.**|  
|07S01|Недействительное использование параметра по умолчанию|Значение параметра, установленное с **помощью S'LBindParameter**, было SQL_DEFAULT_PARAM, а соответствующий параметр не имел значения по умолчанию.|  
|08S01|Сбой связи|Связь между драйвером и источником данных, к которому был подключен драйвер, не сработала до завершения обработки функции.|  
|22001|Строковые данные, правильное усечение|Назначение символа или двоичного значения в столбец привело к усечению непустых (символов) или не-нулевых (двоичных) символов или байтов.<br /><br /> Тип SQL_NEED_LONG_DATA_LEN информации в **S'LGetInfo** был "Y", и больше данных было отправлено для длинного параметра (тип данных был SQL_LONGVARCHAR, SQL_LONGVARBINARY или длинный тип данных, специфичный для исходных данных), чем было указано в *StrLen_or_IndPtr* аргументе в **S'LBindParameter.**<br /><br /> Тип SQL_NEED_LONG_DATA_LEN информации в **S'LGetInfo** был "Y", и больше данных было отправлено для длинного столбца (тип данных был SQL_LONGVARCHAR, SQL_LONGVARBINARY или длинный тип данных, специфичный для исходных данных), чем было указано в буфере длины, соответствующем столбику в ряду данных, которые были добавлены или обновлены с **помощью S'LBulkOperations** или обновлены с **помощью S'LSetPos.**|  
|22003|Числовое значение вне диапазона|Данные, отправленные для связанного численного параметра или столбца, привели к тому, что вся (в отличие от дробной) часть числа была усечена при присвоении столбцу связанной таблицы.<br /><br /> Возвращение численного значения (в качестве численного или строки) для одного или нескольких входных/выходных или выходных параметров привело бы к тому, что вся (в отличие от дробной) часть числа была бы усечена.|  
|22007|Недействительный формат дата-времени|Данные, отправленные для параметра или столбца, привязанного к структуре даты, времени или метки времени, были, соответственно, недействительной датой, временем или меткой времени.<br /><br /> Параметр ввода/вывода или вывода был привязан к структуре даты, времени или временной метки C, а значение в возвращенном параметре, соответственно, является недействительной датой, временем или меткой времени. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|22008|Переполниние полей datetime|Выражение времени даты, вычисленные для ввода/вывода или параметра вывода, привело к недействительной структуре даты, времени или временной метки C.|  
|22012|Разделение на ноль|Арифметическое выражение, рассчитанное для ввода/вывода или вывода параметра, привело к разделению на ноль.|  
|22015|Переполниние поля интервала|Данные, отправленные для точного цифрового или интервального столбца или параметра в интервале типа данных S'L, привели к потере значительных цифр.<br /><br /> Данные были отправлены для интервального столбца или параметра с более чем одним полем, были преобразованы в числовый тип данных и не имели представления в численном типе данных.<br /><br /> Данные, отправленные для данных столбца или параметра, были отнесены к типу интервала S'L, и в типе интервала s-L не было представлено значение типа C.<br /><br /> Данные, отправленные для точного цифрового или интервала C столбец или параметр в тип интервала C вызвало потерю значительных цифр.<br /><br /> Данные, отправленные для данных столбца или параметра, были назначены структуре интервала C, и в структуре данных интервала не было представлено.|  
|22018|Недействительное значение символов для спецификации литья|Тип C был точным или приблизительным числом, временем даты или типом данных интервала; тип столбца s'L был типом данных символов; и значение в столбце или параметре не является действительным буквальным типом связанного C.<br /><br /> Тип S'L был точным или приблизительным числом, временем даты или типом данных интервала; тип C был SQL_C_CHAR; и значение в столбце или параметре не было действительным буквальным типа связанного Типа S'L.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка была включена для *StatementHandle*. Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхлик** был вызван на *StatementHandle*. Затем функция была вызвана снова на *StatementHandle*.<br /><br /> Функция была вызвана, и перед завершением выполнения, **S'LCancel** или **S'LКансортхливнейра** был вызван на *StatementHandle* из другого потока в многопоточном приложении.|  
|HY009|Недействительное использование нулевой указатель|(DM) Аргумент *DataPtr* был нулевой указатель, и аргумент *StrLen_or_Ind* не было 0, SQL_DEFAULT_PARAM, или SQL_NULL_DATA.|  
|HY010|Ошибка последовательности функций|(DM) Предыдущий вызов функции не был вызовом на **S'LPutData** или **S'LParamData**.<br /><br /> (DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *StatementHandle.* Эта асинхронная функция по-прежнему исполнялась, когда была вызвана функция S'LPutData.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, или **S'LMoreResults** был вызван для *statementHandle* и вернулся SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до того, как данные были извлечены для всех потоковых параметров.<br /><br /> (DM) Асинхронно выполнение функции (не этот) был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY019|Нехарактерные и небинарные данные, отправленные по частям|Для параметра или столбца **s'LPutData** неразно назывался, и он не использовался для отправки данных символов C в столбец с типом данных, двоичных или исходных данных данных, или для отправки двоичных данных C в столбец с типом данных с символом, двоичным или исходным типом данных.|  
|HY020|Попытка совмещеть нулевую стоимость|С момента вызова, который возвращался SQL_NEED_DATA, **s'LPutData** вызывали несколько раз, и в одном из этих вызовов *аргумент StrLen_or_Ind* содержал SQL_NULL_DATA или SQL_DEFAULT_PARAM.|  
|HY090|Недействительная длина строки или буфера|Аргумент *DataPtr* не был нулевым указателем, и аргумент *StrLen_or_Ind* был меньше, чем 0, но не равен SQL_NTS или SQL_NULL_DATA.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
|IM017|Опрос отключен в асинхронном режиме уведомления|Всякий раз, когда используется модель уведомления, опрос отключается.|  
|IM018|Для завершения предыдущей асинхронной операции на этой ручке не был вызван **S'LCompleteAsync.**|Если предыдущий вызов функции на ручке возвращается SQL_STILL_EXECUTING и если режим уведомления включен, **s'LCompleteAsync** должен быть вызван на ручку, чтобы сделать пост-обработку и завершить операцию.|  
  
 Если **при** отправке данных по параметру в выписке s-L можно вернуть любой S'Lstate, который может быть возвращен функцией, вызванной для выполнения оператора (**S'LExecute** или **S'LExecDirect**). Если он вызывается при отправке данных для обновления или добавления в столбец с **помощью S'LBulkOperations** или обновления с **помощью S'LSetPos,** он может вернуть любой S'LSTATE, который может быть возвращен **с помощью S'LBulkOperations** или **S'LSetPos**.  
  
## <a name="comments"></a>Комментарии  
 **Можно** вызвать данные о количестве данных по исполнению данных для двух целей: данные о параметрах, которые будут использоваться при вызове в **S'L'LExecute** или **S'LExecDirect,** или данные столбцов, которые будут использоваться при обновлении или добавлении строки в **S'LBulkOperations** или обновлены вызовом в **S'LSetPos.**  
  
 Когда приложение вызывает **данные S'LParamData,** чтобы определить, какие данные оно должно отправить, драйвер возвращает индикатор, который приложение может использовать для определения данных параметра для отправки или где можно найти данные столбца. Он также возвращает SQL_NEED_DATA, что является индикатором для приложения, что он должен вызвать **S'LPutData** для отправки данных. В аргументе *DataPtr* в **пользу S'LPutData**приложение передает указатель в буфер, содержащий фактические данные для параметра или столбца.  
  
 Когда водитель возвращает SQL_SUCCESS для **S'LPutData,** приложение снова вызывает **S'LParamData.** **SLParamData** возвращает SQL_NEED_DATA, если необходимо отправить больше данных, и в этом случае приложение снова вызывает **S'LPutData.** Он возвращает SQL_SUCCESS если все данные о выполнении данных были отправлены. Затем приложение снова вызывает **S'LParamData.** Если драйвер возвращается SQL_NEED_DATA и еще один индикатор в * \*ValuePtrPtr,* он требует данных для другого параметра или столбца и **s'LPutData** вызывается снова. Если драйвер возвращается SQL_SUCCESS, то все данные о выполнении данных были отправлены, и выписка по S'LL-L'L может быть выполнена или можно обработать вызов **S'LBulkOperations** или **sLSetPos.**  
  
 Для получения дополнительной информации о том, как данные параметра данных данных [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) о параметрах [Sending Long Data](../../../odbc/reference/develop-app/sending-long-data.md)данных о данных по исполнению передаются во время выполнения оператора, см. Для получения более подробной информации о том, как обновляются или добавляются данные столбца данных о персональных данных в исполнении, см. [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md) [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md) [Long Data and SQLSetPos and SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)  
  
> [!NOTE]  
>  Приложение может использовать **данные** по частям только при отправке данных о символе C в столбец с типом данных, двоичных или исходных данных данных, или при отправке двоичных данных C в столбец с типом данных, характерных для символов, двоичных или исходных данных. Если **s'LPutData** вызывается более одного раза при любых других условиях, он возвращает SQL_ERROR и S'Lstate HY019 (нехарактерные и небинарные данные, отправленные частями).  
  
## <a name="example"></a>Пример  
 Следующий пример предполагает имя источника данных под названием Test. Связанная база данных должна иметь таблицу, которую можно создать следующим образом:  
  
```sql  
CREATE TABLE emp4 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)  
```  
  
```cpp  
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
|Привязка буфера к параметру|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Отмена обработки оператора|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выполнение оператора S'L|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнение подготовленного заявления по S'L|[Функция «СЗЛВы»](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Возвращение следующего параметра для отправки данных для|[Функция SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
