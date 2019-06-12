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
manager: jroth
ms.openlocfilehash: b188649e138dddfc7dd4fd9fe974d6ccf28cc904
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66777956"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>Использование файлов библиотеки и заголовков драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server заголовка и файлы библиотек устанавливаются при выборе драйвер OLE DB для SQL Server SDK параметр во время процесса установки. При разработке приложения важно скопировать и установить все требуемые файлы для работы среды разработки. Дополнительные сведения об установке и распространении драйвера OLE DB для SQL Server см. в разделе [установка драйвер OLE DB для SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md).  
  
 Драйвер OLE DB для SQL Server заголовка и файлы библиотек устанавливаются в следующий каталог:  
  
 *%PROGRAM FILES%* \Microsoft SQL Server\Client SDK\OLEDB\182\SDK  
  
 Драйвер OLE DB для SQL Server заголовочного файла (msoledbsql.h) может использоваться для добавления драйвера OLE DB для функции доступа к данным SQL Server в пользовательские приложения. Файл заголовка драйвера OLE DB для SQL Server содержит все определения, атрибуты, свойства и интерфейсы, необходимые для использования новых функций, представленных в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 В дополнение к драйвер OLE DB для SQL Server файла заголовка, имеется также файл библиотеки msoledbsql.lib, являющийся библиотекой экспорта для [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) функциональные возможности.  
  
 Файл заголовка драйвера OLE DB для SQL Server имеет обратную совместимость с файлом заголовка sqloledb.h, используемым компонентами доступа к данным MDAC, но не содержит идентификаторов CLSID для SQLOLEDB (поставщик OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], включенный в компоненты MDAC) или символов для функциональных возможностей XML (которые не поддерживаются драйвером OLE DB для SQL Server).    
  
 Приложения OLE DB, использующие драйвер OLE DB для SQL Server достаточно указать msoledbsql.h. Если приложение использует как компоненты MDAC (SQLOLEDB), так и драйвер OLE DB для SQL Server, оно может ссылаться как на sqloledb.h, так и на msoledbsql.h при условии, что ссылка на файл sqloledb.h будет идти первой.  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>С помощью драйвера OLE DB для SQL Server файл заголовка  
 Чтобы использовать драйвер OLE DB для SQL Server заголовочного файла, необходимо использовать **включают** инструкции в программном коде на C/C++. Следующие разделы описывают, как это сделать в приложениях OLE DB.  
  
> [!NOTE]  
>  Драйвер OLE DB для SQL Server заголовочные и библиотечные файлы можно только в том случае, скомпилированный с помощью C++ в Visual Studio 2012 или более поздней версии.  
  
### <a name="ole-db"></a>OLE DB  
 Использование драйвера OLE DB для SQL Server файла заголовка в приложении OLE DB, используя приведенный ниже программный код:  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  Если приложение имеет **включают** инструкции для файла sqloledb.h, **включают** инструкции для msoledbsql.h должна идти после нее.  
  
 При создании подключения к источнику данных с помощью драйвера OLE DB для SQL Server, используйте «MSOLEDBSQL» как строку имени поставщика.  

  
## <a name="component-names-and-properties-by-version"></a>Имена и свойства компонентов в зависимости от версии  

|Свойство|Драйвер OLE DB для SQL Server|MDAC|  
|--------|----------------------------|----|   
|Идентификатор PROGID OLE DB|MSOLEDBSQL|SQLOLEDB|  
|Имя файла заголовка OLE DB|msoledbsql.h|Sqloledb.h|  
|DLL-библиотека поставщика OLE DB|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>Статическая компоновка и функции BCP  
 Если в приложении используются функции BCP, важно указывать в строке подключения драйвер из той же версии, которая поставлялась с файлом заголовка и библиотекой, использованными при компиляции приложения.  
  
 Дополнительные сведения см. в разделе Выполнение [выполнение операций массового копирования](../../oledb/features/performing-bulk-copy-operations.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
