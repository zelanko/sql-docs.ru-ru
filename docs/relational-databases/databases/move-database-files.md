---
title: "Перемещение файлов базы данных | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "аварийное восстановление [SQL Server], перемещение файлов баз данных"
  - "файлы [SQL Server], перемещение"
  - "файлы данных [SQL Server], перемещение"
  - "перемещение файлов [SQL Server]"
  - "перенос полнотекстовых каталогов"
  - "перемещение баз данных"
  - "полнотекстовые каталоги [SQL Server], перемещение"
  - "перемещение файлов базы данных"
  - "запланированное обслуживание диска [SQL Server]"
  - "перемещение файлов"
  - "перемещение файлов базы данных"
  - "запланированные перемещения базы данных [SQL Server]"
  - "базы данных [SQL Server], перемещение"
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Перемещение файлов базы данных
  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно перемещать системные и пользовательские базы данных, задав в предложении FILENAME инструкции [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) новое местоположение файла. Таким образом могут быть перемещены файлы данных, журналов и полнотекстовых каталогов. Это может быть полезно в следующих ситуациях.  
  
-   Восстановление после сбоя. Например, база данных находится в подозрительном режиме, или ее работа была прекращена из-за сбоя оборудования.  
  
-   Плановое перемещение.  
  
-   Перемещение для запланированного обслуживания дисков.  
  
## В этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Перемещение пользовательских баз данных](../../relational-databases/databases/move-user-databases.md)|Описывает процедуры перемещения файлов пользовательской базы данных и файлов полнотекстовых каталогов в другое местоположение.|  
|[Перемещение системных баз данных](../../relational-databases/databases/move-system-databases.md)|Описывает процедуры перемещения файлов системной базы данных в другое местоположение.|  
  
## См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Присоединение и отсоединение базы данных (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  