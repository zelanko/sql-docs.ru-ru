---
description: Динамические административные представления Filestream and FileTable (Transact-SQL)
title: Динамические административные представления FILESTREAM и FileTable (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], dynamic management views
ms.assetid: e50a135d-6644-42a4-a0df-1c7a2b722051
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ca18eb28d70fb2b9d479a629545f46bae8ef3d9d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427856"
---
# <a name="filestream-and-filetable-dynamic-management-views-transact-sql"></a>Динамические административные представления Filestream and FileTable (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  В этом разделе описываются динамические административные представления, связанные с функциями FILESTREAM и FileTable.  
  
## <a name="filestream-dynamic-management-views-and-functions"></a>Динамические административные представления и функции Filestream  
 [sys.dm_filestream_file_io_handles (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql.md)  
 Показывает транзакционные дескрипторы файлов, открытые в данный момент.  
  
 [sys.dm_filestream_file_io_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql.md)  
 Выводит текущие запросы на ввод и вывод файлов.  
  
## <a name="filetable-dynamic-management-views-and-functions"></a>Динамические административные представления и функции FileTable  
 [sys.dm_filestream_non_transacted_handles (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)  
 Показывает открытые на данный момент нетранзакционные дескрипторы файлов, связанные с данными FileTable.  

## <a name="see-also"></a>См. также:
[Потока](../../relational-databases/blob/filestream-sql-server.md)
<br>[Таблицы FileTable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Представления каталога Filestream и FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
<br>[Системные хранимые процедуры Filestream и FileTable (Transact-SQL)](../system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)
  
