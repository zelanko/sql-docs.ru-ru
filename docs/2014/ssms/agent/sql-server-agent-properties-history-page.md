---
title: Свойства агента SQL Server (страница "Журнал") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4008df15ded37398ef8565bac759364699561fad
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058688"
---
# <a name="sql-server-agent-properties-history-page"></a>Свойства агента SQL Server (страница «Журнал»)
  Эта страница используется для просмотра и изменения параметров [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] журнала службы агента.  
  
## <a name="options"></a>Варианты  
 **Ограничить размер журнала заданий**  
 Ограничивает объем данных, которые агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохраняет в журнале заданий.  
  
 **Максимальный размер журнала заданий (в строках)**  
 Максимальное число строк, записываемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При увеличении объема журнала до указанной границы для записи новых строк агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаляет наиболее старые строки в журнале.  
  
 **Максимальное число строк в журнале заданий для одного задания**  
 Максимальное количество строк, записываемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для одного задания. При увеличении объема журнала для указанного задания до указанной границы для записи новых строк агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаляет наиболее старые строки в журнале.  
  
 **Удаление журнала агента**  
 Вызывает удаление агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записей со сроком давности больше заданного. Это однократное выполнение для удаления журнала. Для выполнения повторяющегося задания создайте план обслуживания с заданием очистки и расписание для него.  
  
 **Срок давности**  
 Срок, в течение которого агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит записи.  
  
## <a name="see-also"></a>См. также:  
 [Журнал ошибок агента SQL Server](sql-server-agent-error-log.md)  
  
  
