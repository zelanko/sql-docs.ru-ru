---
title: "Добавление строк на панели результатов (визуальные инструменты для баз данных) | Документация Майкрософт"
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
- View Designer, Results pane
- inserting rows
- Query Designer [SQL Server], Results pane
- Results pane
- adding rows
- row additions [SQL Server], Results pane
ms.assetid: 59891c84-3f54-4ab9-8b86-72c59627b480
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 736d3da284554a6657ff644bd9e3658a3bc06a0c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="add-new-rows-in-the-results-pane-visual-database-tools"></a>Добавление новых строк на панель результатов (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Новые данные можно добавлять, вводя их или копируя из другой программы, например из блокнота или приложения Excel. Чтобы можно было вставить строку, в ней должно быть ровно то же число столбцов тех же типов, что и в таблице, куда производится вставка. За раз на панель результатов можно вставить несколько строк.  
  
Сведения о вводе данных см. в разделе [Правила обновления результатов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/rules-for-updating-results-visual-database-tools.md).  
  
### <a name="to-add-a-new-data-row"></a>Добавление новой строки данных  
  
1.  Перейдите в нижнюю часть панели результатов, где есть пустая строка, в которую можно добавить новые данные.  
  
    Начальным значением всех столбцов будет *NULL*.  
  
    > [!TIP]  
    > Чтобы перейти сразу к первой пустой строке, воспользуйтесь панелью навигации в нижней части области результатов.  
  
2.  Если копируются строки из буфера обмена, выберите новую строку, нажав на кнопку слева от нее.  
  
    > [!NOTE]  
    > Если хотя бы одна вставляемая строка не может быть сохранена в базе данных, будет получено сообщение, в котором будет сказано, какие строки не удается сохранить.  
  
3.  Введите данные в новую строку. При копировании выберите **Вставка** из меню **Правка** .  
  
4.  Дайте строке зафиксироваться в базе данных.  
  
Если при сохранении строки произойдет ошибка, конструктор запросов и представлений отобразит соответствующее сообщение, а затем осуществит возврат к редактируемой строке. Можно выполнить следующее.  
  
-   Решить проблему, отредактировав строку.  
  
-   Отменить правку, нажав клавишу ESC. При нажатии клавиши ESC, если курсор находится в изменяемой ячейке, изменения в этой ячейке будут отменены. При нажатии клавиши ESC, если курсор находится в неизменяемой ячейке, будут отменены изменения во всей строке.  
  
## <a name="see-also"></a>См. также:  
[Работа с данными на панели результатов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/work-with-data-in-the-results-pane-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
