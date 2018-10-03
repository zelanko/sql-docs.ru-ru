---
title: С помощью SQL Server Native Client файлов заголовков и библиотек | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- header files [SQL Server Native Client]
- SQLNCLI, header files
- OLE DB, header files
- library files [SQL Server Native Client]
- SQL Server Native Client, header files
- data access [SQL Server Native Client], header files
- SQL Server Native Client ODBC driver,header files
- data access [SQL Server Native Client], library files
- SQL Server Native Client, library files
- ODBC applications, header files
- SQLNCLI, library files
ms.assetid: 69889a98-7740-4667-aecd-adfc0b37f6f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 800b3e43129bba36db0836f9a58a3ad1e47b40c1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141184"
---
# <a name="using-the-sql-server-native-client-header-and-library-files"></a>Использование файлов заголовков и библиотек собственного клиента SQL Server
  Файлы заголовка и библиотеки собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливаются с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. При разработке приложения важно скопировать и установить все требуемые файлы для работы среды разработки. Дополнительные сведения об установке и распространении [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, см. в разделе [Установка SQL Server Native Client](installing-sql-server-native-client.md).  
  
 Файлы заголовка и библиотеки собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливаются в следующий каталог.  
  
 *% PROGRAM FILES %* \Microsoft SQL Server\110\SDK  
  
 Файл заголовка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (sqlncli.h) можно использовать для добавления в пользовательские приложения функциональных возможностей по доступу к данным собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Файл заголовка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] содержит все определения, атрибуты, свойства и интерфейсы, необходимые для использования новых функций, представленных в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 В дополнение к файлу заголовка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], существует также файл библиотеки sqlncli11.lib, являющийся библиотекой экспорта для функций массового копирования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (BCP) для ODBC.  
  
 Файл заголовка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имеет обратную совместимость с обоими файлами sqloledb.h и odbcss.h, используемыми компонентами доступа к данным MDAC, но не содержит идентификаторов CLSID для SQLOLEDB (поставщик OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], включенный с компонентами MDAC) или символов для функциональных возможностей XML (которые не поддерживаются собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
 Приложения ODBC не могут ссылаться на заголовок собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (sqlncli.h) и odbcss.h в одной программе. Даже если ни одна из возможностей, представленных в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], не используется, файл заголовка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно использовать вместо старого файла odbcss.h.  
  
 Приложениям OLE DB, использующим поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], необходима ссылка только на файл sqlncli.h. Если приложение использует и компоненты MDAC (SQLOLEDB), и поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], оно может ссылаться как на sqloledb.h, так и на sqlncli.h при условии, что ссылка на файл sqloledb.h будет идти первой.  
  
## <a name="using-the-sql-server-native-client-header-file"></a>Использование файла заголовка собственного клиента SQL Server  
 Для использования файла заголовка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо использовать инструкцию `include` в программном коде на C/C++. В следующих подразделах описано, как это сделать для приложений OLE DB и ODBC.  
  
> [!NOTE]  
>  Файлы заголовка и библиотеки собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] могут быть скомпилированы только с помощью компилятора C++ среды Visual Studio 2002 или более поздней версии.  
  
### <a name="ole-db"></a>OLE DB  
 Чтобы использовать файл заголовка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в приложении OLE DB, вставьте в программный код следующие строки:  
  
```  
#define _SQLNCLI_OLEDB_  
include "sqlncli.h";  
```  
  
> [!NOTE]  
>  Если приложение использует оба API-интерфейса (OLE DB и ODBC), то первая строка приведенного выше кода должна быть пропущена. Кроме того, если приложение содержит инструкцию `include` для файла sqloledb.h, то инструкция `include` для файла sqlncli.h должна идти после нее.  
  
 При создании соединения с источником данных с помощью собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используйте в качестве строки имени поставщика «SQLNCLI11».  
  
### <a name="odbc"></a>интерфейс ODBC  
 Чтобы использовать файл заголовка собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в приложении ODBC, вставьте в программный код следующие строки:  
  
```  
#define _SQLNCLI_ODBC_  
include "sqlncli.h";  
```  
  
> [!NOTE]  
>  Если приложение использует оба API-интерфейса (OLE DB и ODBC), то первая строка приведенного выше кода должна быть пропущена. Кроме того, если приложение содержит инструкцию `#include` для файла odbcss.h, ее нужно удалить.  
  
 При создании соединения с источником данных с помощью собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используйте в качестве строки имени драйвера «SQL Server Native Client 11.0».  
  
## <a name="component-names-and-properties-by-version"></a>Имена и свойства компонентов в зависимости от версии  
  
|Свойство|собственный клиент SQL Server<br /><br /> SQL Server 2005|SQL Server Native Client 10.0<br /><br /> SQL Server 2008|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]|MDAC|  
|--------------|--------------------------------------------------|-------------------------------------------------------|---------------------------------------------------------------|----------|  
|Имя драйвера ODBC|Собственный клиент SQL|SQL Server Native Client 10.0|SQL Server Native Client 11.0|SQL Server|  
|Имя файла заголовка ODBC|Sqlncli.h|Sqlncli.h|Sqlncli.h|Odbcss.h|  
|DLL-библиотека драйвера ODBC|Sqlncli.dll|Sqlncl10.dll|Sqlncl11.dll|sqlsrv32.dll|  
|Библиотека ODBC для API-интерфейсов программы BCP|Sqlncli.lib|Sqlncli10.lib|Sqlncli11.lib|Odbcbcp.lib|  
|DLL-библиотека ODBC для API-интерфейсов программы BCP|Sqlncli.dll|Sqlncli10.dll|Sqlncli11.dll|Odbcbcp.dll|  
|Идентификатор PROGID OLE DB|SQLNCLI|SQLNCLI10|SQLNCLI11|SQLOLEDB|  
|Имя файла заголовка OLE DB|Sqlncli.h|Sqlncli.h|Sqlncli.h|Sqloledb.h|  
|DLL-библиотека поставщика OLE DB|Sqlncli.dll|Sqlncli10.dll|Sqlncli11.dll|Sqloledb.dll|  
  
 Файл sqlncli.h поддерживает несколько версий [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client с помощью макроса SQLNCLI_VER. По умолчанию SQLNCLI_VER принимает значение, соответствующее последней версии собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Чтобы создать приложение, использующее sqlncli10.dll вместо sqlncli11.dll, установите SQLNCLI_VER в значение 10.  
  
## <a name="static-linking-and-bcp-functions"></a>Статическая компоновка и функции BCP  
 Если в приложении используются функции BCP, важно указывать в строке подключения драйвер из той же версии, которая поставлялась с файлом заголовка и библиотекой, использованными при компиляции приложения.  
  
 Например, если приложение компилируется с помощью собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а связанный файл библиотеки (sqlncli11.lib) и файл заголовка (sqlncli.h) взяты из каталога «\Program Files\Microsoft SQL Server\110\SDK», то убедитесь, что в строке подключения указывается (например, посредством ODBC) параметр «DRIVER={SQL Server Native Client 11.0}».  
  
 Дополнительные сведения см. в разделе Выполнение [выполнение операций массового копирования](../features/performing-bulk-copy-operations.md).  
  
## <a name="see-also"></a>См. также  
 [Построение приложений с использованием SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
