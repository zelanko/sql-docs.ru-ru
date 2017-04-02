---
title: "Задача &#171;Проверка целостности базы данных&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.checkdatabaseintegritytask.f1"
helpviewer_keywords: 
  - "целостность данных [службы Integration Services]"
  - "задача «Проверка целостности базы данных» [службы Integration Services]"
  - "проверка согласованности базы данных"
  - "проверка согласованности базы данных [службы Integration Services]"
  - "проверка согласованности базы данных"
  - "проверка целостности [службы Integration Services]"
ms.assetid: 5a82fe99-4503-429f-9337-e6bac7649fe4
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# Задача &#171;Проверка целостности базы данных&#187;
  Задача «Проверка целостности базы данных» заключается в проверке распределения и структурной целостности всех объектов в заданной базе данных. Можно проверить одну или несколько баз данных. Кроме того, можно задать проверку индексов базы данных.  
  
 Задача проверки целостности базы данных содержит инструкцию DBCC CHECKDB. Дополнительные сведения см. в разделе [DBCC CHECKDB (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).  
  
## Настройка задачи «Проверка целостности базы данных»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Проверка целостности базы данных" (план обслуживания)](../../relational-databases/maintenance-plans/check-database-integrity-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
  