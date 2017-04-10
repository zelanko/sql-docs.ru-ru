---
title: "Создание резервной копии на зеркальном наборе носителей (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# Создание резервной копии на зеркальном наборе носителей (Transact-SQL)
  В этой статье описан порядок использования инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](../../t-sql/statements/backup-transact-sql.md) для указания зеркального набора носителей при резервном копировании базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для определения зеркального набора носителей в инструкции BACKUP укажите первое зеркало в предложении TO. Затем определите каждое зеркало в своем собственном предложении TO. Предложения TO и MIRROR TO должны определять одинаковое количество и одинаковый тип устройств резервного копирования.  
  
## Пример  
 В следующем примере создается зеркальный набор носителей, показанный на предыдущем рисунке, и производится резервное копирование базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на оба зеркала.  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## Связанные задачи  
 **Восстановление из зеркально отображенной резервной копии**  
  
-   [RESTORE (Transact-SQL)](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
## См. также:  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Зеркальные наборы носителей резервных копий (SQL Server)](../../relational-databases/backup-restore/mirrored-backup-media-sets-sql-server.md)  
  
  