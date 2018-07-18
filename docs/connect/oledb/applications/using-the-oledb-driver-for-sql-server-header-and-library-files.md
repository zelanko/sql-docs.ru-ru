---
title: С помощью драйвер OLE DB для SQL Server заголовка и файлам библиотеки | Документы Microsoft
description: С помощью драйвера OLE DB для SQL Server файлы заголовка и библиотеки
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: f228442c31d754265769645a640b1eb1285c5897
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2018
ms.locfileid: "35612149"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>С помощью драйвер OLE DB для SQL Server заголовка и файлам библиотеки
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Драйвер OLE DB для SQL Server заголовка и файлы библиотек устанавливаются при выборе драйвер OLE DB для SQL Server SDK параметра во время процесса установки. При разработке приложения важно скопировать и установить все требуемые файлы для работы среды разработки. Дополнительные сведения об установке и распространении драйвер OLE DB для SQL Server см. в разделе [установка драйвер OLE DB для SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md).  
  
 Драйвер OLE DB для SQL Server заголовка и файлы библиотек устанавливаются в следующий каталог:  
  
 *% PROGRAM FILES %* \Microsoft SQL Server\Client SDK\OLEDB\180\SDK  
  
 Драйвер OLE DB для SQL Server заголовочного файла (msoledbsql.h) можно использовать для добавления драйвер OLE DB для SQL Server функции доступа к данным в пользовательские приложения. Драйвер OLE DB для SQL Server заголовочного файла содержит все определения, атрибуты, свойства и интерфейсы, необходимые для использования преимуществ новых функций представлены в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Помимо драйвер OLE DB для SQL Server файла заголовка, имеется также файл библиотеки msoledbsql.lib, являющийся библиотекой экспорта для [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) функциональные возможности.  
  
 Драйвер OLE DB для SQL Server заголовочного файла обладает обратной совместимостью с sqloledb.h файл заголовка, используемый с Microsoft данных Access Components (MDAC), но не содержит идентификаторов CLSID для SQLOLEDB (поставщик OLE DB для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включенный с компонентами MDAC) или символы для Возможности работы с XML (который не поддерживается драйвером OLE DB для SQL Server).    
  
 Приложения OLE DB, которые используют драйвер OLE DB для SQL Server должны ссылаться на msoledbsql.h. Если приложение использует компоненты MDAC (SQLOLEDB) и драйвер OLE DB для SQL Server, он может ссылаться на sqloledb.h и msoledbsql.h, но ссылка на файл SQLOLEDB.h будет идти первой.  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>С помощью драйвер OLE DB для SQL Server заголовочного файла  
 Чтобы использовать драйвер OLE DB для SQL Server заголовочного файла, необходимо использовать **включают** инструкции в программный код на C/C++. В следующих разделах описаны как сделать это приложения OLE DB.  
  
> [!NOTE]  
>  Драйвер OLE DB для SQL Server файлы заголовка и библиотеки можно только в том случае, скомпилированные для работы с C++ в Visual Studio 2012 или более поздней версии.  
  
### <a name="ole-db"></a>OLE DB  
 Чтобы использовать драйвер OLE DB для SQL Server заголовочного файла в приложении OLE DB, используя программный код следующие строки:  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  Если приложение имеет **включают** инструкции для файла sqloledb.h, **включают** инструкции для msoledbsql.h должна идти после нее.  
  
 При создании соединения с источником данных с помощью драйвера OLE DB для SQL Server, используйте в качестве строки имени поставщика «MSOLEDBSQL».  

  
## <a name="component-names-and-properties-by-version"></a>Имена и свойства компонентов в зависимости от версии  

|Свойство|Драйвер OLE DB для SQL Server|MDAC|  
|--------|----------------------------|----|   
|Идентификатор PROGID OLE DB|MSOLEDBSQL|SQLOLEDB|  
|Имя файла заголовка OLE DB|msoledbsql.h|Sqloledb.h|  
|DLL-библиотека поставщика OLE DB|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>Статическая компоновка и функции BCP  
 Если в приложении используются функции BCP, важно указывать в строке подключения драйвер из той же версии, которая поставлялась с файлом заголовка и библиотекой, использованными при компиляции приложения.  
  
 Дополнительные сведения см. в разделе Выполнение [выполнение операций массового копирования](../../oledb/features/performing-bulk-copy-operations.md).  
  
## <a name="see-also"></a>См. также  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
