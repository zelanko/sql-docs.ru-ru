---
description: Использование драйвера ODBC для Visual FoxPro с приложением C или Visual C++
title: Использование драйвера ODBC для Visual FoxPro с C или Visual C++ приложением | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- FoxPro ODBC driver [ODBC], C or C++ applications
- C++ applications [ODBC]
- Visual FoxPro ODBC driver [ODBC], C or C++ applications
- Visual FoxPro data [ODBC], C or C++ applications
- C applications [ODBC]
ms.assetid: beb11a68-849e-4fe0-b217-d3722b1b1389
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d8e7dcbc0d14dfddb4aa8a2318d424dc6c7222e5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471296"
---
# <a name="use-the-visual-foxpro-odbc-driver-with-your-c-or-visual-c-application"></a>Использование драйвера ODBC для Visual FoxPro с приложением C или Visual C++
Приложение C или C++ взаимодействует с данными Visual FoxPro, отправляя инструкцию [SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md) или [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md) в Visual FoxPro. Эта инструкция может содержать следующее:  
  
-   Инструкции SQL, которые являются собственными для языка Visual FoxPro, такие как команда [DROP TABLE](../../odbc/microsoft/drop-table-command.md) .  
  
-   [Поддерживаемая грамматика ODBC SQL](../../odbc/microsoft/supported-odbc-sql-grammar-visual-foxpro-odbc-driver.md).  
  
-   Язык, отличный от языка SQL Visual FoxPro, такой как [Поддерживаемые команды Set](../../odbc/microsoft/supported-set-commands-visual-foxpro-odbc-driver.md).  
  
 Дополнительные сведения о SQL Native для Visual FoxPro см. в документации по Visual FoxPro.  
  
## <a name="example-using-the-visual-foxpro-odbc-driver-with-your-c-or-c-application"></a>Пример. Использование драйвера ODBC для Visual FoxPro с приложением C или C++  
 В следующем примере используется ODBC C API для получения данных, хранящихся в поле last_name таблицы Employee в образце базы данных Microsoft® Visual FoxPro с именем Тастраде. Эта база данных предоставляется в Visual FoxPro и устанавливается по умолчанию в следующем расположении:  
  
 `c:\vfp\samples\mainsamp\data\tastrade.dbc`  
  
 В этом примере отображается по одному фамилии за раз, что позволяет нажать кнопку ОК в окне сообщения, чтобы увидеть имя следующего фамилии. Предполагается, что источник данных с именем Тастраде настроен для использования базы данных Тастраде. DBC.  
  
> [!NOTE]  
>  Проверка ошибок должна выполняться для всех вызовов API ODBC; Этот пример исключает проверку ошибок для краткости.  
  
```  
// FoxPro_ODBC_Driver_with_C.cpp  
// compile with: odbc32.lib user32.lib /c  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <stdio.h>  
#include <mbstring.h>  
  
#define MAX_DATA 100  
#define MYSQLSUCCESS(rc) ((rc==SQL_SUCCESS)||(rc==SQL_SUCCESS_WITH_INFO))  
  
class direxec {  
   RETCODE rc;        // ODBC return code  
   HENV henv;         // Environment     
   HDBC hdbc;         // Connection handle  
   HSTMT hstmt;       // Statement handle  
   unsigned char szData[MAX_DATA];   // Returned data storage  
   SDWORD cbData;     // Output length of data  
   unsigned char chr_ds_name[SQL_MAX_DSN_LENGTH];   // Data source name  
  
public:  
   direxec();           // Constructor  
   void sqlconn();      // Allocate env, stat, and conn  
   void sqlexec(unsigned char *);   // Execute SQL statement  
   void sqldisconn();   // Free pointers to env, stat, conn, and disconnect  
   void error_out();    // Displays errors  
};  
  
// Constructor initializes the string chr_ds_name with the data source name.  
direxec::direxec() {  
   _mbscpy_s(chr_ds_name, (const unsigned char *)"tastrade");  
}  
  
// Allocate environment handle, allocate connection handle,  
// connect to data source, and allocate statement handle.  
void direxec::sqlconn() {  
   SQLAllocEnv(&henv);  
   SQLAllocConnect(henv, &hdbc);  
   rc=SQLConnect(hdbc, chr_ds_name, SQL_NTS, NULL, 0, NULL, 0);  
  
   // Deallocate handles, display error message, and exit.  
   if (!MYSQLSUCCESS(rc)) {  
      SQLFreeEnv(henv);  
      SQLFreeConnect(hdbc);  
      error_out();  
      exit(-1);  
   }  
  
   rc = SQLAllocStmt(hdbc, &hstmt);  
}  
  
// Execute SQL command with SQLExecDirect() ODBC API.  
void direxec::sqlexec(unsigned char * cmdstr) {  
   rc = SQLExecDirect(hstmt, cmdstr, SQL_NTS);  
   if (!MYSQLSUCCESS(rc)) {   // Error  
      error_out();  
      // Deallocate handles and disconnect.  
      SQLFreeStmt(hstmt, SQL_DROP);  
      SQLDisconnect(hdbc);  
      SQLFreeConnect(hdbc);  
      SQLFreeEnv(henv);  
      exit(-1);  
   }  
   else {  
      for (rc = SQLFetch(hstmt) ; rc == SQL_SUCCESS; rc=SQLFetch(hstmt)) {  
         SQLGetData(hstmt, 1, SQL_C_CHAR, szData, sizeof(szData), &cbData);  
         // In this example, the data is returned in a messagebox for  
         // simplicity. However, normally the SQLBindCol() ODBC API could  
         // be called to bind individual data rows and assign for a rowset.  
         MessageBox(NULL, (const char *)szData, "ODBC", MB_OK);  
      }  
   }  
}  
  
// Free the statement handle, disconnect, free the connection handle, and  
// free the environment handle.  
void direxec::sqldisconn() {  
   SQLFreeStmt(hstmt, SQL_DROP);  
   SQLDisconnect(hdbc);  
   SQLFreeConnect(hdbc);  
   SQLFreeEnv(henv);  
}  
  
// Display error message in a message box that has an OK button.  
void direxec::error_out() {  
   unsigned char szSQLSTATE[10];  
   SDWORD nErr;  
   unsigned char msg[SQL_MAX_MESSAGE_LENGTH + 1];  
   SWORD cbmsg;  
  
   while(SQLError(0, 0, hstmt, szSQLSTATE, &nErr, msg, sizeof(msg), &cbmsg) == SQL_SUCCESS) {  
      sprintf_s((char *)szData, MAX_DATA, "Error:\nSQLSTATE=%s, Native error=%ld, msg='%s'",   
         szSQLSTATE, nErr, msg);  
  
      MessageBox(NULL, (const char *)szData, "ODBC Error", MB_OK);  
   }  
}  
  
int main (){  
   // Declare an instance of the direxec object.  
   direxec x;  
  
   // Allocate handles and connect.  
   x.sqlconn();  
  
   // Execute SQL command "SELECT last_name FROM employee".  
   x.sqlexec((UCHAR FAR *)"SELECT last_name FROM employee");  
  
   // Free handles, and disconnect.  
   x.sqldisconn();  
  
   // Return success code; example executed successfully.  
   return (TRUE);  
}  
```
