---
title: Удаление ограничения уникальности | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- UNIQUE constraints [SQL Server], deleting
- constraints [SQL Server], deleting
- deleting constraints
- constraints [SQL Server], unique
ms.assetid: 71e563fc-f5d7-4c2e-a42f-f0695a831f32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8225039ece914c461af34f5344350227d6a39cdc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62761145"
---
# <a name="delete-unique-constraints"></a>Удаление ограничений уникальности
  Удалить ограничение уникальности в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно при помощи [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Удаление ограничения уникальности приводит к удалению требования уникальности значений, вводимых в столбцы или в сочетание столбцов, указанных в выражении ограничения, а также к удалению соответствующего уникального индекса.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Удаление ограничения уникальности с использованием:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-unique-constraint-using-object-explorer"></a>Удаление ограничения уникальности в обозревателе объектов  
  
1.  В обозревателе объектов разверните таблицу, содержащую ограничение уникальности, а затем разверните узел **Ограничения**.  
  
2.  Щелкните ключ правой кнопкой мыши и выберите команду **Удалить**.  
  
3.  В диалоговом окне **Удаление объекта** убедитесь в том, что выбран правильный ключ, и нажмите кнопку **ОК**.  
  
#### <a name="to-delete-a-unique-constraint-using-table-designer"></a>Удаление ограничения уникальности с помощью конструктора таблиц  
  
1.  В **Обозревателе объектов**щелкните таблицу с ограничением уникальности правой кнопкой мыши и выберите пункт **Конструктор**.  
  
2.  В меню **Конструктор таблиц** выберите пункт **Индексы и ключи**.  
  
3.  В диалоговом окне **Индексы и ключи** выберите уникальный ключ в списке **Выбранный первичный или уникальный ключ или индекс** .  
  
4.  Щелкните **Удалить**.  
  
5.  В меню **Файл** выберите пункт **Сохранить** _имя_таблицы_.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-delete-a-unique-constraint"></a>Удаление ограничения уникальности  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Return the name of unique constraint.  
    SELECT name  
    FROM sys.objects  
    WHERE type = 'UQ' AND OBJECT_NAME(parent_object_id) = N' DocExc';  
    GO  
    -- Delete the unique constraint.  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT UNQ_ColumnB_DocExc;  
    GO  
    ```  
  
 Дополнительные сведения см. в статьях [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql) и [sys.objects (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql).  
  
###  <a name="TsqlExample"></a>  
