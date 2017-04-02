---
title: "Переключение сеанса зеркального отображения базы данных на другой ресурс вручную (язык Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "переход на другой ресурс [SQL Server], зеркальное отображение базы данных"
  - "ручная отработка отказа [SQL Server]"
  - "зеркальное отображение базы данных [SQL Server], переход на другой ресурс"
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
caps.latest.revision: 32
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 32
---
# Переключение сеанса зеркального отображения базы данных на другой ресурс вручную (язык Transact-SQL)
  Когда зеркальная база данных синхронизирована (то есть база данных находится в состоянии SYNCHRONIZED), владелец базы данных может инициировать отработку отказа на зеркальном сервере вручную. Переход на другой ресурс вручную может быть инициирован только с основного сервера.  
  
### Отработка отказа в сеансе зеркального отображения базы данных вручную  
  
1.  Подключитесь к основному серверу.  
  
2.  Задайте базу данных **master** в качестве контекста базы данных:  
  
     **USE master;**  
  
3.  Введите следующую инструкцию на основном сервере:  
  
     [ALTER DATABASE](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md) *имя_базы_данных* SET PARTNER FAILOVER, где *имя_базы_данных* — это зеркально отображаемая база данных.  
  
     В результате роль основного сервера немедленно перейдет к зеркальному серверу.  
  
 На бывшем основном сервере произойдет отключение клиентов базы данных с откатом незавершенных транзакций.  
  
> [!NOTE]  
>  Транзакции, подготовленные с помощью координатора распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)], но еще не зафиксированные на момент отработки отказа, после отработки отказа базы данных будут считаться отмененными.  
  
## См. также:  
 [Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [Переключение сеанса зеркального отображения базы данных на другой ресурс вручную (среда SQL Server Management Studio)](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [Переключение ролей во время сеанса зеркального отображения базы данных (SQL Server)](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  