---
title: Просмотр зависимостей таблицы | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- table dependencies [SQL Server]
- dependencies [SQL Server], tables
- displaying dependences
- viewing dependencies
ms.assetid: c4351ef5-e7d0-46e7-8367-88695e9974f8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 313d128d0323c8400828e43c7d80f94614950ee5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080844"
---
# <a name="view-the-dependencies-of-a-table"></a>Просмотр зависимостей таблицы
  Зависимости таблицы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно просмотреть в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Просмотр зависимостей таблицы с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение VIEW DEFINITION в базе данных и разрешение SELECT на представление sys.sql_expression_dependencies в базе данных. По умолчанию разрешение SELECT предоставляется только членам предопределенной роли базы данных db_owner. Если разрешения SELECT и VIEW DEFINITION предоставлены другому пользователю, он может просматривать все зависимости в базе данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-the-dependencies-of-a-table"></a>Просмотр зависимостей таблицы  
  
1.  В **Обозревателе объектов**разверните узел **Базы данных**, разверните саму базу данных, а затем разверните узел **Таблицы**.  
  
2.  Щелкните таблицу правой кнопкой мыши и выберите **Просмотр зависимостей**.  
  
3.  В диалоговом окне **Зависимости объектов***\<имя объекта>* выберите либо **Объекты, зависящие от** *\<имя объекта>*, либо **Объекты, от которых зависит***\<имя объекта>*****.  
  
4.  Выберите объект в сетке **Зависимости** . Тип объекта (например, "Триггер" или "Хранимая процедура") появится в поле **Тип** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-the-objects-that-depend-on-a-table"></a>Просмотр объектов, зависящих от таблицы  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');   
    GO  
  
    ```  
  
#### <a name="to-view-the-objects-on-which-a-table-depends"></a>Просмотр объектов, от которых зависит таблица  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Следующий пример возвращает объекты, которые зависят от таблицы `Production.Product`. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referenced_id = OBJECT_ID(N'Production.Product');   
    GO  
  
    ```  
  
 Дополнительные сведения см. в разделе [sys.sql_expression_dependencies (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
