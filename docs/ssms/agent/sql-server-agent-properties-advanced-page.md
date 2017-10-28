---
title: "Свойства агента SQL Server (страница \"Дополнительно\") | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7239a45e4c3761919503a50f64168e266c58a0f5
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-agent-properties-advanced-page"></a>Свойства агента SQL Server (страница «Дополнительно»)
Эта страница используется для просмотра и изменения дополнительных свойств службы агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
## <a name="options"></a>Параметры  
**Пересылка событий SQL Server**  
Параметры в данной категории активируют и настраивают пересылку событий.  
  
**Переслать события на другой сервер**  
Перенаправляет события агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] другому серверу.  
  
**Server**  
Выберите имя сервера, которому нужно перенаправить события.  
  
**Необработанные события**  
Переправляет заданному серверу только необработанные события. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] перенаправляет только события, на которые не реагирует ни одно предупреждение.  
  
**Все события**  
Переправляет все события. Если предупреждение локального экземпляра реагирует на событие, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] перенаправит этот событие и обработает предупреждение.  
  
**Если серьезность события равна или превышает**  
Пересылает только события, уровень серьезности которых равен указанному или превышает его.  
  
**Условие простоя ЦП**  
Параметры в данной категории определяют условия, при которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] запускает задания, запланированные к выполнению в расписании простоя ЦП.  
  
**Определить условие простоя ЦП**  
Определяет условия, при которых агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] считает, что ЦП простаивает.  
  
**Среднее время использования ЦП сократилось до**  
Процент использования ЦП сократился до уровня, при котором считается, что ЦП простаивает.  
  
**И остается ниже этого уровня в течение**  
Отрезок времени, который средний ЦП должен простаивать, прежде чем агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] запустит задания по расписанию простоя ЦП.  
  
## <a name="see-also"></a>См. также:  
[Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[Управление событиями](../../ssms/agent/manage-events.md)  
  

