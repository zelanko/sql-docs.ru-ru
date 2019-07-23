---
title: Использование файлов библиотеки и заголовков драйвера OLE DB для SQL Server | Документация Майкрософт
description: Использование файлов библиотеки и заголовков драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- header files [OLE DB Driver for SQL Server]
- MSOLEDBSQL, header files
- OLE DB, header files
- library files [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, header files
- data access [OLE DB Driver for SQL Server], header files
- data access [OLE DB Driver for SQL Server], library files
- OLE DB Driver for SQL Server, library files
- MSOLEDBSQL, library files
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 93b906a0604772fe224b1e63eaf6eed9eb8af983
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989232"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>Использование файлов библиотеки и заголовков драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server заголовков и файлов библиотек устанавливается, когда в процессе установки выбран параметр Драйвер OLE DB для SQL Server SDK. При разработке приложения важно скопировать и установить все требуемые файлы для работы среды разработки. Дополнительные сведения об установке и распространении драйвера OLE DB для SQL Server см. в разделе [Установка драйвера OLE DB для SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md).  
  
 Драйвер OLE DB для SQL Server заголовков и файлов библиотек устанавливается в следующем расположении:  
  
 *%PROGRAM FILES%* \Microsoft SQL Server\Client SDK\OLEDB\182\SDK  
  
 Драйвер OLE DB для SQL Server файла заголовков (мсоледбскл. h) можно использовать для добавления драйвера OLE DB для SQL Server функций доступа к данным в пользовательские приложения. Файл заголовка драйвера OLE DB для SQL Server содержит все определения, атрибуты, свойства и интерфейсы, необходимые для использования новых функций, представленных в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Помимо драйвера OLE DB для SQL Server файла заголовков, существует также файл библиотеки мсоледбскл. lib, который является библиотекой экспорта для функциональности [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) .  
  
 Файл заголовка драйвера OLE DB для SQL Server имеет обратную совместимость с файлом заголовка sqloledb.h, используемым компонентами доступа к данным MDAC, но не содержит идентификаторов CLSID для SQLOLEDB (поставщик OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], включенный в компоненты MDAC) или символов для функциональных возможностей XML (которые не поддерживаются драйвером OLE DB для SQL Server).    
  
 OLE DB приложениям, использующим драйвер OLE DB для SQL Server, требуется только ссылка на мсоледбскл. h. Если приложение использует как компоненты MDAC (SQLOLEDB), так и драйвер OLE DB для SQL Server, оно может ссылаться как на sqloledb.h, так и на msoledbsql.h при условии, что ссылка на файл sqloledb.h будет идти первой.  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>Использование драйвера OLE DB для SQL Server заголовочного файла  
 Чтобы использовать драйвер OLE DB для SQL Server заголовочного файла, необходимо использовать инструкцию **include** в коде C/C++ программирования. В следующих разделах описано, как это сделать в OLE DB приложениях.  
  
> [!NOTE]  
>  Драйвер OLE DB для SQL Server заголовков и файлов библиотек можно скомпилировать только с помощью Visual C++ Studio 2012 или более поздней версии.  
  
### <a name="ole-db"></a>OLE DB  
 Чтобы использовать драйвер OLE DB для SQL Server заголовочного файла в приложении OLE DB, используйте следующие строки программного кода:  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  Если приложение содержит оператор **include** для SQLOLEDB. h, после него должен следовать оператор **include** для мсоледбскл. h.  
  
 При создании подключения к источнику данных с помощью драйвера OLE DB для SQL Server используйте "МСОЛЕДБСКЛ" в качестве строки имени поставщика.  

  
## <a name="component-names-and-properties-by-version"></a>Имена и свойства компонентов в зависимости от версии  

|Свойство|Драйвер OLE DB для SQL Server|MDAC|  
|--------|----------------------------|----|   
|Идентификатор PROGID OLE DB|МСОЛЕДБСКЛ|SQLOLEDB|  
|Имя файла заголовка OLE DB|мсоледбскл. h|Sqloledb.h|  
|DLL-библиотека поставщика OLE DB|мсоледбскл. dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>Статическая компоновка и функции BCP  
 Если в приложении используются функции BCP, важно указывать в строке подключения драйвер из той же версии, которая поставлялась с файлом заголовка и библиотекой, использованными при компиляции приложения.  
  
 Дополнительные сведения см. в разделе Выполнение [операций](../../oledb/features/performing-bulk-copy-operations.md)с массовым копированием.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
