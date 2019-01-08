---
title: Удаление моментального снимка базы данных (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- removing database snapshots
- deleting database snapshots
- database snapshots [SQL Server], deleting
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d1387b6321ace59ec8a0c13ed03444553f4adf85
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52774306"
---
# <a name="drop-a-database-snapshot-transact-sql"></a>удалить моментальный снимок базы данных (Transact-SQL)
  При удалении моментального снимка базы данных он удаляется из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и удаляются разреженные файлы, используемые моментальным снимком. При удалении моментального снимка базы данных все соединения пользователя с ним должны быть завершены.  
  
## <a name="security"></a>безопасность  
  
###  <a name="Permissions"></a> Permissions  
 Любой пользователь с разрешениями DROP DATABASE может удалить моментальный снимок базы данных.  
  
##  <a name="TsqlProcedure"></a> Как удалить моментальный снимок базы данных (с помощью Transact-SQL)  
 **Удаление моментального снимка базы данных**  
  
1.  Идентифицируйте моментальный снимок базы данных, который нужно удалить. Просмотреть моментальные снимки в базе данных можно в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Просмотр моментального снимка базы данных (SQL Server)](view-a-database-snapshot-sql-server.md).  
  
2.  Выполните инструкцию [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) , указав имя моментального снимка базы данных, который нужно удалить. Синтаксис:  
  
     DROP DATABASE *имя_моментального_снимка_базы_данных* [ **,**...*n* ]  
  
     Где *имя_моментального_снимка_базы_данных* — имя удаляемого моментального снимка базы данных.  
  
####  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 Следующий код удаляет моментальный снимок базы данных, имеющий имя SalesSnapshot0600, без влияния на базу данных-источник.  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 Все пользовательские соединения к SalesSnapshot0600 будут завершены, а все разреженные файлы файловой системы NTFS, используемые моментальным снимком, будут удалены.  
  
> [!NOTE]  
>  Сведения об использовании разреженных файлов для моментальных снимков баз данных см. в разделе [Моментальные снимки базы данных (SQL Server)](database-snapshots-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание моментального снимка базы данных (Transact-SQL)](create-a-database-snapshot-transact-sql.md)  
  
-   [Просмотр моментального снимка базы данных (SQL Server)](view-a-database-snapshot-sql-server.md)  
  
-   [Восстановление базы данных до состояния, сохраненного в моментальном снимке](revert-a-database-to-a-database-snapshot.md)  
  

  
## <a name="see-also"></a>См. также  
 [DROP DATABASE (Transact-SQL)](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)   
 [Моментальные снимки базы данных (SQL Server)](database-snapshots-sql-server.md)  
  
  
