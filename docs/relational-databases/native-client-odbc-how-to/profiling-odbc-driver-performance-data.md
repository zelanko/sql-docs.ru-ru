---
title: Данные о производительности драйверов профиля (ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- driver performance data [ODBC]
ms.assetid: b997790a-8cc6-4800-8867-74c1bef07be3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b9fa6612f7a9cf0a3e4f26ae4aa42623ec56b268
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282090"
---
# <a name="profiling-odbc-driver-performance-data"></a>Создание профилей данных производительности драйвера ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этом образце показаны параметры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для драйвера ODBC, относящиеся к сбору статистики производительности. Образец создает один файл: odbcperf.log. Этот образец показывает и создание файла журнала со сведениями о производительности, и отображение сведений о производительности непосредственно из структуры данных SQLPERF (структура SQLPERF определена в файле Odbcss.h.). Этот образец разработан для ODBC версии 3.0 или более поздней.  
  
> [!IMPORTANT]  
>  По возможности используйте аутентификацию Windows. Если проверка подлинности Windows недоступна, запросите у пользователя ввод учетных данных во время выполнения. Избегайте хранения учетных данных в файле. Если необходимо сохранить учетные данные, зашифруйте их с помощью [API-интерфейса шифрования Win32](https://go.microsoft.com/fwlink/?LinkId=64532).  
  
### <a name="to-log-driver-performance-data-using-odbc-administrator"></a>Запись сведений о производительности драйвера при помощи администратора ODBC  
  
1.  В **панели управления**, дважды нажмите **административные инструменты,** а затем дважды нажмите на **источники данных (ODBC)**. Можно также вызвать программу odbcad32.exe.  
  
2.  Нажмите на вкладку **Пользователя DSN,** **System DSN**или **файл DSN.**  
  
3.  Щелкните источник данных, для которого необходимо заносить в журнал производительность.  
  
4.  Щелкните **Настройка**.  
  
5.  В сервере Microsoft S'L Configure DSN Wizard перейдите на страницу со **статистикой драйверов журнала ODBC в файл журнала.**  
  
6.  Выберите **статистику драйвера журнала ODBC в файл журнала.** В поле укажите имя файла, куда будет записана статистика. Дополнительно нажмите **«Просмотреть»** —свяжет— файловую систему для журнала статистики.  
  
### <a name="to-log-driver-performance-data-programmatically"></a>Программная запись сведений о производительности драйвера  
  
1.  Позвоните в [S'LSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_PERF_DATA_LOG и полным маршрутом и именем файла данных производительности. Пример:  
  
    ```  
    "C:\\Odbcperf.log"  
    ```  
  
2.  Позвоните в [S'LSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_PERF_DATA и SQL_PERF_START, чтобы начать регистрацию данных о производительности.  
  
3.  Дополнительно позвоните в [s'LSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_LOG_NOW и NULL, чтобы записать в файл журнала данных о производительности запись, раздеченную для вкладок. Это можно делать каждый раз при запуске приложения.  
  
4.  Позвоните в [s'LSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_PERF_DATA и SQL_PERF_STOP, чтобы остановить регистрацию данных о производительности.  
  
### <a name="to-pull-driver-performance-data-into-an-application"></a>Получение в приложение данных о производительности  
  
1.  Позвоните в [S'LSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_PERF_DATA и SQL_PERF_START, чтобы начать профилирование данных о производительности.  
  
2.  Позвоните в [S'LGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) с SQL_COPT_SS_PERF_DATA и адресом указателя на структуру S'LPERF. Первый такой вызов установит указатель на адрес допустимой структуры SQLPERF, содержащей текущие сведения о производительности. Драйвер не обновляет непрерывно данные в структуре производительности. Приложение должно повторять вызов в [S'LGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) в любое время, когда ему необходимо обновить структуру с более актуальными данными о производительности.  
  
3.  Позвоните в [s'LSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_PERF_DATA и SQL_PERF_STOP, чтобы остановить регистрацию данных о производительности.  
  
## <a name="example"></a>Пример  
 Также необходим источник данных ODBC с именем AdventureWorks, для которого базой данных по умолчанию является образец базы данных AdventureWorks. (Вы можете скачать образную базу данных AdventureWorks с домашней [страницы microsoft S'L Server Samples and Community Projects.)](https://go.microsoft.com/fwlink/?LinkID=85384) Этот источник данных должен быть основан на драйвере ODBC, поставляемом операционной системой (имя драйвера — «Сервер» (S'L Server). При построении и запуске этого образца как 32-разрядного приложения в 64-разрядной операционной системе необходимо создать источник данных ODBC с помощью программы администрирования ODBC (исполняемый файл %windir%\SysWOW64\odbcad32.exe).  
  
 Этот образец соединяется с установленным на компьютер экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию. Чтобы соединиться с именованным экземпляром, измените определение источника данных ODBC, указав экземпляр в следующем формате: Сервер\ИменованныйЭкземпляр. По умолчанию [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] устанавливается на именованный экземпляр.  
  
 Скомпилируйте с библиотекой odbc32.lib.  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
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
  
   // Pointer to the ODBC driver performance structure.  
   SQLPERF *PerfPtr;  
   SQLINTEGER cbPerfPtr;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // This sample use Integrated Security. Please create the SQL Server   
   // DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log performance statistics.  Specify file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG, &"odbcperf.log", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the performance statistics log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle, then execute command.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Write current statistics to the performance log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG_NOW, (SQLPOINTER)NULL, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Get pointer to current SQLPerf structure.  
   // Print a couple of statistics.  
   retcode =   
      SQLGetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)&PerfPtr, SQL_IS_POINTER, &cbPerfPtr);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLGetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("SQLSelects = %d, SQLSelectRows = %d\n", PerfPtr->SQLSelects, PerfPtr->SQLSelectRows);  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Профилирование производительности драйвера ODBC Как-к темам &#40;&#41;ODBC](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-odbc.md)   
 [Создание профилей производительности драйвера ODBC](../../relational-databases/native-client/odbc/profiling-odbc-driver-performance.md)  
  
  
