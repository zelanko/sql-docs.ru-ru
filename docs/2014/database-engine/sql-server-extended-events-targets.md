---
title: Цели расширенных событий SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
caps.latest.revision: 50
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ba3ea863b35142c65b2e5f38789f888d603b6977
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160985"
---
# <a name="sql-server-extended-events-targets"></a>SQL Server Extended Events Targets
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Целями расширенных событий являются потребители события. Цели могут записывать события в файл, хранить данные событий в буфере памяти и cобирать статистические данные о событиях. Цели могут обрабатывать данные в синхронном или асинхронном режиме.  
  
 Структура расширенных событий гарантирует, что цели получают события единственный раз за сеанс.  
  
 Расширенные события предоставляют следующие цели, которые можно использовать в сеансах расширенных событий.  
  
-   [Счетчик событий](../../2014/database-engine/event-counter-target.md)  
  
     Подсчитывает все события, происходящие в ходе сеанса расширенных событий. Эта цель используется для получения сведений о характеристиках рабочей нагрузки без затрат на сбор всех событий. Это синхронная цель.  
  
-   [Файл событий](../../2014/database-engine/event-file-target.md)  
  
     Используется для записи выходных данных сеанса событий из полных буферов памяти на диск. Это асинхронная цель.  
  
-   [Попарное разбиение событий](../../2014/database-engine/event-pairing-target.md)  
  
     Многие типы событий происходят попарно, например получение и снятие блокировки. Эта цель позволяет определить, что указанное парное событие не произошло в правильной последовательности. Это асинхронная цель.  
  
-   [События трассировки событий Windows (ETW)](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     Предназначена для сопоставления событий [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с данными событий Windows или данными событий приложений. Это синхронная цель.  
  
-   [Гистограммы](../../2014/database-engine/histogram-target.md)  
  
     Используется для подсчета количества указанных событий на основании указанного действия или столбца события. Это асинхронная цель.  
  
-   [Кольцевой буфер](../../2014/database-engine/ring-buffer-target.md)  
  
     Используется для хранения данных о событиях в памяти по принципу очереди (FIFO) или по принципу FIFO для каждого события. Это асинхронная цель.  
  
## <a name="see-also"></a>См. также  
 [Расширенные события](../relational-databases/extended-events/extended-events.md)   
 [Пакеты обработки расширенных событий SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [SQL Server Extended Events Sessions](../relational-databases/extended-events/sql-server-extended-events-sessions.md)   
 [Подсистема расширенных событий SQL Server](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  
