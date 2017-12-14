---
title: "Удаление соединений (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dfa07daeea3832a3149a9549a55ffd8c6d3d37f2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="remove-joins-visual-database-tools"></a>Удаление соединений (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Если нежелательно, чтобы таблицы были соединены с помощью внутреннего или внешнего соединения, можно удалить это соединение между таблицами. Например, можно удалить соединение, автоматически созданное между двумя таблицами в [конструкторе запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) .  
  
> [!NOTE]  
> Удаление соединения из запроса не влияет на базовые связи, существующие в базе данных.  
  
Если две соединяемые таблицы являются частью запроса и все условия соединения между ними удаляются, то результирующий запрос становится пересечением этих таблиц, то есть перекрестным соединением (CROSS JOIN).  
  
### <a name="to-remove-a-join"></a>Удаление соединения  
  
-   На [панели диаграммы](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)выберите удаляемую линию соединения и нажмите клавишу DELETE. Можно одновременно выбрать и удалить несколько линий соединений.  
  
Конструктор запросов и представлений удаляет линию соединения и изменяет инструкцию на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также:  
[Автоматическое соединение таблиц (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)  
[Соединение таблиц вручную (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md)  
[Запросы с соединениями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
