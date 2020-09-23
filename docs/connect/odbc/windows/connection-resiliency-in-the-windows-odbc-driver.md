---
title: Устойчивость подключения в драйвере ODBC в Windows
description: Узнайте, как функция устойчивости подключений в драйвере ODBC обеспечивает прозрачное восстановление соединений и улучшает работу приложения, когда сервер закрывает бездействующие подключения.
ms.custom: ''
ms.date: 09/01/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 614fa0b4-e9fd-4c68-aab3-183f9b9df143
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01b8da5d2a7f7c0e49d54a9fe237367ab3ed405f
ms.sourcegitcommit: b6ee0d434b3e42384b5d94f1585731fd7d0eff6f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "89288126"
---
# <a name="connection-resiliency-in-the-windows-odbc-driver"></a>Устойчивость подключения в драйвере ODBC в Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Чтобы обеспечить сохранение подключения приложений к [!INCLUDE[ssAzure](../../../includes/ssazure_md.md)], драйвер ODBC в Windows может восстанавливать неактивные соединения.  
  
> [!IMPORTANT]  
>  Функция устойчивости подключений поддерживается в Базе данных SQL Microsoft Azure и SQL Server 2014 (и более поздних версий).  
  
 Дополнительные сведения об устойчивости неактивных подключений см. в технической статье [Устойчивость неактивных подключений](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Idle%20Connection%20Resiliency.docx).
  
 Драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Windows имеет два параметра для управления поведением повторного подключения.  
  
-   Число попыток подключения.  
  
     Число попыток подключения управляет количеством повторных попыток подключения в случае сбоя соединения. Допустимы значения от 0 до 255. Ноль (0) означает отсутствие повторных попыток возобновления соединения. Значение по умолчанию — одна попытка повторного подключения.  
  
     Можно изменить число повторных попыток подключения, когда вы:  
  
    -   определяете или изменяете источник данных, использующий драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с элементом управления **Число попыток подключения**;  
  
    -   используете ключевое слово строки подключения **ConnectRetryCount** .  
  
     Чтобы получить количество повторных попыток подключения, используйте атрибут соединения **SQL_COPT_SS_CONNECT_RETRY_COUNT** (только для чтения). Если приложение подключается к серверу, который не поддерживает устойчивость подключений, **SQL_COPT_SS_CONNECT_RETRY_COUNT** возвращает значение 0.  
  
-   Интервал повтора подключения.  
  
     Интервал повтора подключения указывает количество секунд между попытками подключения. Допустимые значения: 1–60. Общее время для повторного подключения не может превышать время ожидания подключения (SQL_ATTR_QUERY_TIMEOUT в SQLSetStmtAttr). Значение по умолчанию — 10 секунд.  
  
     Можно изменить интервал повтора подключения, когда вы:  
  
    -   определяете или изменяете источник данных, использующий драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с элементом управления **Интервал повтора подключения** ;  
  
    -   используете ключевое слово строки подключения **ConnectRetryInterval** .  
  
     Чтобы извлечь продолжительность интервала повтора подключения, используйте атрибут соединения **SQL_COPT_SS_CONNECT_RETRY_INTERVAL** (только для чтения).  
  
 Если приложение устанавливает соединение с SQL_DRIVER_COMPLETE_REQUIRED, а затем пытается выполнить инструкцию через разорванное соединение, драйвер ODBC не отображает это диалоговое окно повторно. Кроме того, во время восстановления наблюдается следующее:  
  
-   Во время восстановления любой вызов **SQLGetConnectAttr(SQL_COPT_SS_CONNECTION_DEAD)** должен возвращать значение **SQL_CD_FALSE**.  
  
-   В случае сбоя восстановления любой вызов **SQLGetConnectAttr(SQL_COPT_SS_CONNECTION_DEAD)** должен возвращать значение **SQL_CD_TRUE**.  
  
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
 Следующий пример содержит две функции. **func1** показывает способ подключения с помощью имени источника данных (DSN), использующего драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Windows. Имя DSN использует проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и задает идентификатор пользователя. Затем **func1** извлекает число повторных попыток подключения с помощью **SQL_COPT_SS_CONNECT_RETRY_COUNT**.  
  
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
  
   SQLCHAR ConnStrIn[MAXBUFLEN] = "DRIVER={ODBC Driver 17 for SQL Server};SERVER=server_that_supports_connection_resiliency;UID=userID;PWD= password_for_userID;ConnectRetryCount=2";
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
  
## <a name="see-also"></a>См. также:  
 [Драйвер Microsoft ODBC Driver for SQL Server в Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
