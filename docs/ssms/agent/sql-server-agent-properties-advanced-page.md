---
description: Свойства агента SQL Server (страница «Дополнительно»)
title: Свойства агента SQL Server (страница «Дополнительно»)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 96dcf5690bac961e08c222023e14d92b833cfff2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88318182"
---
# <a name="sql-server-agent-properties-advanced-page"></a>Свойства агента SQL Server (страница «Дополнительно»)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Эта страница используется для просмотра и изменения дополнительных свойств службы агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
**Пересылка событий SQL Server**  
Параметры в данной категории активируют и настраивают пересылку событий.  
  
**Переслать события на другой сервер**  
Перенаправляет события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] другому серверу.  
  
**Server**  
Выберите имя сервера, которому нужно перенаправить события.  
  
**Необработанные события**  
Переправляет заданному серверу только необработанные события. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перенаправляет только события, на которые не реагирует ни одно предупреждение.  
  
**Все события**  
Переправляет все события. Если предупреждение локального экземпляра реагирует на событие, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перенаправит этот событие и обработает предупреждение.  
  
**Если серьезность события равна или превышает**  
Пересылает только события, уровень серьезности которых равен указанному или превышает его.  
  
**Условие простоя ЦП**  
Параметры в данной категории определяют условия, при которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускает задания, запланированные к выполнению в расписании простоя ЦП.  
  
**Определить условие простоя ЦП**  
Определяет условия, при которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] считает, что ЦП простаивает.  
  
**Среднее время использования ЦП сократилось до**  
Процент использования ЦП сократился до уровня, при котором считается, что ЦП простаивает.  
  
**И остается ниже этого уровня в течение**  
Отрезок времени, который средний ЦП должен простаивать, прежде чем агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запустит задания по расписанию простоя ЦП.  
  
## <a name="see-also"></a>См. также:  
[Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[Управление событиями](../../ssms/agent/manage-events.md)  
  
