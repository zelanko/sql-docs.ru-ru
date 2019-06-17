---
title: Добавление отступов | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9dce05c1-c52f-455d-8b8d-6f303e242760
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 009f61563548e0c060350a75e9627804e18a7c54
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63222952"
---
# <a name="adding-indentation"></a>Добавление отступов
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
  
     ![Внешний вид диалогового окна "Вкладки"](media/tabsdialog.gif "Внешний вид диалогового окна \"Вкладки\"")  
  
3.  Нажмите кнопку **ОК**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Разворачивание окна редактора запросов](lesson-2-3-maximizing-query-editor.md)  
  
  
