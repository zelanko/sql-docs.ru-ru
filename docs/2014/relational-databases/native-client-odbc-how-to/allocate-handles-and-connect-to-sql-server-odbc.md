---
title: Выделение дескрипторов и подключитесь к SQL Server (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: adf51bdb9181030079d8b3f94628a1280299c856
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095446"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>Выделение дескрипторов и соединение с SQL Server (ODBC)
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>Выделение дескрипторов и соединение с SQL Server  
  
1.  Включите файлы заголовка ODBC Sql.h, Sqlext.h, Sqltypes.h.  
  
2.  Включите зависящий от драйвера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл заголовка Odbcss.h.  
  
3.  Вызовите [SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396) с `HandleType` установленным в значение sql_handle_env для инициализации ODBC и выделить дескриптор среды.  
  
4.  Вызовите [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) с `Attribute` значение SQL_ATTR_ODBC_VERSION и `ValuePtr` присвоено значение SQL_OV_ODBC3 для указания того, приложение будет использовать вызовы функций ODBC 3.x формата.  
  
5.  При необходимости вызовите [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) задать среду другие параметры, либо вызовите [SQLGetEnvAttr](http://go.microsoft.com/fwlink/?LinkId=58403) для их получения.  
  
6.  Вызовите [SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396) с `HandleType` из SQL_HANDLE_DBC, чтобы выделить дескриптор подключения.  
  
7.  При необходимости вызовите [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) для установки параметров соединения, либо вызовите [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) для получения параметров подключения.  
  
8.  Вызовите SQLConnect для использования существующего источника данных для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     либо  
  
     Вызовите [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) использовать строку подключения для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Минимальная строка соединения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет одну из двух форм:  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     Если строка подключения не полная, функция `SQLDriverConnect` может запросить требуемые сведения. Это поведение управляется значение, указанное для *DriverCompletion* параметра.  
  
     \- или -  
  
     Вызовите [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md) несколько раз итеративно для создания строки подключения и подключения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
9. При необходимости вызовите [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md) получение атрибутов драйвера и поведение для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных.  
  
10. Выделите и используйте инструкции.  
  
11. Вызовите SQLDisconnect для отключения от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сделать дескриптор соединения доступным для нового соединения.  
  
12. Вызовите [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) с `HandleType` установленным в значение sql_handle_dbc для освобождения дескриптора соединения.  
  
13. Для освобождения дескриптора среды вызовите функцию `SQLFreeHandle` с параметром `HandleType`, установленным в значение SQL_HANDLE_ENV.  
  
> [!IMPORTANT]  
>  По возможности используйте аутентификацию Windows. Если проверка подлинности Windows недоступна, запросите у пользователя ввод учетных данных во время выполнения. Избегайте хранения учетных данных в файле. Если необходимо сохранить учетные данные, зашифруйте их с помощью [API-интерфейса шифрования Win32](http://go.microsoft.com/fwlink/?LinkId=64532).  
  
## <a name="example"></a>Пример  
 В этом примере показано, как вызывать функцию `SQLDriverConnect` для соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] без необходимости в существовании источника данных ODBC. Передача функции `SQLDriverConnect` незавершенной строки соединения приводит к запросу драйвера ODBC к пользователю на ввод отсутствующих сведений.  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  