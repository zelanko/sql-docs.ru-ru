---
description: Удаление ограничений уникальности
title: Удаление ограничения уникальности | Документация Майкрософт
ms.custom: ''
ms.date: 10/12/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 95234d86bc68c063d90226bb23e09533bea446ae
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446433"
---
# <a name="delete-unique-constraints"></a>Удаление ограничений уникальности
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Удалить ограничение уникальности в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно при помощи [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Удаление ограничения уникальности приводит к удалению требования уникальности значений, вводимых в столбцы или в сочетание столбцов, указанных в выражении ограничения, а также к удалению соответствующего уникального индекса.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Удаление ограничения уникальности с использованием:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-delete-a-unique-constraint-using-object-explorer"></a>Удаление ограничения уникальности в обозревателе объектов  
  
1.  В обозревателе объектов разверните таблицу, содержащую ограничение уникальности, а затем разверните узел **Ограничения**.  
  
2.  Щелкните ключ правой кнопкой мыши и выберите команду **Удалить**.  
  
3.  В диалоговом окне **Удаление объекта** убедитесь в том, что выбран правильный ключ, и нажмите кнопку **ОК**.  
  
#### <a name="to-delete-a-unique-constraint-using-table-designer"></a>Удаление ограничения уникальности с помощью конструктора таблиц  
  
1.  В **Обозревателе объектов**щелкните таблицу с ограничением уникальности правой кнопкой мыши и выберите пункт **Конструктор**.  
  
2.  В меню **Конструктор таблиц** выберите пункт **Индексы и ключи**.  
  
3.  В диалоговом окне **Индексы и ключи** выберите уникальный ключ в списке **Выбранный первичный или уникальный ключ или индекс** .  
  
4.  Щелкните **Удалить**.  
  
5.  В меню **Файл** выберите команду **Сохранить** _имя_таблицы_.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
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
