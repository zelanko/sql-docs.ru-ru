---
title: "Автоматическое соединение самосоединения (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c25ca1aa33e069fdb08d58196d274aa2198ae3af
ms.lasthandoff: 04/11/2017

---
# <a name="create-self-joins-automatically-visual-database-tools"></a>Автоматическое создание самосоединения (визуальные инструменты для баз данных)
Если таблица имеет рефлексивную связь в базе данных, можно автоматически создать самосоединение.  
  
### <a name="to-create-a-self-join-automatically"></a>Автоматическое создание самосоединения  
  
1.  Добавьте на [панель диаграмм](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) нужную таблицу.  
  
2.  Еще раз добавьте эту таблицу, чтобы на панели диаграмм эта таблица была показана дважды.  
  
    [Конструктор запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) присваивает второму экземпляру псевдоним, добавляя порядковый номер к имени таблицы. Кроме того, конструктор запросов и представлений создает линию соединения между двумя прямоугольниками, представляющими два разных способа, которыми таблица участвует в запросе.  
  
## <a name="see-also"></a>См. также:  
[Запросы с соединениями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  

