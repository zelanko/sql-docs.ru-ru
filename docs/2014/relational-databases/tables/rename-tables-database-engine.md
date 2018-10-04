---
title: Переименование таблиц (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
ms.assetid: 2f5c922d-4d71-4694-9fca-28dd99375799
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0ea78b3891b3622d98711495814b0029272a5605
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48098194"
---
# <a name="rename-tables-database-engine"></a>Переименование таблиц (компонент Database Engine)
  Таблицу в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно переименовать, используя [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!CAUTION]  
>  Каждое переименование таблицы следует тщательно планировать. Если существующие запросы, представления, определяемые пользователем функции, хранимые процедуры или программы ссылаются на таблицу, изменение имени таблицы сделает эти объекты недействительными.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Переименование таблицы с использованием:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 Переименование таблицы не приводит к автоматическому переименованию ссылок на эту таблицу. Необходимо вручную изменить все объекты, которые ссылаются на переименованную таблицу. Например, если переименована таблица и на эту таблицу имеется ссылка в триггере, то необходимо изменить триггер, указав новое имя таблицы. Используйте представление каталога [sys.sql_expression_dependencies](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql) , чтобы составить список зависимостей для таблицы перед переименованием.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-a-table"></a>Переименование таблицы  
  
1.  В обозревателе объектов правой кнопкой мыши щелкните таблицу, имя которой хотите переименовать, и в контекстном меню выберите пункт **Конструирование** .  
  
2.  В меню **Просмотр** выберите команду **Свойства**.  
  
3.  В поле **Имя** окна **Свойства** введите новое имя таблицы.  
  
4.  Чтобы отменить это действие, нажмите клавишу ESC перед тем, как выйти из этого поля.  
  
5.  В меню **Файл** выберите команду *Сохранить***имя_таблицы*.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-rename-a-table"></a>Переименование таблицы  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  В следующем примере столбец `SalesTerritory` в таблице `SalesTerr` переименовывается в `Sales` . Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 Дополнительные примеры см. в статье [sp_rename (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).  
  
  
