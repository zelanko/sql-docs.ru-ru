---
title: SQL Server мишеней расширенных событий | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- extended events [SQL Server], targets
ms.assetid: e281684c-40d1-4cf9-a0d4-7ea1ecffa384
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f7be4c1cc392516ffaf6d1e36fc10b93b517d772
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088871"
---
# <a name="sql-server-extended-events-targets"></a>SQL Server Extended Events Targets
  Целями расширенных событий [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] являются потребители события. Цели могут записывать события в файл, хранить данные событий в буфере памяти и cобирать статистические данные о событиях. Цели могут обрабатывать данные в синхронном или асинхронном режиме.  
  
 Структура расширенных событий гарантирует, что цели получают события единственный раз за сеанс.  
  
 Расширенные события предоставляют следующие цели, которые можно использовать в сеансах расширенных событий.  
  
-   [Счетчик событий](../../2014/database-engine/event-counter-target.md)  
  
     Подсчитывает все события, происходящие в ходе сеанса расширенных событий. Эта цель используется для получения сведений о характеристиках рабочей нагрузки без затрат на сбор всех событий. Это синхронная цель.  
  
-   [Файл событий](../../2014/database-engine/event-file-target.md)  
  
     Используется для записи выходных данных сеанса событий из полных буферов памяти на диск. Это асинхронная цель.  
  
-   [Попарное разбиение событий](../../2014/database-engine/event-pairing-target.md)  
  
     Многие типы событий происходят попарно, например получение и снятие блокировки. Эта цель позволяет определить, что указанное парное событие не произошло в правильной последовательности. Это асинхронная цель.  
  
-   [Трассировка событий Windows (ETW)](../relational-databases/extended-events/event-tracing-for-windows-target.md)  
  
     Предназначена для сопоставления событий [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с данными событий Windows или данными событий приложений. Это синхронная цель.  
  
-   [Отображения](../../2014/database-engine/histogram-target.md)  
  
     Используется для подсчета количества указанных событий на основании указанного действия или столбца события. Это асинхронная цель.  
  
-   [Кольцевой буфер](../../2014/database-engine/ring-buffer-target.md)  
  
     Используется для хранения данных о событиях в памяти по принципу очереди (FIFO) или по принципу FIFO для каждого события. Это асинхронная цель.  
  
## <a name="see-also"></a>См. также:  
 [Расширенные события](../relational-databases/extended-events/extended-events.md)   
 [SQL Server пакетов расширенных событий](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [Сеансы расширенных событий SQL Server](../relational-databases/extended-events/sql-server-extended-events-sessions.md)   
 [Подсистема расширенных событий SQL Server](../relational-databases/extended-events/sql-server-extended-events-engine.md)  
  
  
