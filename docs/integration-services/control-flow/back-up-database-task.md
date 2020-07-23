---
title: Задача "Резервное копирование базы данных" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d10f1ceab3ddb56ae8edbd06b2226fad2646c586
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86918887"
---
# <a name="back-up-database-task"></a>Задача «Создание резервной копии базы данных»

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Задача «Резервное копирование базы данных» выполняет различные типы резервного копирования базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 С помощью задачи «Создание резервной копии базы данных» пакет может создать резервную копию отдельной базы данных или нескольких баз данных. При создании резервной копии только одной базы данных можно указать компонент для резервного копирования: база данных или ее файлы и файловые группы.  
  
## <a name="supported-recover-models-and-backup-types"></a>Поддерживаемые модели восстановления и типы резервного копирования  
 В следующей таблице перечисляются модели восстановления и типы резервных копий, поддерживаемые задачей «Создание резервной копии базы данных».  
  
|Модель восстановления|База данных|Разностное копирование базы данных|Журнал транзакций|Файл или разностное копирование файлов|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|Простая|Обязательно|Необязательно|Не поддерживается|Не поддерживается|  
|Полное|Обязательно|Необязательно|Обязательно|Необязательно|  
|С массовой регистрацией|Обязательно|Необязательно|Обязательно|Необязательно|  
  
 Задача «Создание резервной копии базы данных» содержит инструкцию BACKUP языка Transact-SQL. Дополнительные сведения см. в разделе [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md).  
  
## <a name="configuration-of-the-back-up-database-task"></a>Настройка задачи «Резервное копирование базы данных»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Резервное копирование базы данных" (план обслуживания)](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  
