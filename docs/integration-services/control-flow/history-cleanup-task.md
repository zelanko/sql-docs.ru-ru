---
title: "Задача &#171;Очистка журнала&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.historycleanuptask.f1"
helpviewer_keywords: 
  - "таблицы журналов [SQL Server]"
  - "задача «Очистка журнала» [службы Integration Services]"
ms.assetid: 5defc5b9-dfd3-4859-a7fe-ac8c2b5480f8
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Задача &#171;Очистка журнала&#187;
  Задача «Очистка журнала» удаляет записи в следующих таблицах журнала в базе данных msdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   backupfile;  
  
-   backupfilegroup  
  
-   backupmediafamily;  
  
-   backupmediaset;  
  
-   backupset;  
  
-   restorefile;  
  
-   restorefilegroup;  
  
-   restorehistory.  
  
 Используя задачу «Очистка журнала», пакет может удалить данные журнала, связанные с деятельностью по созданию резервных копий и восстановлению, с заданиями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и планами обслуживания баз данных.  
  
 Эта задача инкапсулирует системную хранимую процедуру sp_delete_backuphistory и передает указанную дату процедуре как аргумент. Дополнительные сведения см. в разделе [sp_delete_backuphistory (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md).  
  
## Настройка задачи «Очистка журнала»  
 Эта задача включает свойство для указания самой ранней даты для данных, остающихся в таблицах журнала. Дата может задаваться числом дней, недель, месяцев или лет от текущего дня; в этом случае задача автоматически преобразует промежуток времени в дату.  
  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Очистка журнала" (план обслуживания)](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## См. также  
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)  
  
  