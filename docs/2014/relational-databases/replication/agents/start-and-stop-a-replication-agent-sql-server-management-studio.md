---
title: Запуск и остановка агента репликации (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
caps.latest.revision: 40
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 70011cb38e22d94b72eb41ccb01f10a7739c05d9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281230"
---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a>Запуск и остановка агента репликации (среда SQL Server Management Studio)
  Запуск и остановка агентов выполняется из папки **Задания** и папки **Репликация** в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from Репликация Monitor. Могут запускаться и останавливаться следующие агенты и задания:  
  
-   Агент моментальных снимков, используемый всеми публикациями.  
  
-   Агент чтения журналов, используемый всеми публикациями транзакций.  
  
-   Агент чтения очереди, используемый публикациями транзакций, активированными для подписок, обновляемых посредством очередей.  
  
-   Агент распространителя, синхронизирующий подписки на публикации транзакций и моментальных снимков.  
  
-   Агент слияния, синхронизирующий подписки на публикации слиянием.  
  
-   Задания по обслуживанию репликации.  
  
 Дополнительные сведения о запуске агента слияния и агента распространения см. в статьях [Синхронизация принудительной подписки](../synchronize-a-push-subscription.md) и [Синхронизация подписки по запросу](../synchronize-a-pull-subscription.md). Дополнительные сведения о заданиях обслуживания см. в статье [Запуск заданий по обслуживанию репликаций (среда SQL Server Management Studio)](../../../ssms/sql-server-management-studio-ssms.md).  
  
 Сведения о запуске монитора репликации см. в [этой статье](../monitor/start-the-replication-monitor.md).  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a>Запуск и остановка агента моментальных снимков или агента чтения журналов из среды Management Studio  
  
1.  Подключитесь к издателю в [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера и папку **Репликация** .  
  
2.  Раскройте папку **Локальные публикации** , затем щелкните правой кнопкой публикацию.  
  
3.  Щелкните **Просмотреть состояние агента моментальных снимков** или **Просмотреть состояние агента чтения журнала**.  
  
4.  Щелкните **Пуск** или **Стоп**.  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a>Запуск и остановка агента чтения очереди из среды Management Studio  
  
1.  Подключитесь к распространителю в [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Агент SQL Server** , а затем — папку **Задания** .  
  
3.  Щелкните правой кнопкой задание для агента и выберите пункт **Запустить задание** или **Остановить задание**. Имя задания для агента чтения очереди имеет следующий формат: **[\<распространитель>].\<целое число>**.  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a>Запуск и остановка агента моментальных снимков, агента чтения журнала или агента чтения очереди из монитора репликации  
  
1.  Раскройте на левой панели группу издателей, раскройте издатель и выберите нужную публикацию.  
  
2.  Перейдите на вкладку **Агенты** .  
  
3.  Щелкните правой кнопкой агент и затем щелкните **Запустить агент** или **Остановить агент**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией](../monitoring-replication.md)   
 [Основные понятия исполняемых файлов агента репликации](../concepts/replication-agent-executables-concepts.md)   
 [Replication Agents Overview](replication-agents-overview.md)  
  
  
