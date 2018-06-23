---
title: Свойства агента SQL Server (страница "Журнал") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e882745886a3a9a2c2575461d96d24355e2139bb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098092"
---
# <a name="sql-server-agent-properties-history-page"></a>Свойства агента SQL Server (страница «Журнал»)
  На этой странице можно просмотреть и изменить параметры журнала службы агента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Параметры  
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
  
## <a name="see-also"></a>См. также  
 [Журнал ошибок агента SQL Server](sql-server-agent-error-log.md)  
  
  