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
ms.openlocfilehash: 676f9fb526996e96b27bb758a7343c86afaac460
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053652"
---
# <a name="sqlputdata-function"></a>SQLPutData, функция
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: ISO 92  
  
 **Сводка**  
 **SQLPutData** позволяет приложению передавать данные для параметра или столбца в драйвер во время выполнения инструкции. Эта функция может использоваться для отправки символьных или двоичных значений данных в части в столбец с типом данных символьного, двоичного или конкретного источника данных (например, параметры типов SQL_LONGVARBINARY или SQL_LONGVARCHAR). **SQLPutData** поддерживает привязку к типу данных Юникода C, даже если базовый драйвер не поддерживает данные в Юникоде.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLPutData(  
      SQLHSTMT     StatementHandle,  
      SQLPOINTER   DataPtr,  
      SQLLEN       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции.  
  
 *датаптр*  
 Входной Указатель на буфер, содержащий фактические данные для параметра или столбца. Данные должны находиться в типе данных C, указанном в аргументе *ValueType* **SQLBindParameter** (для данных параметра) или в аргументе *TargetType* **SQLBindCol** (для данных столбца).  
  
 *StrLen_or_Ind*  
 Входной \*Длина *датаптр*. Указывает объем данных, отправляемых в вызове **SQLPutData**. Объем данных может различаться при каждом вызове для данного параметра или столбца. *StrLen_Or_Ind* игнорируется, если он не соответствует одному из следующих условий:  
  
-   *StrLen_Or_Ind* — SQL_NTS, SQL_NULL_DATA или SQL_DEFAULT_PARAM.  
  
-   Тип данных C, указанный в **SQLBindParameter** или **SQLBindCol** , SQL_C_CHAR или SQL_C_BINARY.  
  
-   Тип данных C — SQL_C_DEFAULT, а для указанного типа данных SQL по умолчанию — SQL_C_CHAR или SQL_C_BINARY.  
  
 Для всех других типов данных языка C, если *StrLen_Or_Ind* не SQL_NULL_DATA или SQL_DEFAULT_PARAM, драйвер предполагает, что \*размер буфера *датаптр* равен размеру типа данных C, указанного в параметре *ValueType* или *TargetType* , и отправляет все значение данных. Дополнительные сведения см. в разделе [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) в приложении г: типы данных.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLPutData** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLPutData** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, усеченные справа|Строковые или двоичные данные, возвращаемые для выходного параметра, привели к усечению непустого символа или двоичных данных, отличных от NULL. Если это строковое значение, оно было усечено по правому краю. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|07006|Нарушение атрибута ограниченного типа данных|Значение данных, определяемое аргументом *ValueType* в **SQLBindParameter** для привязанного параметра, не может быть преобразовано в тип данных, определяемый аргументом *ParameterType* в **SQLBindParameter**.|  
|07S01|Недопустимое использование параметра по умолчанию|Значение параметра, заданное с помощью **SQLBindParameter**, было SQL_DEFAULT_PARAM, а соответствующий параметр не имел значения по умолчанию.|  
|08S01|Сбой канала связи|Канал связи между драйвером и источником данных, к которому был подключен драйвер, был неудачен до завершения обработки функции.|  
|22001|Строковые данные, усечение справа|Присвоение символьного или двоичного значения столбцу привело к усечению непустых (символов) или не пустых (двоичных) символов или байтов.<br /><br /> SQL_NEED_LONG_DATA_LEN тип сведений в **SQLGetInfo** был "Y", а для длинного параметра было отправлено больше данных (тип данных был SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных, относящийся к определенному источнику данных), чем было указано с помощью аргумента *StrLen_or_IndPtr* в **SQLBindParameter**.<br /><br /> Тип сведений SQL_NEED_LONG_DATA_LEN в **SQLGetInfo** был "Y", а для длинного столбца были отправлены дополнительные данные (тип данных был SQL_LONGVARCHAR, SQL_LONGVARBINARY или тип данных Long, определяемый источником данных), чем указано в буфере длины, соответствующем столбцу в строке данных, которая была добавлена или изменена с помощью **SQLBulkOperations** или изменена с помощью **SQLSetPos**.|  
|22003|Числовое значение вне допустимого диапазона|Данные, отправленные для привязанного числового параметра или столбца, обрезают часть числа (в отличие от дробной части), которая будет обрезана при назначении связанному столбцу таблицы.<br /><br /> Возврат числового значения (в виде числового или строкового) для одного или нескольких входных, выходных или выходных параметров приведет к усечению всего числа (в отличие от дробной части).|  
|22007|Недопустимый формат даты и времени|Данные, отправленные для параметра или столбца, привязанные к структуре даты, времени или метки времени, соответственно, имеют недопустимую дату, время или отметку времени.<br /><br /> Входной/выходной или выходной параметр привязан к структуре даты, времени или метки времени C, а значение в возвращенном параметре было соответственно недействительной дате, времени или метке времени. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|22008|Переполнение поля даты и времени|Выражение DateTime, вычисленное для входного/выходного или выходного параметра, привело к недопустимой структуре даты, времени или метки времени C.|  
|22012|Деление на ноль|Арифметическое выражение, вычисленное для входного/выходного или выходного параметра, привело к делению на нуль.|  
|22015|Переполнение поля интервала|Данные, отправленные для точного числового или интервалного столбца или параметра в тип данных SQL Interval, привели к утрате значащих цифр.<br /><br /> Данные были отправлены для столбца интервала или параметра с более чем одним полем, были преобразованы в числовой тип данных и не имели представления в числовом типе данных.<br /><br /> Данные, отправленные для данных столбца или параметра, были назначены типу SQL Interval, и в типе SQL Interval не было представления значения типа C.<br /><br /> Данные, отправленные для точного числового столбца или параметра в интервале C для типа Interval C, привели к утрате значащих цифр.<br /><br /> Данные, отправленные для данных столбца или параметра, были назначены структуре интервала C и не существовало представления данных в структуре данных интервала.|  
|22018|Недопустимое символьное значение для спецификации приведения|Тип C был точным или приблизительным числовым, типом данных DateTime или интервалом. тип SQL столбца имеет символьный тип данных; и значение в столбце или параметре не является допустимым литералом для привязанного типа C.<br /><br /> Тип SQL был точным или приблизительным числовым, типом данных DateTime или значением интервала. Тип C — SQL_C_CHAR; и значение в столбце или параметре не является допустимым литералом привязанного типа SQL.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка включена для *статеменсандле*. Функция была вызвана, и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** для *статеменсандле*. Затем функция была вызвана в *статеменсандле*.<br /><br /> Функция была вызвана и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** в *статеменсандле* из другого потока многопоточного приложения.|  
|HY009|Недопустимое использование пустого указателя|(DM) аргумент *датаптр* был пустым указателем, а аргумент *StrLen_Or_Ind* не равен 0, SQL_DEFAULT_PARAM или SQL_NULL_DATA.|  
|HY010|Ошибка последовательности функций|(DM) предыдущий вызов функции не вызывал **SQLPutData** или **метод SQLParamData**.<br /><br /> (DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове функции SQLPutData.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.<br /><br /> (DM) вызывается асинхронно исполняемая функция (не эта одна) для *статеменсандле* и все еще выполнялась при вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY019|Несимвольные и недвоичные данные, отправляемые частями|**SQLPutData** был вызван более одного раза для параметра или столбца, и он не был использован для отправки символьных данных c в столбец с типом данных символьного, двоичного или конкретного источника данных либо для отправки двоичных данных c в столбец с символьным, двоичным типом данных или данными определенного источника данных.|  
|HY020|Попытка сцепления значения NULL|**SQLPutData** был вызван более одного раза с момента вызова, который вернул SQL_NEED_DATA, и в одном из этих вызовов аргумент *StrLen_Or_Ind* содержал SQL_NULL_DATA или SQL_DEFAULT_PARAM.|  
|HY090|Недопустимая длина строки или буфера|Аргумент *датаптр* не был пустым указателем, а аргумент *StrLen_Or_Ind* был меньше 0, но не равен SQL_NTS или SQL_NULL_DATA.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
|IM017|Опрос отключен в режиме асинхронного уведомления|При использовании модели уведомления опрос отключен.|  
|IM018|**Склкомплетеасинк** не был вызван для завершения предыдущей асинхронной операции с этим обработчиком.|Если предыдущий вызов функции в обработчике возвращает SQL_STILL_EXECUTING и если включен режим уведомления, то для обработки после обработки и завершения операции необходимо вызвать **склкомплетеасинк** .|  
  
 Если при отправке данных для параметра в инструкции SQL вызывается **SQLPutData** , он может вернуть любое значение SQLSTATE, которое может быть возвращено функцией, вызываемой для выполнения инструкции (**SQLExecute** или **SQLExecDirect**). При вызове во время отправки данных для столбца, обновляемого или добавляемого с помощью **SQLBulkOperations** или обновляемого с помощью функции **SQLSetPos**, он может вернуть любое значение SQLSTATE, которое может быть возвращено **SQLBulkOperations** или **SQLSetPos**.  
  
## <a name="comments"></a>Комментарии  
 **SQLPutData** можно вызвать для предоставления данных на выполнение для двух целей: данные параметров, которые будут использоваться при вызове **SQLExecute** или **SQLExecDirect**, или данные столбца, которые будут использоваться при обновлении или добавлении строки путем вызова **SQLBulkOperations** или обновления посредством вызова функции **SQLSetPos**.  
  
 Когда приложение вызывает **метод SQLParamData** , чтобы определить, какие данные должны быть отправлены, драйвер возвращает индикатор, который приложение может использовать для определения того, какие данные параметров следует отправить или где можно найти данные столбца. Он также возвращает SQL_NEED_DATA, который является индикатором для приложения, которое должно вызывать **SQLPutData** для отправки данных. В аргументе *датаптр* для **SQLPutData**приложение передает указатель на буфер, содержащий фактические данные для параметра или столбца.  
  
 Когда драйвер возвращает SQL_SUCCESS для **SQLPutData**, приложение вызывает **метод SQLParamData** снова. **Метод SQLParamData** возвращает SQL_NEED_DATA если требуется отправить больше данных, в этом случае приложение вызывает **SQLPutData** снова. Он возвращает SQL_SUCCESS, если все данные, выполняемые при выполнении, были отправлены. Затем приложение вызывает **метод SQLParamData** еще раз. Если драйвер возвращает SQL_NEED_DATA и другой индикатор в * \*валуептрптр*, он требует данные для другого параметра или столбца, и **SQLPutData** вызывается снова. Если драйвер возвращает SQL_SUCCESS, то все данные, выполняемые при выполнении, были отправлены, и можно выполнить инструкцию SQL или обработать вызов **SQLBulkOperations** или **SQLSetPos** .  
  
 Дополнительные сведения о передаче данных параметров при выполнении во время выполнения инструкции см. в разделе "передача значений параметров" в [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) и [Отправка длинных данных](../../../odbc/reference/develop-app/sending-long-data.md). Дополнительные сведения о том, как обновляются или добавляются данные в столбцах данных, см. в подразделе «Использование SQLSetPos» раздела [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), «выполнение массовых обновлений с помощью закладок» в [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)и « [Long Data](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)», «SQLSetPos» и «SQLBulkOperations».  
  
> [!NOTE]  
>  Приложение может использовать **SQLPutData** для отправки данных частями только при отправке символьных данных c в столбец с типом данных символьного, двоичного или конкретного источника данных, а также при отправке двоичных данных c в столбец с символьным, двоичным типом данных или данными, зависящими от источника данных. Если **SQLPutData** вызывается более одного раза при любых других условиях, он возвращает SQL_ERROR и SQLSTATE HY019 (несимвольные и недвоичные данные, отправляемые в части).  
  
## <a name="example"></a>Пример  
 В следующем примере предполагается, что имя источника данных — test. Связанная база данных должна иметь таблицу, которую можно создать следующим образом:  
  
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
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Привязка буфера к параметру|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Исполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Исполнение подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Возврат следующего параметра для отправки данных|[Функция SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
