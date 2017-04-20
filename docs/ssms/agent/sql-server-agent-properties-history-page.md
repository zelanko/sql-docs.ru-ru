---
title: "Свойства агента SQL Server (страница &quot;Журнал&quot;) | Документация Майкрософт"
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
- sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 51839ab3d459e2350c582810fe003fc5086de3eb
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-agent-properties-history-page"></a>Свойства агента SQL Server (страница «Журнал»)
На этой странице можно просмотреть и изменить параметры журнала службы агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
## <a name="options"></a>Параметры  
**Ограничить размер журнала заданий**  
Ограничивает объем данных, которые агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] сохраняет в журнале заданий.  
  
**Максимальный размер журнала заданий (в строках)**  
Максимальное число строк, записываемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . При увеличении объема журнала до указанной границы для записи новых строк агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] удаляет наиболее старые строки в журнале.  
  
**Максимальное число строк в журнале заданий для одного задания**  
Максимальное количество строк, записываемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для одного задания. При увеличении объема журнала для указанного задания до указанной границы для записи новых строк агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] удаляет наиболее старые строки в журнале.  
  
**Удаление журнала агента**  
Вызывает удаление агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] записей со сроком давности больше заданного. Это однократное выполнение для удаления журнала. Для выполнения повторяющегося задания создайте план обслуживания с заданием очистки и расписание для него.  
  
**Срок давности**  
Срок, в течение которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] хранит записи.  
  
## <a name="see-also"></a>См. также:  
[Журнал ошибок агента SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  

