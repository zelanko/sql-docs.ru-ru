---
title: "Урок 1. преобразование таблицы в иерархическую структуру | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "HierarchyID"
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Урок 1. преобразование таблицы в иерархическую структуру
Если у клиентов имеются таблицы, в которых для выражения иерархических связей используются самосоединения, то эти таблицы можно преобразовать в иерархическую структуру, руководствуясь указаниями из данного занятия. Миграция от старого метода представления к методу представления, использующему тип данных **hierarchyid**, проходит относительно легко. После миграции пользователи получат компактное и легкое для понимания иерархическое представление, которое может быть проиндексировано несколькими способами для обеспечения эффективного поиска.  
  
В этом занятии происходит изучение существующей таблицы, создание новой таблицы, содержащей столбец **hierarchyid** , заполнение этой таблицы данными из таблицы источника, а также проводится демонстрация трех стратегий индексирования. Это занятие содержит следующие разделы:  
  
-   [Изучение текущей структуры таблицы сотрудников](../../relational-databases/tables/examining-the-current-structure-of-the-employee-table.md)  
  
-   [Заполнение таблицы существующими иерархическими данными](../../relational-databases/tables/populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Оптимизация таблицы NewOrg](../../relational-databases/tables/optimizing-the-neworg-table.md)  
  
-   [Сводка. преобразование таблицы в иерархическую структуру](../../relational-databases/tables/summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## Предварительные требования  
Для этого занятия требуется образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## Следующая задача занятия  
[Изучение текущей структуры таблицы сотрудников](../../relational-databases/tables/examining-the-current-structure-of-the-employee-table.md)  
  
## Следующее занятие  
[Занятие 2. Создание данных и управление ими в иерархической таблице](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
  
