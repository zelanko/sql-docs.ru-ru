---
title: FileStream и FileTable системные хранимые процедуры (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], catalog views
ms.assetid: 2c83a4a7-720b-4435-a3b5-788c29f56949
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 854593c3ee467502e19ae7b07ae3ff9979e4397a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="filestream-and-filetable-system-stored-procedures-transact-sql"></a>FileStream и FileTable системные хранимые процедуры (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе описаны системные хранимые процедуры, функции FileTable и Filestream.  

## <a name="filestream-and-filetable-system-stored-procedures"></a>FileStream и Filetable системные хранимые процедуры
  [sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)

   Принудительно запускает сборщик мусора FILESTREAM, который удаляет все ненужные файлы FILESTREAM.

  [sp_kill_filestream_non_transacted_handles (Transact-SQL)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)

  Закрывает нетранзакционные дескрипторы файлов для данных FileTable.


## <a name="see-also"></a>См. также:
[FileStream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Таблицы Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Динамические административные представления Filestream и FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Представления каталога Filestream и FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
  
  
