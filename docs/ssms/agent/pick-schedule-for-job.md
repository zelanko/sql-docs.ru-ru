---
description: Выбор расписания для задания
title: Выбор расписания для задания
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.pickscheduleforjob.f1
helpviewer_keywords:
- Pick Schedule for Job dialog box
ms.assetid: 6de2025d-c25c-47b9-9a25-18c294935c15
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c095370f69aaa1e9f06cfc3e57500c09442c728a
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92030945"
---
# <a name="pick-schedule-for-job"></a>Выбор расписания для задания
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Используйте это диалоговое окно, чтобы выбрать расписание из списка имеющихся расписаний для задания агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
**Доступные расписания**  
Содержит список расписаний, доступных для данного задания. Поскольку задание и расписание должны иметь одного и того же владельца, этот список включает в себя только те расписания, которые принадлежат владельцу задания.  
  
**Имя**  
Отображает имя расписания.  
  
**Enabled**  
Этот параметр выбран, если расписание включено.  
  
**Описание**  
Описывает условия, при которых расписание запускает задание.  
  
**Задания в расписании**  
Приводит список номеров заданий, внесенных в расписание. Щелкните номер, чтобы увидеть свойства задания.  
  
**Свойства**  
Открывает диалоговое окно **Свойства расписания задания** , в котором можно просмотреть сведения о расписании.  
  
## <a name="see-also"></a>См. также:  
[Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
