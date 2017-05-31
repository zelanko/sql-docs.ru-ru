---
title: "Просмотр моментального снимка базы данных (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database snapshots [SQL Server], viewing
- displaying database snapshots
- viewing database snapshots
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c11dd41a0c6077ff1d34b6a1f2b348fed87d92e5
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="view-a-database-snapshot-sql-server"></a>Просмотр моментального снимка базы данных (SQL Server)
  В этом разделе объясняется, как просмотреть моментальный снимок базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!NOTE]  
>  Создание, возврат к предыдущему состоянию и удаление моментального снимка базы данных необходимо производить с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Просмотр моментального снимка базы данных с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Просмотр моментального снимка базы данных**  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**.  
  
3.  Разверните узел **Моментальные снимки базы данных**и выберите моментальный снимок, который необходимо просмотреть.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Просмотр моментального снимка базы данных**  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Чтобы просмотреть список моментальных снимков базы данных для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните запрос столбца **source_database_id** представления каталога [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) по значениям, отличным от NULL.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание моментального снимка базы данных (Transact-SQL)](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [Восстановление базы данных до состояния, сохраненного в моментальном снимке](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
-   [Удаление моментального снимка базы данных (Transact-SQL)](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
