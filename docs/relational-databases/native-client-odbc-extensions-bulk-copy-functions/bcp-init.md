---
title: bcp_init | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_init
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_init function
ms.assetid: 6a25862c-7f31-4873-ab65-30f3abde89d2
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e47c7c4f5324da021db2624e5e936493fd54ea45
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67895531"
---
# <a name="bcpinit"></a>bcp_init
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Инициализирует операцию массового копирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
RETCODE bcp_init (  
        HDBC hdbc,  
        LPCTSTR szTable,  
        LPCTSTR szDataFile,  
        LPCTSTR szErrorFile,  
        INT eDirection);  
```  
  
## <a name="arguments"></a>Аргументы  
 *HDBC*  
 Дескриптор соединения ODBC с поддержкой массового копирования.  
  
 *szTable*  
 Имя таблицы базы данных, в которую (или из которой) выполняется копирование. Это имя также может включать имя базы данных или владельца. Например **pubs.gracie.titles**, **pubs.. заголовки**, **gracie.titles**, и **заголовки** являются допустимыми именами таблиц.  
  
 Если *eDirection* имеет значение DB_OUT, *szTable* также может быть именем представления базы данных.  
  
 Если *eDirection* имеет значение DB_OUT, и инструкция SELECT указывается с помощью [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) перед [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) вызове **bcp_init** *szTable* должно быть присвоено значение NULL.  
  
 *szdatafile функции*  
 Имя пользовательского файла, в который или из которого выполняется копирование. Если данные копируются напрямую из переменных с помощью [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), задайте *szDataFile* значение NULL.  
  
 *szErrorFile*  
 Имя файла ошибок, заполняемого сообщениями о ходе работы, сообщениями об ошибках и копиями строк, которые по каким-либо причинам не могут быть скопированы из пользовательского файла в таблицу. Если NULL передается как *szErrorFile*, файл ошибок не используется.  
  
 *eDirection*  
 Направление копирования (DB_IN или DB_OUT). Значение DB_IN указывает на копирование из переменных программы или пользовательского файла в таблицу. Значение DB_OUT указывает на копирование из таблицы базы данных в пользовательский файл. Если используется значение DB_OUT, необходимо указать имя пользовательского файла.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 Вызовите **bcp_init** перед вызовом любой другой функции массового копирования. **bcp_init** выполняет необходимую инициализацию массового копирования данных между рабочей станцией и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Bcp_init** функции должно быть указано с дескриптором соединения ODBC, который включен для использования с функциями массового копирования. Чтобы включить дескриптор, используйте [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с параметром SQL_COPT_SS_BCP, в значение SQL_BCP_ON, для подключения выделенного, но не подключенного дескриптора. Попытка назначения атрибута для подключенного дескриптора приведет к ошибке.  
  
 Если указан файл данных, **bcp_init** проверяет структуру базы данных исходной или целевой таблицы, не файл данных. **bcp_init** определяет формат данных для файла данных, на основе каждого столбца в таблице базы данных, представления или результирующего набора инструкции SELECT. Эта спецификация включает тип данных каждого столбца, присутствие или отсутствие длины и допустимости значений NULL и строки байтов признака конца, а также ширину для типов данных с фиксированной длиной. **bcp_init** устанавливает эти значения следующим образом:  
  
-   Указанный тип данных представляет собой тип данных столбца в таблице базы данных, представлении или результирующем наборе SELECT. Тип данных ограничивается собственными типами данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указанными в файле sqlncli.h. Сами данные представляются в машинной форме. То есть данные из столбца **целое число** тип данных представляется с помощью последовательности размером 4 байта, велик- или обратным порядком байтов на используемом компьютере, который создан файл данных.  
  
-   Если тип данных базы данных имеет фиксированную длину, то для данных файла данных также задается фиксированная длина. Функции массового копирования, которые обрабатывают данные (например, [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)) анализируют строки данных, ожидая, что длина данных в файле данных будет идентична длине данных, указанных в таблице базы данных, представления или списка столбцов SELECT. Например, данные для базы данных столбец, определенный как **char(13)** должны быть представлены с 13 символов для каждой строки данных в файле. Данные фиксированной длины могут быть обозначены префиксом с признаком значения NULL, если столбец базы данных допускает значения NULL.  
  
-   После определения последовательности байт, служащей признаком конца, ее длина устанавливается в значение 0.  
  
-   При копировании в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл данных должен содержать данные для каждого столбца таблицы базы данных. При копировании на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данные из всех столбцов в таблице, представлении или результирующем наборе инструкции SELECT базы данных копируются в файл данных.  
  
-   При копировании в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] порядковый номер столбца в файле данных должен совпадать с порядковым номером столбца таблицы базы данных. При копировании из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **bcp_exec** помещает данные, основанные на порядковый номер столбца в таблице базы данных.  
  
-   Если тип данных базы данных имеет переменную длину (например, **varbinary(22)** ) или если столбец базы данных может содержать значения null, данные в файле данных в качестве префикса Признак длины, null. Ширина признака изменяется в зависимости от типа данных и версии массового копирования.  
  
 Чтобы изменить значения форматов данных, указанный для файла данных, вызовите [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) и [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md).  
  
 Массовое копирование в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может быть оптимизировано для таблиц, не содержащих индексов, путем установки модели восстановления базы данных в значение SIMPLE или BULK_LOGGED. Дополнительные сведения см. в разделе [необходимые условия для минимального протоколирования массового импорта](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md) и [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md).  
  
 Если файл данных не используется, необходимо вызвать [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) Чтобы задать формат и местоположение в памяти данных для каждого столбца, затем скопировать строки данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
## <a name="example"></a>Пример  
 В этом образце демонстрируется использование функции ODBC bcp_init с файлом форматирования.  
  
 Перед компиляцией и выполнением кода на С++ необходимо выполнить следующие действия.  
  
-   Создайте источник данных ODBC с именем Test. Его можно сопоставить с любой базой данных.  
  
-   Выполните в базе данных следующую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
    ```  
    CREATE TABLE BCPDate (cola int, colb datetime);  
    ```  
  
-   В каталог, где будет запускаться приложение, добавьте файл Bcpfmt.fmt и добавьте в этот файл следующик код:  
  
    ```  
    8.0  
    2  
    1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
    2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
    ```  
  
-   В каталог, где будет запускаться приложение, добавьте файл Bcpodbc.bcp и добавьте в этот файл следующик код:  
  
    ```  
    1  
    2  
    ```  
  
 Теперь все готово к компиляции и выполнению кода на C++.  
  
```  
// compile with: odbc32.lib sqlncli11.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC;   
  
void Cleanup() {  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
   SDWORD cRows;  
  
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
  
   // Allocate ODBC connection handle, set BCP mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetConnectAttr(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security. Create SQL Server DSN using Windows NT authentication.  
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Read the format file.  
   retcode = bcp_readfmt(hdbc1, "BCPFMT.fmt");  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_readfmt(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_exec(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied in = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
```  
  
## <a name="see-also"></a>См. также  
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
