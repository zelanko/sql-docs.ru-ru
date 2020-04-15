---
title: Выделение ручек и подключение к серверу S'L (ODBC) Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d26af711c07c4ea296d5351d0fcb0d1f9710706
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294529"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>Выделение дескрипторов и соединение с SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>Выделение дескрипторов и соединение с SQL Server  
  
1.  Включите файлы заголовка ODBC Sql.h, Sqlext.h, Sqltypes.h.  
  
2.  Включите зависящий от драйвера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл заголовка Odbcss.h.  
  
3.  Позвоните [в S'LAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) с **помощью SQL_HANDLE_ENV HandleType,** чтобы инициализировать ODBC и выделить ручку среды.  
  
4.  Позвоните [в S'LSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) с **набором attributes,** чтобы SQL_ATTR_ODBC_VERSION и **ValuePtr,** установленным для SQL_OV_ODBC3, чтобы указать, что приложение будет использовать вызовы функции формата ODBC 3.x.  
  
5.  Дополнительно позвоните по [телефону s'LSetEnvAttr,](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) чтобы установить другие параметры среды, или позвоните в [S'LGetEnvAttr,](https://go.microsoft.com/fwlink/?LinkId=58403) чтобы получить параметры среды.  
  
6.  Позвоните [в S'LAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) с **помощью SQL_HANDLE_DBC,** чтобы выделить ручку соединения.  
  
7.  Дополнительно позвоните по [телефону S'LSetConnectAttr,](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) чтобы установить параметры подключения, или позвоните по [s'LGetConnectAttr,](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) чтобы получить варианты подключения.  
  
8.  Позвоните в S'LConnect, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]использовать существующий источник данных для подключения к.  
  
     Или  
  
     Позвоните [в S'LDriverConnect,](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]использовать строку подключения для подключения.  
  
     Минимальная строка соединения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет одну из двух форм:  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     Если строка подключения не завершена, **S'LDriverConnect** может запросить требуемую информацию. Это контролируется значением, указанным для параметра *DriverCompletion.*  
  
     \- или -  
  
     Позвоните [в S'LBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) несколько раз итеративным способом, чтобы построить строку соединения и подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
9. Дополнительно позвоните по [телефону s'LGetInfo,](../../relational-databases/native-client-odbc-api/sqlgetinfo.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] чтобы получить атрибуты драйвера и поведение для источника данных.  
  
10. Выделите и используйте инструкции.  
  
11. Позвоните в S'LDisconnect, чтобы отключиться от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и сделать ручку соединения доступной для нового соединения.  
  
12. Позвоните [в S'LFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) с **помощью SQL_HANDLE_DBC,** чтобы освободить ручку соединения.  
  
13. Позвоните **в S'LFreeHandle** с **помощью SQL_HANDLE_ENV,** чтобы освободить ручку среды.  
  
> [!IMPORTANT]  
>  По возможности используйте аутентификацию Windows. Если проверка подлинности Windows недоступна, запросите у пользователя ввод учетных данных во время выполнения. Избегайте хранения учетных данных в файле. Если необходимо сохранить учетные данные, зашифруйте их с помощью [API-интерфейса шифрования Win32](https://go.microsoft.com/fwlink/?LinkId=64532).  
  
## <a name="example"></a>Пример  
 В этом примере показан вызов на **S'LDriverConnect** для подключения к экземпляру без необходимости существующего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источника данных ODBC. Проходя неполную строку подключения к **S'LDriverConnect,** это приводит к тому, что драйвер ODBC подсказывает пользователю ввести недостающую информацию.  
  
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
  
  
