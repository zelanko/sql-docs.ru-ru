---
title: "Резюмирование результатов запросов (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- summarizing query results
- queries [SQL Server], results
- aggregate queries [SQL Server]
ms.assetid: c9e15350-ed57-4d95-814d-815fbebfd86b
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 37946b24586881c8a9105fd882af71dd075ab7ab
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="summarize-query-results-visual-database-tools"></a>Резюмирование результатов запросов (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] К созданию статистических запросов следует применять определенные логические принципы. Например, невозможно вывести содержимое отдельных строк в сводном запросе. Конструктор запросов и представлений помогает соблюсти эти принципы — такое поведение заложено в [панель диаграммы](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) и [панель критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md) .  
  
Поняв принципы статистических запросов и поведение конструктора запросов и представлений, можно создавать логически безошибочные статистические запросы. Важнейший принцип гласит, что статистические запросы могут выдавать только сводные данные. Таким образом, большинство остальных принципов описывают способы создания в статистическом запросе ссылок на отдельные столбцы данных.  
  
## <a name="in-this-section"></a>в этом разделе  
[Работа со столбцами в статистических запросах (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/work-with-columns-in-aggregate-queries-visual-database-tools.md)  
Описывает концепции группирования и суммирования столбцов при помощи предложений GROUP BY, WHERE и HAVING.  
  
[Подсчет строк в таблице (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/count-rows-in-a-table-visual-database-tools.md)  
Пошаговые инструкции для подсчета количества строк в таблице или количество строк в таблице, отвечающих набору критериев.  
  
[Получение суммарных или статистических значений для всех строк в таблице (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)  
Пошаговые инструкции относительно суммирования всех строк, а не набора сгруппированных строк.  
  
[Суммирование значения или выполнение статистической обработки с помощью пользовательских выражений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-or-aggregate-values-using-custom-expressions-visual-database-tools.md)  
Пошаговые инструкции по использованию выражений для суммирования и выполнения статистической обработки вместо стандартных предложений.  
  
## <a name="related-sections"></a>См. также  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
Предоставляет ссылки на разделы, объясняющие как использовать конструктор запросов и представлений.  
  
