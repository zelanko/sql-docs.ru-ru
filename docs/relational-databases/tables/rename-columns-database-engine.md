---
title: "Переименование столбцов (ядро СУБД) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [SQL Server], names
- renaming columns
- column names [SQL Server]
ms.assetid: 7c71ec9f-0180-4398-b32a-4bfb7592e75d
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e02a5d26a0a04d5afa1c4ddfcc9c06c503b6bd2c
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="rename-columns-database-engine"></a>Переименование столбцов (компонент Database Engine)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Столбец таблицы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно переименовать, используя [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Переименование столбцов с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
 Переименование столбца таблицы не приводит к автоматическому переименованию ссылок на этот столбец. Необходимо вручную изменить все объекты, которые ссылаются на переименованный столбец. Например, если переименован столбец таблицы и на этот столбец имеется ссылка в триггере, то необходимо изменить триггер, указав новое имя столбца. Используйте [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) , чтобы составить список зависимостей для объекта перед его переименованием.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение ALTER на объект.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-rename-a-column-using-object-explorer"></a>Переименование столбца в обозревателе объектов  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  В **обозревателе объектов**щелкните правой кнопкой мыши таблицу, в которой нужно переименовать столбцы, и выберите пункт **Переименовать**.  
  
3.  Введите новое имя столбца.  
  
#### <a name="to-rename-a-column-using-table-designer"></a>Переименование столбца в конструкторе таблиц  
  
1.  В **обозревателе объектов**щелкните правой кнопкой мыши таблицу, в которой нужно переименовать столбцы, и выберите пункт **Конструирование**.  
  
2.  В разделе **Имя столбца**выберите имя, которое нужно изменить, и введите новое.  
  
3.  В меню **Файл** выберите пункт **Сохранить***table name*.  
  
> [!NOTE]  
>  Имя столбца можно также изменить на вкладке **Свойства столбца** . Выберите столбец, имя которого нужно изменить, и введите новое значение в поле **Имя**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Переименование столбца**  
  
#### <a name="to-rename-a-column"></a>Переименование столбца  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  В следующем примере столбец `TerritoryID` в таблице `Sales.SalesTerritory` переименовывается в `TerrID`. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename 'Sales.SalesTerritory.TerritoryID', 'TerrID', 'COLUMN';  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [sp_rename (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md).  
  
  
