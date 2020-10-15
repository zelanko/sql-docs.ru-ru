---
description: Управление расписаниями
title: Управление расписаниями
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: af21aa75f777d2745901736dce695cf226f3cbcf
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037857"
---
# <a name="manage-schedules"></a>Управление расписаниями
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Позволяет просматривать и менять свойства для расписаний заданий агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
**Доступные расписания**  
Приводит список расписаний, доступных пользователю. Обратите внимание, что у задания и у расписания должен быть один владелец. Следовательно, в этом списке приводятся только расписания, которые принадлежат владельцу задания.  
  
**Имя**  
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
