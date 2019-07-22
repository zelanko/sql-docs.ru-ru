---
title: Свойства агента SQL Server (страница "Журнал") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 098ce57a7565e50c1f52301c9c567087b9dbc620
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265264"
---
# <a name="sql-server-agent-properties-history-page"></a>Свойства агента SQL Server (страница «Журнал»)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

На этой странице можно просмотреть и изменить параметры журнала службы агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
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
  
## <a name="see-also"></a>См. также:  
[Журнал ошибок агента SQL Server](../../ssms/agent/sql-server-agent-error-log.md)  
  
