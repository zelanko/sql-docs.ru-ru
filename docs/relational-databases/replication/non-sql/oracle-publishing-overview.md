---
title: Обзор публикации Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], Oracle publishing
- snapshot replication [SQL Server], Oracle publishing
- Oracle publishing [SQL Server replication]
- transactional replication, Oracle publishing
- Oracle publishing [SQL Server replication], about Oracle publishing
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02d36b72c949db673bcc2d00918bd7571821d025
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111086"
---
# <a name="oracle-publishing-overview"></a>Oracle Publishing Overview  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Начиная с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], в топологию репликации можно включать издателей Oracle, начиная с Oracle версии 9i. Серверы публикаций можно развернуть на любом оборудовании и под управлением любой операционной системы, поддерживаемой Oracle. Эта функция, разработанная на базе репликации моментальных снимков и репликации транзакций [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , представляет аналогичные производительность и удобство работы.  
  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает следующие разнородные сценарии для репликации транзакций и репликации моментальных снимков.  
  
-   Публикация данных с подписчиков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на подписчики, отличные от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  

-   Публикация данных в Oracle и из Oracle имеет следующие ограничения:  
  | |2016 или более ранние версии |2017 или более поздние версии |
  |-------|-------|--------|
  |Репликация из Oracle |Поддержка только Oracle 10g или более ранних версий |Поддержка только Oracle 10g или более ранних версий |
  |Репликация в Oracle |Версии до Oracle 12c |Не поддерживается |


 Разнородная репликация на подписчики, отличные от подписчика SQL Server, устарела. Публикация Oracle устарела. Для перемещения данных создайте решения с помощью системы отслеживания измененных данных и служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  

  
## <a name="snapshot-replication-for-oracle"></a>Репликация моментальных снимков для Oracle  
 Публикации моментальных снимков Oracle реализованы в стиле публикации моментальных снимков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Когда агент моментальных снимков запущен для публикации Oracle, он создает соединение с издателем Oracle и обрабатывает каждую таблицу в публикации. Обрабатывая каждую таблицу, агент получает строки таблицы и создает скрипты схемы, которые затем сохраняются в хранилище моментального снимка публикации. Полный набор данных создается при каждом запуске агента моментальных снимков, по этой причине триггеры отслеживания изменений не добавляются в таблицы Oracle, как в случае репликации транзакций. Репликация моментальных снимков предоставляет удобный способ переноса данных с минимальным воздействием на публикующую систему.  
  
## <a name="transactional-replication-for-oracle"></a>Репликация транзакций для Oracle  
 Публикации транзакций Oracle реализованы с помощью архитектуры публикации транзакций [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Однако изменения отслеживаются при помощи сочетания триггеров базы данных в базе данных Oracle и агента чтения журнала. Подписчики на публикацию транзакций Oracle автоматически инициализируются с помощью репликации моментальных снимков; последующие изменения отслеживаются и доставляются подписчикам с помощью агента чтения журнала.  
  
 Когда создается публикация Oracle, для каждой опубликованной таблицы в базе данных Oracle создаются триггеры и таблицы отслеживания. При внесении изменений в опубликованные таблицы срабатывают триггеры базы данных и данные вставляются в таблицы отслеживания репликации по каждой измененной строке. Затем агент чтения журнала на распространителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] перемещает сведения об изменении данных из таблиц отслеживания в базу данных распространителя на стороне распространителя. Наконец, как и при обычной репликации транзакций, агент распространителя перемещает изменения от распространителя подписчикам.  
  
## <a name="see-also"></a>См. также:  
 [Настройка издателя Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Глоссарий терминов по публикации Oracle](../../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Разнородная репликация базы данных](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  
