---
title: "Свойства базы данных (страница \"Файловые группы\") | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.databaseproperties.filegroups.f1
ms.assetid: 8d06e859-73dd-4019-b6e8-99c5c5297697
caps.latest.revision: "31"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b5059c901a9b2dc517b765a642ddbe16bb926471
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="database-properties-filegroups-page"></a>Свойства базы данных (страница «Файловые группы»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Эта страница используется для просмотра файловых групп или добавления новой файловой группы в выбранную базу данных. Типы файловых групп разделены на файловые группы *строк* , файловые группы данных FILESTREAM и файловые группы, оптимизированные для памяти.  
  
 Файловые группы строк содержат обычные данные и файлы журналов. Файловые группы данных FILESTREAM содержат файлы данных FILESTREAM. В этих файлах данных содержатся сведения о способах хранения данных больших двоичных объектов (BLOB) в файловой системе при использовании хранилища Filestream. Параметры одинаковы для файловых групп обоих типов.  
  
 Если хранилище FILESTREAM отключено, то раздел **Filestream** недоступен. Хранилище FILESTREAM можно включить в диалоговом окне [Свойства сервера (страница "Дополнительно")](../../database-engine/configure-windows/server-properties-advanced-page.md).  
  
 Дополнительные сведения об использовании файловых групп строк в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Файлы и файловые группы базы данных](../../relational-databases/databases/database-files-and-filegroups.md). Дополнительные сведения о данных и файловых группах FILESTREAM см. в разделе [FILESTREAM (SQL Server)](../../relational-databases/blob/filestream-sql-server.md).  
  
 Оптимизированные для памяти файловые группы необходимы, когда база данных должна содержать одну или несколько оптимизированных для памяти таблиц.  
  
## <a name="row-and-filestream-data-filegroup-options"></a>Параметры файловых групп для строк и данных FILESTREAM.  
 **Название**  
 Введите имя файловой группы.  
  
 **Files**  
 Отображает число файлов в файловой группе.  
  
 **Только для чтения**  
 Выберите, чтобы установить для файловой группы статус «только для чтения».  
  
 **Default**  
 Выберите, чтобы сделать эту файловую группу используемой по умолчанию. Можно организовать одну файловую группу по умолчанию для строк и одну файловую группу по умолчанию для данных FILESTREAM.  
  
 **Добавить**  
 Позволяет добавить новую пустую строку в сетку списка файловых групп базы данных.  
  
 **Удалить**  
 Позволяет удалить выбранную строку файловой группы из сетки.  
  
## <a name="memory-optimized-data-filegroup-options"></a>Параметры файловых групп для данных, оптимизированных для памяти.  
 **Название**  
 Введите имя файловой группы, оптимизированной для памяти.  
  
 **Файлы файловой группы**  
 Отображает число файлов (контейнеров) в оптимизированной для памяти файловой группе данных. На странице **Файлы** можно добавлять контейнеры.  
  
 **Добавить**  
 Позволяет добавить новую пустую строку в сетку списка файловых групп базы данных.  
  
 **Удалить**  
 Позволяет удалить выбранную строку файловой группы из сетки.  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  
