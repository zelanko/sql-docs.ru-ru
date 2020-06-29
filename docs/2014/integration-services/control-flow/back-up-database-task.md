---
title: Задача "Резервное копирование базы данных" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0980d89cc915121414dd7d3c89be6f4d72eb715
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434001"
---
# <a name="back-up-database-task"></a>Задача «Создание резервной копии базы данных»
  Задача «Резервное копирование базы данных» выполняет различные типы резервного копирования базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 С помощью задачи «Создание резервной копии базы данных» пакет может создать резервную копию отдельной базы данных или нескольких баз данных. При создании резервной копии только одной базы данных можно указать компонент для резервного копирования: база данных или ее файлы и файловые группы.  
  
## <a name="supported-recover-models-and-backup-types"></a>Поддерживаемые модели восстановления и типы резервного копирования  
 В следующей таблице перечисляются модели восстановления и типы резервных копий, поддерживаемые задачей «Создание резервной копии базы данных».  
  
|Модель восстановления|База данных|Разностное копирование базы данных|Журнал транзакций|Файл или разностное копирование файлов|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|Простая|Обязательно|Необязательно|Не поддерживается|Не поддерживается|  
|Полное|Обязательно|Необязательно|Обязательно|Необязательно|  
|С массовой регистрацией|Обязательно|Необязательно|Обязательно|Необязательно|  
  
 Задача «Создание резервной копии базы данных» содержит инструкцию BACKUP языка Transact-SQL. Дополнительные сведения см. в разделе [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql).  
  
## <a name="configuration-of-the-back-up-database-task"></a>Настройка задачи «Резервное копирование базы данных»  
 Свойства задаются с помощью конструктора служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Эта задача находится в разделе **Задачи плана обслуживания** **области элементов** в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Задача "Резервное копирование базы данных" (план обслуживания)](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
  
