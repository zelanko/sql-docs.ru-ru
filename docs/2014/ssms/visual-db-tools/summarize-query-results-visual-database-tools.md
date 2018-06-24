---
title: Резюмирование результатов запросов (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- summarizing query results
- queries [SQL Server], results
- aggregate queries [SQL Server]
ms.assetid: c9e15350-ed57-4d95-814d-815fbebfd86b
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d447d321d89da666d6db044ef9adac8b523d5656
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194164"
---
# <a name="summarize-query-results-visual-database-tools"></a>Резюмирование результатов запросов (визуальные инструменты для баз данных)
  К созданию статистических запросов следует применять определенные логические принципы. Например, невозможно вывести содержимое отдельных строк в сводном запросе. Конструктор запросов и представлений помогает соблюсти эти принципы — такое поведение заложено в [панель диаграммы](visual-database-tools.md) и [панель критериев](criteria-pane-visual-database-tools.md) .  
  
 Поняв принципы статистических запросов и поведение конструктора запросов и представлений, можно создавать логически безошибочные статистические запросы. Важнейший принцип гласит, что статистические запросы могут выдавать только сводные данные. Таким образом, большинство остальных принципов описывают способы создания в статистическом запросе ссылок на отдельные столбцы данных.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Работа со столбцами в статистических запросах (визуальные инструменты для баз данных)](work-with-columns-in-aggregate-queries-visual-database-tools.md)  
 Описывает концепции группирования и суммирования столбцов при помощи предложений GROUP BY, WHERE и HAVING.  
  
 [Подсчет строк в таблице (визуальные инструменты для баз данных)](count-rows-in-a-table-visual-database-tools.md)  
 Пошаговые инструкции для подсчета количества строк в таблице или количество строк в таблице, отвечающих набору критериев.  
  
 [Получение суммарных или статистических значений для всех строк в таблице (визуальные инструменты для баз данных)](summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)  
 Пошаговые инструкции относительно суммирования всех строк, а не набора сгруппированных строк.  
  
 [Суммирование значения или выполнение статистической обработки с помощью пользовательских выражений (визуальные инструменты для баз данных)](summarize-or-aggregate-values-using-custom-expressions-visual-database-tools.md)  
 Пошаговые инструкции по использованию выражений для суммирования и выполнения статистической обработки вместо стандартных предложений.  
  
## <a name="related-sections"></a>См. также  
 [Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 Предоставляет ссылки на разделы, объясняющие как использовать конструктор запросов и представлений.  
  
  