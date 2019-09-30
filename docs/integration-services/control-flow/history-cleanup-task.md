---
title: Задача "Очистка журнала" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.historycleanuptask.f1
helpviewer_keywords:
- history tables [SQL Server]
- History Cleanup task [Integration Services]
ms.assetid: 5defc5b9-dfd3-4859-a7fe-ac8c2b5480f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1844f4088c026dda5636cd31a7f90b5effe4bfbc
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71298248"
---
# <a name="history-cleanup-task"></a>Задача «Очистка журнала»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Задача «Очистка журнала» удаляет записи в следующих таблицах журнала в базе данных msdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
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
  
## <a name="configuration-of-the-history-cleanup-task"></a>Настройка задачи «Очистка журнала»  
 Эта задача включает свойство для указания самой ранней даты для данных, остающихся в таблицах журнала. Дата может задаваться числом дней, недель, месяцев или лет от текущего дня; в этом случае задача автоматически преобразует промежуток времени в дату.  
  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Очистка журнала" (план обслуживания)](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a>См. также:  
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)  
  
  
