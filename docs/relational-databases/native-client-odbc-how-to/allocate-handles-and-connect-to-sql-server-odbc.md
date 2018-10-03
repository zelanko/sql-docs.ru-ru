---
title: Выделение дескрипторов и подключение к SQL Server (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dfccae77af978ad0422d6eae0ca965624c8ee615
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602672"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>Выделение дескрипторов и соединение с SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>Выделение дескрипторов и соединение с SQL Server  
  
1.  Включите файлы заголовка ODBC Sql.h, Sqlext.h, Sqltypes.h.  
  
2.  Включите зависящий от драйвера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл заголовка Odbcss.h.  
  
3.  Вызовите [SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396) с **HandleType** из SQL_HANDLE_ENV, для инициализации ODBC и выделить дескриптор среды.  
  
4.  Вызовите [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) с **атрибут** значение SQL_ATTR_ODBC_VERSION и **ValuePtr** присвоено значение SQL_OV_ODBC3 для указания, то приложение будет использовать функции ODBC 3.x-format вызовы.  
  
5.  Можно также вызвать [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) задать другой среде, параметры или вызов [SQLGetEnvAttr](http://go.microsoft.com/fwlink/?LinkId=58403) для их получения.  
  
6.  Вызовите [SQLAllocHandle](http://go.microsoft.com/fwlink/?LinkId=58396) с **HandleType** из SQL_HANDLE_DBC выделить дескриптор соединения.  
  
7.  Можно также вызвать [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) для установки параметров соединения, или вызов [SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) для их получения.  
  
8.  Вызовите SQLConnect для использования существующего источника данных для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     либо  
  
     Вызовите [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) использовать строку подключения для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Минимальная строка соединения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет одну из двух форм:  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     Если строка подключения не завершена, **SQLDriverConnect** можно ввести запрос необходимые сведения. Это поведение управляется значение, указанное для *DriverCompletion* параметра.  
  
     \- или -  
  
     Вызовите [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) несколько раз в итеративно для создания строки подключения и подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
9. Можно также вызвать [SQLGetInfo](../../relational-databases/native-client-odbc-api/sqlgetinfo.md) для получения атрибутов и поведения для драйвера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных.  
  
10. Выделите и используйте инструкции.  
  
11. Вызовите SQLDisconnect отключиться от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сделать дескриптор соединения доступным для нового соединения.  
  
12. Вызовите [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) с **HandleType** из SQL_HANDLE_DBC для освобождения дескриптора соединения.  
  
13. Вызовите **SQLFreeHandle** с **HandleType** из SQL_HANDLE_ENV, для освобождения дескриптора среды.  
  
> [!IMPORTANT]  
>  По возможности используйте аутентификацию Windows. Если проверка подлинности Windows недоступна, запросите у пользователя ввод учетных данных во время выполнения. Избегайте хранения учетных данных в файле. Если необходимо сохранить учетные данные, зашифруйте их с помощью [API-интерфейса шифрования Win32](http://go.microsoft.com/fwlink/?LinkId=64532).  
  
## <a name="example"></a>Пример  
 В этом примере показан вызов **SQLDriverConnect** для подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] без использования существующего источника данных ODBC. Путем передачи незавершенной строки соединения для **SQLDriverConnect**, он заставляет драйвер ODBC для запроса пользователя на ввод отсутствующих сведений.  
  
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
  
  
