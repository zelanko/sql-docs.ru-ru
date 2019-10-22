---
title: Групповое копирование с помощью файла форматирования (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy using format file [ODBC]
- ODBC, bulk copy operations
ms.assetid: 970fd3af-f918-4fc3-a5b1-92596515d4de
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2dc0ac57b132a0e681337b358a951a0e33f56db
ms.sourcegitcommit: 82a1ad732fb31d5fa4368c6270185c3f99827c97
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688909"
---
# <a name="bulk-copy-by-using-a-format-file-odbc"></a>Выполнение массового копирования при использовании файла форматирования (ODBC)
  В этом образце демонстрируется использование функции ODBC bcp_init с файлом форматирования.  
  
### <a name="to-bulk-copy-by-using-a-format-file"></a>Массовое копирование с использованием файла форматирования  
  
1.  Выделите дескриптор среды и дескриптор соединения.  
  
2.  Включите операцию массового копирования, укажите параметры SQL_COPT_SS_BCP и SQL_BCP_ON.  
  
3.  Подключитесь к Microsoft SQL Server.  
  
4.  Вызовите [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) , чтобы задать следующие сведения:  
  
    -   Имя таблицы или представления, из которого или в которое будет производиться массовое копирование.  
  
    -   Имя файла данных, в котором содержатся данные для копирования в базу данных или который получает данные при копировании из базы данных.  
  
    -   Имя файла данных, в который сохраняются все сообщения об ошибках массового копирования (укажите значение NULL, если файл для сообщений не требуется).  
  
    -   Направление копирования: DB_IN из файла в таблицу или представление.  
  
5.  Вызовите [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) , чтобы прочитать файл форматирования, описывающий файл данных, который будет использоваться операцией копирования.  
  
6.  Вызовите [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) , чтобы выполнить операцию с массовым копированием.  
  
## <a name="example"></a>Пример  
 Этот образец не поддерживается на архитектуре IA64.  
  
 Также необходим источник данных ODBC с именем AdventureWorks, для которого базой данных по умолчанию является образец базы данных AdventureWorks. (Образец базы данных AdventureWorks можно скачать на домашней странице [Microsoft SQL Server примеры и проекты сообщества](https://go.microsoft.com/fwlink/?LinkID=85384) .) Этот источник данных должен быть основан на драйвере ODBC, предоставленном операционной системой (имя драйвера — "SQL Server"). При построении и запуске этого образца как 32-разрядного приложения в 64-разрядной операционной системе необходимо создать источник данных ODBC с помощью программы администрирования ODBC (исполняемый файл %windir%\SysWOW64\odbcad32.exe).  
  
 Этот образец соединяется с установленным на компьютер экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по умолчанию. Чтобы соединиться с именованным экземпляром, измените определение источника данных ODBC, указав экземпляр в следующем формате: Сервер\ИменованныйЭкземпляр. По умолчанию [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] устанавливается на именованный экземпляр.  
  
 Выполните первый листинг кода ([!INCLUDE[tsql](../../../includes/tsql-md.md)]), чтобы создать таблицу, которой пользуется образец.  
  
 Скопируйте второй листинг кода и вставьте его в файл Bcpfmt.fmt. Каждый столбец в таблице отделен символом табуляции.  
  
 Скопируйте третий листинг кода и вставьте его в файл Bcpodbc.bcp. Каждому возврату каретки в файле предшествует символ табуляции.  
  
 Скомпилируйте четвертый листинг кода (C++) с библиотеками odbc32.lib и odbcbcp.lib. При работе с программой MSBuild.exe сначала скопируйте файлы Bcpfmt.fmt и Bcpodbc.bcp из каталога проекта в тот каталог, где находится исполняемый файл, а затем вызовите этот исполняемый файл.  
  
 Выполните пятый листинг кода ([!INCLUDE[tsql](../../../includes/tsql-md.md)]), чтобы удалить таблицу, которую использовал образец.  
  
```sql
use AdventureWorks  
CREATE TABLE BCPDate (cola int, colb datetime)  
```  
  
```  
8.0  
2  
1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
```  
  
```  
1  
2  
```  
  
```cpp
// compile with: odbc32.lib odbcbcp.lib  
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
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
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
  
```sql
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
```  
  
## <a name="see-also"></a>См. также статью  
 [Инструкции по копированию с помощью драйвера ODBC для SQL Server &#40;ODBC&#41; ](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md)    
 [Использование файлов данных и файлов форматирования](../../native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
  
