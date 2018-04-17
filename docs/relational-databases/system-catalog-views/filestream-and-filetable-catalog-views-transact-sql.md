---
title: FileStream и представления каталога FileTable (Transact-SQL) | Документы Microsoft
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
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9fcd323c157d43d0dad1546004f79f8e5affd60c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="filestream-and-filetable-catalog-views-transact-sql"></a>Представления каталога Filestream и FileTable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются представления каталога, связанные с таблицами FileTable.  
  
## <a name="filestream-and-filetable-catalog-views-transact-sql"></a>FileStream и filetable представления каталога (Transact-SQL)
 [sys.database_filestream_options (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)  
 Отображает сведения об уровне нетранзакционного доступа к данным FILESTREAM в каждой из включенных таблиц FileTable. Содержит по одной строке для каждой базы данных в экземпляре SQL Server.  
  
 [sys.filetable_system_defined_objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql.md)  
 Отображает список системных объектов, связанных с таблицами FileTable. Содержит по одной строке для каждого системного объекта.  
  
 [sys.filetables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-filetables-transact-sql.md)  
 Возвращает по одной строке для каждой таблицы FileTable. Наследует от **sys.tables**.  

## <a name="see-also"></a>См. также
[FileStream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Таблицы Filetable](../../relational-databases/blob/filetables-sql-server.md)
<br>[FileStream и FileTable динамические административные представления (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[FileStream и FileTable системные хранимые процедуры (Transact-SQL)](../system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)
  
  
