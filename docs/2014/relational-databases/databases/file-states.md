---
title: Состояния файла | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- restoring file state [SQL Server]
- verifying file states
- current file states
- verifying filegroup states
- file states [SQL Server]
- online file state
- offline file state [SQL Server]
- viewing filegroup states
- viewing file states
- suspect file state
- recovering file state [SQL Server]
- current filegroup state
- recovery pending file state [SQL Server]
- displaying file states
- states [SQL Server], files
- displaying filegroup states
- defunct file state
ms.assetid: b426474d-8954-4df0-b78b-887becfbe8d6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3acbe6dffaec03e876f4d9cfc1092c7d6367c364
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48071804"
---
# <a name="file-states"></a>Состояния файла
  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]состояние файла базы данных поддерживается независимо от состояния базы данных. Файл всегда находится в одном определенном состоянии, таком как ONLINE или OFFLINE. Чтобы просмотреть текущее состояние файла, используйте представление каталога [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) или [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) . Если база данных находится в состоянии вне сети, то состояние файлов можно просмотреть в представлении каталога [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) .  
  
 Состояние файлов в файловой группе определяет доступность всей файловой группы. Чтобы файловая группа была доступна, необходимо, чтобы все файлы в файловой группе находились в режиме в сети. Чтобы просмотреть текущее состояние файловой группы, используйте представление каталога [sys.filegroups](/sql/relational-databases/system-catalog-views/sys-filegroups-transact-sql) . Попытка получить доступ к файловой группе, которая находится в режиме вне  сети, с помощью инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] приводит к ошибке. При построении планов запросов для инструкций SELECT оптимизатор запросов избегает некластеризованных индексов и индексированных представлений, принадлежащих файловым группам вне сети, чтобы разрешить успешное выполнение инструкций. Однако если файловая группа, находящаяся в режиме вне  сети, содержит кучу или кластеризованный индекс целевой таблицы, инструкция SELECT не будет выполнена. Кроме того, любая инструкция INSERT, UPDATE или DELETE, изменяющая таблицу с любым индексом в файловой группе, находящихся в режиме вне  сети, также не будет выполнена.  
  
## <a name="file-state-definitions"></a>Определения состояний файлов  
 Состояния файлов определяются в следующей таблице.  
  
|Состояние|Определение|  
|-----------|----------------|  
|ONLINE|Файл доступен для всех операций. Если база данных находится в режиме в сети, то файлы первичной файловой группы всегда находятся в режиме в сети. Если файл первичной файловой группы не находится в режиме в сети, то база данных тоже не находится в режиме в сети, и состояния файлов во вторичной файловой группе не определены.|  
|OFFLINE|Файл недоступен и, возможно, отсутствует на диске. Файлы переходят в режим вне сети с помощью явного указания пользователя и остаются в режиме вне  сети до тех пор, пока пользователем не будет предпринято дополнительное действие.<br /><br /> **\*\* Внимание! \*\*** Файл следует устанавливать в режим "вне сети" только в том случае, если он поврежден, но может быть восстановлен. Файл, который установлен в режим вне сети, может быть установлен в режим в сети только путем восстановления файла из резервной копии. Дополнительные сведения о восстановлении одного файла см. в разделе [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql).|  
|RESTORING|Файл восстанавливается. Файлы переходят в состояние восстановления в результате команды восстановления, воздействующей на весь файл, а не на отдельную страницу; файлы остаются в состоянии восстановления до окончания процесса восстановления файла.|  
|RECOVERY PENDING|Восстановление файла было отложено. Файл переходит в это состояние автоматически в результате частичного восстановления, при котором файл еще не восстановлен. Со стороны пользователя требуется дополнительное действие, чтобы исправить ошибку и разрешить завершение процесса восстановления. Дополнительные сведения см. в разделе [Поэтапное восстановление (SQL Server)](../backup-restore/piecemeal-restores-sql-server.md).|  
|SUSPECT|Не удалось восстановить файл в процессе восстановления файла в сети. Если файл находится в первичной файловой группе, база данных тоже помечается как подозрительная. Иначе база данных остается в режиме в сети, и в подозрительном состоянии находится только файл.<br /><br /> Файл остается в подозрительном состоянии до тех пор, пока он не становится доступным в результате одного из следующих методов.<br /><br /> Восстановление из резервной копии или по журналу транзакций<br /><br /> Инструкцией DBCC CHECKDB c параметром REPAIR_ALLOW_DATA_LOSS|  
|DEFUNCT|Файл был удален, пока находился не в сети. При удалении файловой группы вне сети все файлы группы помечаются удаленными.|  
  
## <a name="related-content"></a>См. также  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [Состояния базы данных](database-states.md)  
  
 [Состояния зеркального отображения (SQL Server)](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
 [Файлы и файловые группы базы данных](database-files-and-filegroups.md)  
  
  
