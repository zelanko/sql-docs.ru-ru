---
title: Обзор публикации Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publishing [SQL Server replication], Oracle publishing
- snapshot replication [SQL Server], Oracle publishing
- Oracle publishing [SQL Server replication]
- transactional replication, Oracle publishing
- Oracle publishing [SQL Server replication], about Oracle publishing
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
caps.latest.revision: 39
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 595547640aa5fb2647208cf092448d691ea92027
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192646"
---
# <a name="oracle-publishing-overview"></a>Oracle Publishing Overview
  Начиная с [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], в топологию репликации можно включать издателей Oracle, начиная с Oracle версии 9i. Серверы публикаций можно развернуть на любом оборудовании и под управлением любой операционной системы, поддерживаемой Oracle. Эта функция, разработанная на базе репликации моментальных снимков и репликации транзакций [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , представляет аналогичные производительность и удобство работы.  
  
 Публикация Oracle устарела. Разнородная репликация на подписчики, отличные от подписчика SQL Server, устарела. Для перемещения данных создайте решения с помощью системы отслеживания измененных данных и служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="snapshot-replication-for-oracle"></a>Репликация моментальных снимков для Oracle  
 Публикации моментальных снимков Oracle реализованы в стиле публикации моментальных снимков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Когда агент моментальных снимков запущен для публикации Oracle, он создает соединение с издателем Oracle и обрабатывает каждую таблицу в публикации. Обрабатывая каждую таблицу, агент получает строки таблицы и создает скрипты схемы, которые затем сохраняются в хранилище моментального снимка публикации. Полный набор данных создается при каждом запуске агента моментальных снимков, по этой причине триггеры отслеживания изменений не добавляются в таблицы Oracle, как в случае репликации транзакций. Репликация моментальных снимков предоставляет удобный способ переноса данных с минимальным воздействием на публикующую систему.  
  
## <a name="transactional-replication-for-oracle"></a>Репликация транзакций для Oracle  
 Публикации транзакций Oracle реализованы с помощью архитектуры публикации транзакций [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Однако изменения отслеживаются при помощи сочетания триггеров базы данных в базе данных Oracle и агента чтения журнала. Подписчики на публикацию транзакций Oracle автоматически инициализируются с помощью репликации моментальных снимков; последующие изменения отслеживаются и доставляются подписчикам с помощью агента чтения журнала.  
  
 Когда создается публикация Oracle, для каждой опубликованной таблицы в базе данных Oracle создаются триггеры и таблицы отслеживания. При внесении изменений в опубликованные таблицы срабатывают триггеры базы данных и данные вставляются в таблицы отслеживания репликации по каждой измененной строке. Затем агент чтения журнала на распространителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] перемещает сведения об изменении данных из таблиц отслеживания в базу данных распространителя на стороне распространителя. Наконец, как и при обычной репликации транзакций, агент распространителя перемещает изменения от распространителя подписчикам.  
  
## <a name="see-also"></a>См. также  
 [Настройка издателя Oracle](configure-an-oracle-publisher.md)   
 [Глоссарий терминов по публикации Oracle](glossary-of-terms-for-oracle-publishing.md)   
 [Разнородная репликация базы данных](heterogeneous-database-replication.md)  
  
  