---
description: Свойства задания — новое задание (страница "Расписания")
title: Свойства задания — новое задание (страница "Расписания")
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.schedules.f1
ms.assetid: 0b03585b-a510-484d-8a63-9b32459def9c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c4476f26f2b17cedcc12e723efc08c116b190488
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037892"
---
# <a name="job-properties---new-job-schedules-page"></a>Свойства задания — новое задание (страница "Расписания")
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Эта страница позволяет просматривать и организовывать расписания для задания агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
**Список расписаний**  
Список расписаний для данного задания.  
  
**Создать**  
Создает новое расписание. После создания нового расписания оно добавляется к заданию.  
  
**Выбрать**  
Выбор расписания из существующих расписаний. Поскольку у задания и расписания должен быть один и тот же владелец, здесь можно выбирать только из расписаний, которыми владеете.  
  
**Edit** (Изменение)  
Изменяет выбранное расписание задания.  
  
**Удалить**  
Удалить выбранное расписание из задания. Если больше ни одно задание не использует это расписание, оно удаляется из базы данных.  
  
## <a name="see-also"></a>См. также:  
[Реализация заданий](../../ssms/agent/implement-jobs.md)  
