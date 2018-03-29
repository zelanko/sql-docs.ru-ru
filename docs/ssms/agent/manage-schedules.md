---
title: Управление расписаниями | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- sql13.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 631e4d3d3b3a97ca2b80c5e21f04b12d4238a8b5
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="manage-schedules"></a>Управление расписаниями
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Позволяет просматривать и изменять свойства расписаний заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
## <a name="options"></a>Параметры  
**Доступные расписания**  
Приводит список расписаний, доступных пользователю. Обратите внимание, что у задания и у расписания должен быть один владелец. Следовательно, в этом списке приводятся только расписания, которые принадлежат владельцу задания.  
  
**Название**  
Отображает имя расписания.  
  
**Enabled**  
Выберите этот параметр, чтобы включить расписание.  
  
**Описание**  
Описывает условия, при которых расписание запускает задание.  
  
**Задания в расписании**  
Приводит список номеров заданий, внесенных в расписание. Щелкните номер, чтобы увидеть свойства задания.  
  
**Создать**  
Нажмите эту кнопку, чтобы создать новое расписание.  
  
**Удаление**  
Нажмите эту кнопку, чтобы удалить выбранное расписание.  
  
**Свойства**  
Нажмите эту кнопку, чтобы изменить свойства выбранного расписания.  
  
## <a name="see-also"></a>См. также:  
[Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
  
