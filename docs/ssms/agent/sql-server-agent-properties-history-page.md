---
title: "Свойства агента SQL Server (страница \"Журнал\") | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: de59a618dc53759a837a6855b5b89a9daa3552fc
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-agent-properties-history-page"></a>Свойства агента SQL Server (страница «Журнал»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] На этой странице можно просмотреть и изменить параметры журнала службы агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
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
  
