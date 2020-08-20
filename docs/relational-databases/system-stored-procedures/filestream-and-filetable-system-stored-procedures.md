---
description: Системные хранимые процедуры Filestream и FileTable (Transact-SQL)
title: Системные хранимые процедуры FILESTREAM и FileTable (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], catalog views
ms.assetid: 2c83a4a7-720b-4435-a3b5-788c29f56949
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4b16bd28de1b6166cfcea3634c02d48ab8bdc400
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489796"
---
# <a name="filestream-and-filetable-system-stored-procedures-transact-sql"></a>Системные хранимые процедуры FILESTREAM и FileTable (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  В этом разделе описываются системные хранимые процедуры функций FileTable и FILESTREAM.  

## <a name="filestream-and-filetable-system-stored-procedures"></a>Системные хранимые процедуры FILESTREAM и FileTable
  [sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)

   Принудительно запускает сборщик мусора FILESTREAM, который удаляет все ненужные файлы FILESTREAM.

  [sp_kill_filestream_non_transacted_handles (Transact-SQL)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)

  Закрывает нетранзакционные дескрипторы файлов для данных FileTable.


## <a name="see-also"></a>См. также раздел
[Потока](../../relational-databases/blob/filestream-sql-server.md)
<br>[Таблицы FileTable](../../relational-databases/blob/filetables-sql-server.md)
<br>[Динамические административные представления Filestream и FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Представления каталога Filestream и FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
  
  
