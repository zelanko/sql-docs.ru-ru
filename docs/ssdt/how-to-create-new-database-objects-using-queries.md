---
title: создать объекты базы данных с помощью запросов
description: Ознакомьтесь с редактором Transact-SQL. Узнайте, как открывать его, и просмотрите примеры, в которых демонстрируется его использование для создания таблицы, функции или представления.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: ac983ac7-f9c4-495d-8a99-e1ba370fb271
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: df5dc9a0af721e8582ec7f9095efe73d03af2710
ms.sourcegitcommit: b860fe41b873977649dca8c1fd5619f294c37a58
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2020
ms.locfileid: "85518774"
---
# <a name="how-to-create-new-database-objects-using-queries"></a>Руководство. создать объекты базы данных с помощью запросов

Если вы предпочитаете использовать скрипты для создания или изменения представлений, хранимых процедур, функций, триггеров и определяемых пользователем типов, то для этого можно пользоваться редактором Transact\-SQL. Редактор Transact\-SQL поддерживает технологии IntelliSense и другие языки. Дополнительные сведения см. в статье [Использование редактора Transact-SQL для изменения и выполнения скриптов](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md).  
  
Редактор Transact\-SQL вызывается, когда через контекстное меню **Просмотр кода** вы открываете любую сущность базы данных в подключенной базе данных или проекте. Кроме того, он автоматически открывается при использовании контекстного меню **Создать запрос** в окне обозревателя объектов SQL Server или при добавлении нового объекта скрипта в проект базы данных. Если подключение к базе данных не установлено, но нужно выполнить к ней запрос, можно воспользоваться диалоговым окном **Создать подключение для запроса**, выбрав пункт **Редактор Transact-SQL** в меню **SQL** для подключения к базе данных и запуска редактора Transact\-SQL.  
  
> [!WARNING]  
> В следующих процедурах используются сущности, созданные ранее с помощью руководства по [разработке подключенной базы данных](../ssdt/connected-database-development.md).  
  
### <a name="to-create-a-new-table-using-a-transact-sql-query"></a>Создание таблицы с помощью запроса Transact\-SQL  
  
1.  Щелкните правой кнопкой мыши узел базы данных **Trade** и выберите **Создать запрос**.  
  
2.  Вставьте следующий код в области скрипта:  
  
    ```  
  
    CREATE TABLE [dbo].[Fruits] (  
        [Id]         INT NOT NULL,  
        [Perishable] BIT DEFAULT ((1)) NULL,  
        PRIMARY KEY CLUSTERED ([Id] ASC),  
        FOREIGN KEY ([Id]) REFERENCES [dbo].[Products] ([Id])   
    );  
    ```  
  
3.  Нажмите кнопку **Выполнить запрос** на панели инструментов в редакторе Transact\-SQL, чтобы выполнить этот запрос.  
  
4.  Щелкните правой кнопкой мыши базу данных **Trade** в **обозревателе объектов SQL Server** и выберите пункт **Обновить**. Обратите внимание, что в базу данных добавлена новая таблица **Fruits**.  
  
### <a name="to-create-a-new-function"></a>Создание новой функции  
  
1.  Замените код в текущем окне редактора Transact\-SQL приведенным ниже кодом.  
  
    ```  
  
    CREATE FUNCTION [dbo].GetProductsBySupplier  
    (  
    @SupplierId int  
    )  
    RETURNS @returntable TABLE   
    (  
    [Id] int NOT NULL,   
    [Name] NVARCHAR (128) NOT NULL,  
    [Shelflife] INT NOT NULL,  
    [SupplierId] INT NOT NULL,  
    [CustomerId] INT NOT NULL  
    )  
    AS  
    BEGIN  
    INSERT @returntable  
    SELECT *  from Products p  
    where p.SupplierId = @SupplierId  
    RETURN   
    END  
    ```  
  
    Эта функция возвращает все строки в таблице `Products`, параметр которой `SupplierId` равен указанному параметру. Нажмите кнопку **Выполнить запрос** на панели инструментов в редакторе Transact\-SQL, чтобы выполнить этот запрос.  
  
2.  В окне обозревателя объектов SQL Server в узле **Trade** разверните узлы **Программирование** и **Функции**. Только что созданную функцию можно найти в разделе **Функции с табличным значением**.  
  
### <a name="to-create-a-new-view"></a>Создание нового представления  
  
1.  Замените код в текущем окне редактора Transact\-SQL приведенным ниже кодом. Затем нажмите кнопку **Выполнить запрос** над редактором, чтобы выполнить этот запрос.  
  
    ```  
    CREATE VIEW [dbo].PerishableFruits   
    AS SELECT p.Id, p.Name FROM dbo.Products p  
    join dbo.Fruits f on f.Id = p.Id  
    where f.Perishable = 1  
    ```  
  
2.  В окне обозревателя объектов SQL Server в узле **Trade** разверните узел **Представление**, чтобы найти только что созданное представление.  
  
## <a name="see-also"></a>См. также:  
[Управление таблицами и связями, а также исправление ошибок](../ssdt/manage-tables-relationships-and-fix-errors.md)  
[Использование редактора Transact-SQL для изменения и выполнения скриптов](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md)  
  
