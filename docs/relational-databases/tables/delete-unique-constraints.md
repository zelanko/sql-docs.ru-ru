---
title: "Удаление ограничения уникальности | Документация Майкрософт"
ms.custom: 
ms.date: 10/12/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing constraints
- UNIQUE constraints [SQL Server], deleting
- constraints [SQL Server], deleting
- deleting constraints
- constraints [SQL Server], unique
ms.assetid: 71e563fc-f5d7-4c2e-a42f-f0695a831f32
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 49169c8ac7e47e6b9d9efff891810c68372aa6c5
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="delete-unique-constraints"></a>Удаление ограничений уникальности
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Удалить ограничение уникальности в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно при помощи [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Удаление ограничения уникальности приводит к удалению требования уникальности значений, вводимых в столбцы или в сочетание столбцов, указанных в выражении ограничения, а также к удалению соответствующего уникального индекса.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Удаление ограничения уникальности с использованием:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
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
  
5.  В меню **Файл** выберите пункт **Сохранить** *table name*.  
  
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
  
 Дополнительные сведения см. в статьях [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md) и [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  

