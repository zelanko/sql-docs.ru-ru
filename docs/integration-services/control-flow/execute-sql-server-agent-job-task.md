---
description: Задача «Выполнение задания агента SQL Server»
title: Задача «Выполнение задания агента SQL Server»
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.executesqlserveragentjobtask.f1
helpviewer_keywords:
- Execute SQL Server Agent Job task [Integration Services]
- jobs [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
author: chugugrace
ms.author: chugu
ms.custom: seo-lt-2019
ms.openlocfilehash: c6456e91ae6747e561d467774da86ad9697bd510
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96123510"
---
# <a name="execute-sql-server-agent-job-task"></a>Задача «Выполнение задания агента SQL Server»

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Задача «Выполнение задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] » запускает задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является службой [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, которая запускает задания, определенные для экземпляра SQL Server. Можно создавать задания, которые выполняют инструкции Transact-SQL и скрипты ActiveX, задачи служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и задачи обслуживания репликаций либо производят запуск пакетов. Можно также настроить задание, чтобы контролировать [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и вызывать предупреждения. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно используются, чтобы автоматически выполнять повторяющиеся задачи. Дополнительные сведения см. в разделе [Реализация заданий](../../ssms/agent/implement-jobs.md).  
  
 Используя задачу «Выполнение задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] », пакет может выполнять административные задачи, связанные с компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Например, задача агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может запускать системную хранимую процедуру — к примеру, **sp_dts_listpackages** — для получения списка пакетов в папке.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент должен быть запущен для автоматического запуска локальных или многосерверных административных заданий.  
  
 Эта задача содержит системную процедуру **sp_start_job** и передает имя задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде аргумента. Дополнительные сведения см. в разделе [sp_start_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md).  
  
## <a name="configuring-the-execute-sql-server-agent-job-task"></a>Настройка задачи «Выполнение задания агента SQL Server»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания****области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Выполнение задания агента SQL Server" (план обслуживания)](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](./add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
