---
title: "Добавление отступов | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 5db067d5a2fe5bbf9953484c9a999ed7b1fcddae
ms.openlocfilehash: 55241a0b99024f557718654869d0ab728089e569
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="lesson-2-2---adding-indentation"></a>Занятие 2–2. Добавление отступов
Редактор запросов позволяет одновременно задать отступ для больших участков кода, а также изменить величину отступа.  
  
## <a name="indenting-code"></a>Добавление отступов кода  
  
#### <a name="to-indent-multiple-lines-of-code"></a>Добавление отступа для нескольких строк кода  
  
1.  На панели инструментов нажмите кнопку **Создать запрос**.  
  
2.  Создайте второй запрос, который выбирает значения столбцов **BusinessEntityID**, FirstName, **MiddleName**и **LastName** из таблицы **Person** схемы **Person** . Разместите каждый столбец на отдельной строке, чтобы код выглядел следующим образом:  
  
    ```  
    -- Search for a contact  
    SELECT   
    BusinessEntityID,  
    FirstName,   
    MiddleName,   
    LastName  
    FROM Person.Person  
    WHERE LastName = 'Sanchez';  
    GO  
    ```  
  
3.  Выделите весь текст, содержащийся в столбцах с `BusinessEntityID` по `LastName`.  
  
4.  Чтобы добавить отступ для всех выбранных строк, на панели инструментов **Редактор SQL** нажмите кнопку **Увеличить отступ** .  
  
#### <a name="to-change-the-default-indentation"></a>Изменение указанного по умолчанию отступа  
  
1.  В меню **Сервис** выберите **Параметры**.  
  
2.  Последовательно раскройте элементы **Текстовый редактор**и **Все языки**, а затем нажмите **Вкладки** и установите необходимые значения отступов. Обратите внимание, что можно изменять как значения отступов, так и значение табуляции, а также указать, следует ли заменять знаки табуляции пробелами.  
  
    ![Внешний вид диалогового окна "Вкладки"](./media/lesson-2-2-adding-indentation/tabsdialog.gif "Внешний вид диалогового окна "Вкладки"")  
  
3.  Нажмите кнопку **ОК**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Разворачивание окна редактора запросов](../../tools/sql-server-management-studio/lesson-2-3-maximizing-query-editor.md)  
  
  
  

