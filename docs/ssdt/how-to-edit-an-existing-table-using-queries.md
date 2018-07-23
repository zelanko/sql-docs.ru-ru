---
title: Практическое руководство. Изменение существующих таблиц с помощью запросов | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 58f4de8e-97b4-4bcb-953f-f3d428432491
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 541310addcd1b9fec25038e962197a1b06eea34a
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088536"
---
# <a name="how-to-edit-an-existing-table-using-queries"></a>Как изменять существующие таблицы с помощью запросов
Вы можете вносить изменения в определение таблицы или ее данные, написав запрос Transact\-SQL. Для просмотра или ввода данных в таблицу с помощью пользовательского интерфейса служит редактор данных, как описано в руководстве по [разработке подключенной базы данных](../ssdt/connected-database-development.md).  
  
> [!WARNING]  
> В следующих процедурах используются сущности, созданные ранее с помощью руководства по [разработке подключенной базы данных](../ssdt/connected-database-development.md).  
  
### <a name="to-edit-the-definition-of-an-existing-table"></a>Изменение определения существующей таблицы  
  
1.  Разверните узел **Tables** базы данных **Trade** в **обозревателе объектов SQL Server** и щелкните правой кнопкой мыши таблицу **dbo.Suppliers**.  
  
2.  Выберите **Открыть в конструкторе**, чтобы просмотреть схему таблицы в конструкторе таблиц.  
  
3.  Установите флажок **Разрешить значения NULL** для столбца **Адрес**. Обратите внимание, что соответствующий код в области скриптов немедленно изменится на `NULL`.  
  
4.  [Обновите подключенную базу данных с помощью Power Buffer](../ssdt/how-to-update-a-connected-database-with-power-buffer.md).  
  
### <a name="to-populate-data-in-new-tables-using-a-transact-sql-query"></a>Заполнение данными новых таблиц с использованием запроса Transact\-SQL  
  
1.  Щелкните правой кнопкой мыши узел базы данных **Trade** и выберите **Создать запрос**.  
  
2.  В области скриптов вставьте следующий код.  
  
    ```  
    insert into dbo.Suppliers values  
    (1, 'NorthWind Traders', 'Seattle, WA'),  
    (2, 'Contoso', 'Tacoma, WA')  
    GO  
  
    insert dbo.Customer values  
    (1, 'Fourth Coffee')  
    GO  
  
    insert dbo.Products values  
    (1, 'Apples', 0, 1, 1),  
    (2, 'Instant Coffee', 1, 2, 1)  
    GO  
    ```  
  
3.  Чтобы выполнить этот запрос, нажмите кнопку **Выполнить запрос**. Если в области **Сообщение** появится следующий текст, это означает, что строки успешно добавлены к таблицам.  
  
**(Обработано строк: 2)(Обработано строк: 1)(Обработано строк: 2)**  
  
4.  Замените код в области скриптов следующим кодом и выполните запрос. Это равносильно попытке добавить новую строку к таблице `Products` со значением `ShelfLife`, равным 6.  
  
    ```  
    insert dbo.Products values  
    (3, 'Potato Chips', 6, 1, 1)  
    GO  
    ```  
  
5.  В области **Сообщение** будет указано, что инструкция `INSERT` конфликтует с существующим проверочным ограничением, которое ограничивает значение `ShelfLife` числом 5. Обновление таблицы Products не произойдет в связи с неудачным завершением инструкции из-за существующего ограничения.  
  
6.  Измените код на следующий и снова запустите запрос. Обратите внимание, что на этот раз обновление строки происходит успешно.  
  
    ```  
    insert dbo.Products values  
    (3, 'Potato Chips', 2, 1, 1)  
    GO  
    ```  
  
## <a name="see-also"></a>См. также:  
[Управление таблицами и связями, а также исправление ошибок](../ssdt/manage-tables-relationships-and-fix-errors.md)  
[Использование редактора Transact-SQL для изменения и выполнения скриптов](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md)  
  
