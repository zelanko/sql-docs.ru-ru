---
description: Задача «Очистка журнала»
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
ms.openlocfilehash: 2455138c200097adc1547d3d57fbe4014b2be022
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "92194263"
---
# <a name="history-cleanup-task"></a>Задача «Очистка журнала»

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


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
  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания****области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Очистка журнала" (план обслуживания)](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](./add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
## <a name="see-also"></a>См. также:  
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)  
  
