---
title: Устойчивость подключения в драйвере ODBC для Windows | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 614fa0b4-e9fd-4c68-aab3-183f9b9df143
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 818cea769cc7ed18b161506e75e3d0b0dd938592
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connection-resiliency-in-the-windows-odbc-driver"></a>Устойчивость подключения в драйвере ODBC в Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Чтобы обеспечить сохранение подключения приложений [!INCLUDE[ssAzure](../../../includes/ssazure_md.md)], драйвер ODBC для Windows может восстанавливать неактивные соединения.  
  
> [!IMPORTANT]  
>  Функция устойчивости подключений поддерживается в Базах данных SQL Microsoft Azure и SQL Server 2014 (и более поздних версий).  
  
 Дополнительные сведения об устойчивости неактивных подключений см. в разделе [Техническая статья — устойчивость неактивных подключений](http://go.microsoft.com/fwlink/?LinkId=393996).  
  
 Драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows имеет два параметра для управления поведением повторного подключения:  
  
-   Число попыток подключения.  
  
     Число попыток подключения управляет количеством повторных попыток подключения в случае сбоя соединения. Допустимы значения от 0 до 255. Ноль (0) означает отсутствие повторных попыток возобновления соединения. Значение по умолчанию — одна попытка повторного подключения.  
  
     Можно изменить число повторных попыток подключения, когда вы:  
  
    -   определяете или изменяете источник данных, использующий драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] с элементом управления **Число попыток подключения** ;  
  
    -   используете ключевое слово строки подключения **ConnectRetryCount** .  
  
     Чтобы извлечь количество повторных попыток подключения, используйте **SQL_COPT_SS_CONNECT_RETRY_COUNT** (только для чтения) атрибут соединения. Если приложение подключается к серверу, который не поддерживает устойчивость подключений, **SQL_COPT_SS_CONNECT_RETRY_COUNT** возвращает 0.  
  
-   Интервал повтора подключения.  
  
     Интервал повтора подключения указывает количество секунд между попытками подключения. Допустимы значения от 1 до 60. Общее время для повторного подключения не может превышать время ожидания подключения (SQL_ATTR_QUERY_TIMEOUT в SQLSetStmtAttr). Значение по умолчанию — 10 секунд.  
  
     Можно изменить интервал повтора подключения, когда вы:  
  
    -   определяете или изменяете источник данных, использующий драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] с элементом управления **Интервал повтора подключения** ;  
  
    -   используете ключевое слово строки подключения **ConnectRetryInterval** .  
  
     Чтобы извлечь продолжительность интервала повтора подключения, используйте **SQL_COPT_SS_CONNECT_RETRY_INTERVAL** (только для чтения) атрибут соединения.  
  
 Если приложение устанавливает соединение с SQL_DRIVER_COMPLETE_REQUIRED, а затем пытается выполнить инструкцию через разорванное соединение, драйвер ODBC не отображает это диалоговое окно повторно. Кроме того, во время восстановления наблюдается следующее:  
  
-   Во время восстановления любой вызов **SQLGetConnectAttr(SQL_COPT_SS_CONNECTION_DEAD)**, должны возвращать **SQL_CD_FALSE**.  
  
-   Если в случае сбоя восстановления любой вызов **SQLGetConnectAttr(SQL_COPT_SS_CONNECTION_DEAD)**, должны возвращать **SQL_CD_TRUE**.  
  
 Любая функция, которая выполняет команду на сервере, возвращает следующие коды состояния:  
  
|Состояние|Сообщение|  
|-----------|-------------|  
|IMC01|Подключение разорвано, и восстановление невозможно. Драйвер клиента один или несколько раз попытался восстановить соединение, и все попытки завершились со сбоем. Увеличьте значение ConnectRetryCount, чтобы увеличить количество попыток восстановления.|  
|IMC02|Сервер не подтвердил попытку восстановления, восстановление соединения невозможно.|  
|IMC03|Сервер не сохранил точную версию TDS клиента, запрошенную во время попытки восстановления, восстановление соединения невозможно.|  
|IMC04|Сервер не сохранил точный основной номер версии сервера, запрошенный во время попытки восстановления, восстановление соединения невозможно.|  
|IMC05|Подключение разорвано, и восстановление невозможно. Соединение помечено сервером как невосстанавливаемое. Попытки восстановить соединение не предпринимались.|  
|IMC06|Подключение разорвано, и восстановление невозможно. Соединение помечено клиентом как невосстанавливаемое. Попытки восстановить соединение не предпринимались.|  
  
## <a name="example"></a>Пример  
 Следующий пример содержит две функции. **func1** показывает способ подключения с именем источника данных (DSN), использующий драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Windows. Имя DSN использует проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] и задает идентификатор пользователя. **func1** затем извлекает число повторных попыток подключения с помощью **SQL_COPT_SS_CONNECT_RETRY_COUNT**.  
  
 **func2** использует **SQLDriverConnect**, ключевое слово строки подключения **ConnectRetryCount** и атрибуты соединения, чтобы получить параметр для повторных попыток подключения и интервала повторных попыток.  
  
```  
// Connection_resiliency.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <stdio.h>  
#include <sqlext.h>  
#include <msodbcsql.h>  
  
void func1() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
   SQLSMALLINT i = 21;  

   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLCHAR*) "MyDSN", SQL_NTS, (SQLCHAR*) "userID", SQL_NTS, (SQLCHAR*) "password_for_userID", SQL_NTS);  
            retcode = SQLGetConnectAttr(hdbc, SQL_COPT_SS_CONNECT_RETRY_COUNT, &i, SQL_IS_INTEGER, NULL);  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}
  
void func2() {  
   SQLHENV henv;  
   SQLHDBC hdbc1;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
   SQLSMALLINT i = 21;  
  
#define MAXBUFLEN 255  
  
   SQLCHAR ConnStrIn[MAXBUFLEN] = "DRIVER={ODBC Driver 13 for SQL Server};SERVER=server_that_supports_connection_resiliency;UID=userID;PWD= password_for_userID;ConnectRetryCount=2";
   SQLCHAR ConnStrOut[MAXBUFLEN];

   SQLSMALLINT cbConnStrOut = 0;  
 
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3_80, SQL_IS_INTEGER);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            // SQLSetConnectAttr(hdbc1, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            retcode = SQLDriverConnect(hdbc1, NULL, ConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
         }  
         retcode = SQLGetConnectAttr(hdbc1, SQL_COPT_SS_CONNECT_RETRY_COUNT, &i, SQL_IS_INTEGER, NULL);  
         retcode = SQLGetConnectAttr(hdbc1, SQL_COPT_SS_CONNECT_RETRY_INTERVAL, &i, SQL_IS_INTEGER, NULL);  
      }  
   }  
}  
  
int main() {  
   func1();  
   func2();  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Драйвер Microsoft ODBC для SQL Server в Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
