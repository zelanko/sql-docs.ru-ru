---
title: Свойства задания — создание задания (страница "Общие") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ag.job.general.f1
ms.assetid: b6832840-1c18-4db8-94fc-080db880ae9f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4d8508bfbfe209db2e6a793ebc961f1ebb23bb40
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="job-properties---new-job-general-page"></a>Свойства задания — создание задания (страница "Общие")
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Эта страница используется для просмотра и изменения общих свойств задания агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="options"></a>Параметры  
**Название**  
Изменение имени задания.  
  
**Владелец**  
Выбор владельца задания.  
  
**Категория**  
Выбор категории задания.  
  
**...**  
Просмотр заданий в выбранной категории.  
  
**Описание**  
Изменение описания задания.  
  
**Enabled**  
Включение задания. Если задание не включено, оно не будет выполняться по расписанию или предупреждению, но может быть запущено с помощью хранимой процедуры **sp_start_job** .  
  
**Source**  
Отображается главный сервер для задания. Доступно только на странице **Свойства задания — общие** .  
  
**Создан**  
Отображаются дата и время создания задания. Доступно только на странице **Свойства задания — общие** .  
  
**Изменено**  
Отображаются дата и время последнего изменения задания. Доступно только на странице **Свойства задания — общие** .  
  
**Последнее выполнение**  
Отображаются дата и время последнего запуска задания. Доступно только на странице **Свойства задания — общие** .  
  
**Просмотр журнала заданий**  
Просмотр журнала заданий. Доступно только на странице **Свойства задания — общие** .  
  
## <a name="see-also"></a>См. также:  
[Реализация заданий](../../ssms/agent/implement-jobs.md)  
[Категории заданий — управление категориями заданий](../../ssms/agent/job-categories-manage-job-categories.md)  
  
