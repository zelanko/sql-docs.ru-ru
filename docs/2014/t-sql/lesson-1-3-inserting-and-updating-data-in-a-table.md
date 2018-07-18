---
title: Вставка данных в таблицу и их обновление (учебник) | Документы Майкрософт
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
- inserting and updating data
ms.assetid: 514dc87a-b829-43b5-8fc8-1a400a260284
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d9dc8bbbc16ef6ed827e5d5ce2bdd95979b67068
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157484"
---
# <a name="inserting-and-updating-data-in-a-table-tutorial"></a>Вставка данных в таблицу и их обновление (учебник)
  После создания таблицы **Products** можно вставлять данные в таблицу с помощью инструкции INSERT. После вставки данных содержимое строки изменяется с помощью инструкции UPDATE. Предложение WHERE предназначено для ограничения числа строк, изменяемых в процессе выполнения инструкции UPDATE до одной строки. Чтобы ввести следующие данные, потребуется четыре инструкции.  
  
|ProductID|ProductName|Price|ProductDescription|  
|---------------|-----------------|-----------|------------------------|  
|1|Clamp|12,48|Workbench clamp|  
|50|Screwdriver|3,17|Flat head|  
|75|Tire Bar||Tool for changing tires.|  
|3000|3mm Bracket|0,52||  
  
 Базовый синтаксис: INSERT, имя таблицы, список столбцов, VALUES, а затем список добавляемых значений. Два дефиса в начале строки означают, что строка является примечанием и текст не будет обрабатываться компилятором. В этом случае примечание описывает возможные варианты синтаксиса.  
  
### <a name="to-insert-data-into-a-table"></a>Вставка данных в таблицу  
  
1.  Выполните следующую инструкцию, чтобы добавить строку в таблицу `Products` , которая была создана в предыдущей задаче. Далее представлен базовый синтаксис.  
  
    ```  
    -- Standard syntax  
    INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
        VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
    GO  
  
    ```  
  
2.  В следующей инструкции показано, как можно изменить порядок, в котором приведены параметры, изменив расположение `ProductID` и `ProductName` одновременно как в списке полей (в круглых скобках), так и в списке значений.  
  
    ```  
    -- Changing the order of the columns  
    INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
        VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
    GO  
  
    ```  
  
3.  Следующая инструкция показывает, что имена столбцов перечислять не обязательно, если значения перечислены в нужном порядке. Этот синтаксис является стандартным, но не рекомендуется, поскольку другим будет трудно понять ваш код. `NULL` указано в столбце `Price` , так как цена этого товара пока неизвестна.  
  
    ```  
    -- Skipping the column list, but keeping the values in order  
    INSERT dbo.Products  
        VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
    GO  
  
    ```  
  
4.  Имя схемы указывать не обязательно, пока доступ и изменение таблицы осуществляются с помощью схемы по умолчанию. Поскольку в столбце `ProductDescription` разрешены значения NULL и значение для столбца не приведено, имя и значение столбца `ProductDescription` в инструкции могут быть полностью опущены.  
  
    ```  
    -- Dropping the optional dbo and dropping the ProductDescription column  
    INSERT Products (ProductID, ProductName, Price)  
        VALUES (3000, '3mm Bracket', .52)  
    GO  
    ```  
  
### <a name="to-update-the-products-table"></a>Обновление таблицы продуктов  
  
1.  Введите и выполните следующую инструкцию `UPDATE` , чтобы изменить значение `ProductName` второго продукта со значения `Screwdriver`на значение `Flat Head Screwdriver`.  
  
    ```  
    UPDATE dbo.Products  
        SET ProductName = 'Flat Head Screwdriver'  
        WHERE ProductID = 50  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Чтение данных в таблице &#40;учебника&#41;](lesson-1-4-reading-the-data-in-a-table.md)  
  
## <a name="see-also"></a>См. также  
 [INSERT (Transact-SQL)](/sql/t-sql/statements/insert-transact-sql)   
 [UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql)  
  
  
