---
title: Запуск или остановка агента репликации (SSMS)
description: Узнайте, как запустить и остановить агент репликации в SQL Server Management Studio и мониторе репликации.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: f578311d9daa9e54830ad5aa8330fc8bc2c7ac71
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76288094"
---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a>Запуск и остановка агента репликации (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Запуск и остановка агентов выполняется из папки **Задания** и папки **Репликация** в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] и из монитора репликации. Могут запускаться и останавливаться следующие агенты и задания:  
  
-   Агент моментальных снимков, используемый всеми публикациями.  
  
-   Агент чтения журналов, используемый всеми публикациями транзакций.  
  
-   Агент чтения очереди, используемый публикациями транзакций, активированными для подписок, обновляемых посредством очередей.  
  
-   Агент распространителя, синхронизирующий подписки на публикации транзакций и моментальных снимков.  
  
-   Агент слияния, синхронизирующий подписки на публикации слиянием.  
  
-   Задания по обслуживанию репликации.  
  
 Дополнительные сведения о запуске агента слияния и агента распространения см. в статьях [Синхронизация принудительной подписки](../../../relational-databases/replication/synchronize-a-push-subscription.md) и [Синхронизация подписки по запросу](../../../relational-databases/replication/synchronize-a-pull-subscription.md). Дополнительные сведения о заданиях обслуживания см. в статье [Запуск заданий по обслуживанию репликаций (среда SQL Server Management Studio)](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md).  
  
 Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a>Запуск и остановка агента моментальных снимков или агента чтения журналов из среды Management Studio  
  
1.  Подключитесь к издателю в [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  Раскройте папку **Локальные публикации** , затем щелкните правой кнопкой публикацию.  
  
3.  Щелкните **Просмотреть состояние агента моментальных снимков** или **Просмотреть состояние агента чтения журнала**.  
  
4.  Щелкните **Пуск** или **Стоп**.  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a>Запуск и остановка агента чтения очереди из среды Management Studio  
  
1.  Подключитесь к распространителю в [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]и разверните узел сервера.  
  
2.  Раскройте папку **Агент SQL Server** , а затем — папку **Задания** .  
  
3.  Щелкните правой кнопкой задание для агента и выберите пункт **Запустить задание** или **Остановить задание**. Имя задания для агента чтения очереди имеет следующий формат: **[\<распространитель>].\<целое число>** .  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a>Запуск и остановка агента моментальных снимков, агента чтения журнала или агента чтения очереди из монитора репликации  
  
1.  Раскройте на левой панели группу издателей, раскройте издатель и выберите нужную публикацию.  
  
2.  Перейдите на вкладку **Агенты** .  
  
3.  Щелкните правой кнопкой агент и затем щелкните **Запустить агент** или **Остановить агент**.  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Replication Agents Overview](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
