---
title: Создание и запуск модульного теста SQL Server
description: Узнайте, как создать модульный тест SQL Server. Выполните пошаговые инструкции по настройке теста, который обнаруживает ошибку в хранимой процедуре.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 992c1d8e-3729-438b-9ef4-cd103e28f145
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: edc5f591746673f55dfc7ea10c99822ee0c13098
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882918"
---
# <a name="walkthrough-creating-and-running-a-sql-server-unit-test"></a>Пошаговое руководство. Создание и запуск модульного теста SQL Server

С помощью этого пошагового руководства вы создадите модульный тест создать, который проверяет работу нескольких хранимых процедур. Модульные тесты SQL Server создаются для выявления ошибок кода, которые могут вызвать неверную работу приложения. Модульные тесты SQL Server и тесты приложений можно запускать в одном автоматизированном наборе тестов.  
  
В этом пошаговом руководстве будут выполнены следующие задачи:  
  
-   [создание скрипта со схемой базы данных](#CreateScript);  
  
-   [создание проекта базы данных и импорт этой схемы базы данных](#CreateProjectAndImport);  
  
-   [развертывание проекта базы данных в автономной среде разработки](#DeployDBProj);  
  
-   [создание модульных тестов SQL Server](#CreateDBUnitTests);  
  
-   [определение логики теста](#DefineTestLogic);  
  
-   [выполнение модульных тестов SQL Server](#RunTests);  
  
-   [добавление отрицательного модульного теста](#NegativeTest).  
  
После того как один из модульных тестов выявит ошибку в хранимой процедуре, вы исправите эту ошибку и повторить тест.  
  
## <a name="prerequisites"></a>Предварительные требования  
Чтобы выполнить это пошаговое руководство, потребуется соединение с сервером базы данных (или базой данных LocalDB), на котором у вас есть разрешения на создание и развертывание базы данных. Дополнительные сведения см. в статье [Обязательные разрешения для функций работы с базами данных Visual Studio](https://msdn.microsoft.com/library/aa833413(VS.100).aspx).  
  
## <a name="create-a-script-that-contains-a-database-schema"></a><a name="CreateScript"></a>Создание скрипта со схемой базы данных  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Создание скрипта, из которого можно импортировать схему  
  
1.  В меню **Файл** укажите пункт **Создать**, а затем выберите пункт **Файл**.  
  
    Откроется диалоговое окно **Создание файла** .  
  
2.  В списке **Категории** щелкните **Общие** , если эта категория еще не выделена.  
  
3.  В списке **Шаблоны** щелкните **Sql-файл**и затем **Открыть**.  
  
    Откроется редактор Transact\-SQL.  
  
4.  Скопируйте следующие Transact\-SQL код и вставьте его в редактор Transact\-SQL.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2030'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2030'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40)  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    RETURN SCOPE_IDENTITY()  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  Сохраните файл. Запомните расположение, поскольку этот скрипт нужно будет использовать на следующем шаге.  
  
6.  В меню **Файл** выберите пункт **Закрыть решение**.  
  
    Далее нужно создать проект базы данных и импортировать схему из созданного скрипта.  
  
## <a name="create-a-database-project-and-import-a-schema"></a><a name="CreateProjectAndImport"></a>Создание проекта базы данных и импорт схемы  
  
#### <a name="to-create-a-database-project"></a>Создание проекта базы данных  
  
1.  В меню **Файл** укажите пункт **Создать**, затем выберите пункт **Проект**.  
  
    Откроется диалоговое окно **Создание проекта** .  
  
2.  В области **Установленные шаблоны** выберите узел **SQL Server**, а затем **Проект базы данных SQL Server**.  
  
3.  В поле **Имя**введите **SimpleUnitTestDB**.  
  
4.  Установите флажок **Создать каталог для решения** , если он еще не установлен.  
  
5.  Снимите флажок **Добавить к системе управления версиями** , если он еще не снят, затем нажмите кнопку **ОК**.  
  
    Проект базы данных будет создан и отображен в **обозревателе решений**. Далее нужно импортировать схему базы данных из скрипта.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>Импорт схемы базы данных из скрипта  
  
1.  Выберите **Импорт** в меню **Проект**, и щелкните **Скрипт (\*.sql)** .  
  
2.  На странице приветствия нажмите кнопку **Далее** .  
  
3.  Нажмите кнопку **Обзор**и перейдите в каталог, в который вы сохранили SQL-файл.  
  
4.  Дважды щелкните SQL-файл и нажмите кнопку **Готово**.  
  
    Скрипт будет импортирован, а объекты, определенные в скрипте, будут добавлены в проект базы данных.  
  
5.  Просмотрите сводные данные и нажмите кнопку **Готово** , чтобы завершить операцию.  
  
    > [!NOTE]  
    > Процедура Sales.uspFillOrder содержит преднамеренную ошибку кода, которая будет выявлена и исправлена на следующем этапе.  
  
#### <a name="to-examine-the-resulting-project"></a>Просмотр итогового проекта  
  
1.  В **обозревателе решений**изучите файлы скриптов, которые были импортированы в проект.  
  
2.  В **обозревателе объектов SQL Server** найдите базу данных в узле "Проекты".  
  
## <a name="deploying-to-localdb"></a><a name="DeployDBProj"></a>Развертывание в LocalDB  
По умолчанию при нажатии клавиши F5 выполняется развертывание (или публикация) базы данных в базу данных LocalDB. Расположение базы данных можно изменить, перейдя на вкладку «Отладка» страницы свойств проекта и изменив строку подключения.  
  
## <a name="create-sql-server-unit-tests"></a><a name="CreateDBUnitTests"></a>Создание модульных тестов SQL Server  
  
#### <a name="to-create-a-sql-server-unit-test-for-the-stored-procedures"></a>Создание модульного теста SQL Server для хранимых процедур  
  
1.  В **обозревателе объектов SQL Server** разверните узел проектов **SimpleUnitTestDB**, а затем по очереди разверните узлы **Программирование** и **Хранимые процедуры**.  
  
2.  Щелкните одну из хранимых процедур правой кнопкой мыши и выберите команду **Создать модульные тесты**, чтобы открыть диалоговое окно **Создание модульных тестов**.  
  
3.  Установите флажки для всех пяти хранимых процедур: **Sales.uspCancelOrder**, **Sales.uspFillOrder**, **Sales.uspNewCustomer**, **Sales.uspPlaceNewOrder**и **Sales.uspShowOrderDetails**.  
  
4.  В раскрывающемся списке **Проект** выберите **Создать тестовый проект Visual C#** .  
  
5.  Примите заданные по умолчанию имена в качестве имени проекта и имени класса и нажмите кнопку **ОК**.  
  
6.  В поле **Выполнить модульные тесты, используя следующее подключение к данным**диалогового окна конфигурации теста укажите подключение к базе данных, развернутой на предыдущих этапах в данном пошаговом руководстве. Например, если использовалось расположение для развертывания по умолчанию, то есть база данных LocalDB, щелкните **Создать соединение** и укажите **(LocalDB)\Projects**. Затем выберите имя базы данных. Далее нажмите кнопку «ОК», чтобы закрыть диалоговое окно **Свойства соединения** .  
  
    > [!NOTE]  
    > Если требуется протестировать представления или хранимые процедуры с ограниченными разрешениями, обычно на этом шаге нужно указать соединение. После этого нужно указать дополнительное соединение с более широкими разрешениями для проверки теста. Если дополнительное соединение задано, нужно добавить этого пользователя в проект базы данных и создать имя входа для этого пользователя в скрипте, выполняемом перед развертыванием.  
  
7.  В диалоговом окне конфигурации теста в разделе **Развертывание** установите флажок **Автоматически развертывать проект базы данных перед выполнением модульных тестов** .  
  
8.  В меню **Проект базы данных**щелкните **SimpleUnitTestDB.sqlproj**.  
  
9. В разделе **Конфигурация развертывания**щелкните **Отладка**.  
  
    Для модульных тестов SQL Server также можно создать тестовые данные. Для этого пошагового руководства этот этап будет пропущен, так как тесты создадут собственные данные.  
  
10. Нажмите кнопку **ОК**.  
  
    Будет выполнена сборка тестового проекта, а затем откроется конструктор модульных тестов SQL Server. После этого вам нужно изменить логику тестов в скрипте Transact\-SQL для модульных тестов.  
  
## <a name="define-test-logic"></a><a name="DefineTestLogic"></a>Определение логики теста  
В этой очень простой базе данных есть две таблицы — Customer и Order. Нужно обновить базу данных с помощью следующих хранимых процедур.  
  
-   uspNewCustomer — эта хранимая процедура добавляет запись в таблицу Customer, которая задает нулевые значения для столбцов YTDOrders и YTDSales.  
  
-   uspPlaceNewOrder — эта хранимая процедура добавляет запись в таблицу Orders для указанного заказчика и обновляет значение YTDOrders соответствующей записи в таблице Customer.  
  
-   uspFillOrder — эта хранимая процедура обновляет запись в таблице Orders путем изменения состояния с «О» на «F» и увеличивает сумму YTDSales для соответствующей записи в таблице Customer.  
  
-   uspCancelOrder — эта хранимая процедура обновляет запись в таблице Orders путем изменения состояния с «О» на «X» и уменьшает сумму YTDOrders для соответствующей записи в таблице Customer.  
  
-   uspShowOrderDetails — эта хранимая процедура объединяет таблицу Orders с таблицей Custom и выводит записи для определенного заказчика.  
  
> [!NOTE]  
> В этом примере показано, как создать простой модульный тест SQL Server. В реальной базе данных можно было бы суммировать все заказы со статусом «O» или «F» для определенного заказчика. В примерах из этого пошагового руководства не описывается обработка ошибок. Например, предлагаемый код не предотвращает вызов процедуры uspFillOrder для заказа, который уже был заполнен.  
  
Предполагается, что база данных в тестах начинает работу в чистом состоянии. Необходимо создать тесты, которые будут проверять следующие условия.  
  
-   uspNewCustomer — проверяет, чтобы таблица Customer содержала одну строку после запуска хранимой процедуры.  
  
-   uspPlaceNewOrder — для заказчика, у которого поле CustomerID имеет значение 1, размещает заказ на 100 долларов. Убедитесь, что сумма YTDOrders для этого заказчика равна 100, а сумма YTDSales — нулю.  
  
-   uspFillOrder — для заказчика, у которого поле CustomerID имеет значение 1, размещает заказ на 50 долларов. Заполните этот заказ. Убедитесь, что суммы YTDOrders и YTDSales обе равны 50.  
  
-   uspShowOrderDetails — для заказчика, у которого поле CustomerID имеет значение 1, размещает заказы на 100, 50 и 5 долларов. Убедитесь, что uspShowOrderDetails возвращает нужное число столбцов и что результирующий набор имеет ожидаемую контрольную сумму.  
  
> [!NOTE]  
> При выполнении полного набора модульных тестов SQL Server нужно убедиться, что остальные столбцы имеют допустимые значения. В целях упрощения этого пошагового руководства оно не содержит проверку работы хранимой процедуры uspCancelOrder.  
  
#### <a name="to-write-the-sql-server-unit-test-for-uspnewcustomer"></a>Создание модульного теста SQL Server для хранимой процедуры uspNewCustomer  
  
1.  На панели навигации в конструкторе модульных тестов SQL Server щелкните **Sales_uspNewCustomerTest** и убедитесь, что в соседнем списке выделен пункт **Тест**.  
  
    После выполнения первого шага можно создавать скрипт теста для тестового действия, выполняемого в рамках модульного теста.  
  
2.  Обновите инструкции Transact\-SQL в редакторе Transact\-SQL так, чтобы они совпадали со следующими инструкциями:  
  
    ```  
    -- ssNoVersion unit test for Sales.uspNewCustomer  
    DECLARE @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @CustomerName = 'Fictitious Customer';  
  
    EXECUTE @RC = [Sales].[uspNewCustomer] @CustomerName;  
  
    SELECT * FROM [Sales].[Customer];  
    ```  
  
3.  На панели **Условия теста** щелкните условие теста "С неопределенным результатом", а затем щелкните красный крестик, чтобы **удалить условие теста**.  
  
4.  На панели **Условия теста** щелкните в списке **Число строк**, а затем щелкните зеленый знак плюса, чтобы **добавить условие теста**.  
  
5.  Откройте окно **Свойства** (выберите условие теста и нажмите клавишу F4) и задайте свойству **Число строк** значение 1.  
  
6.  В меню **Файл** выберите команду **Сохранить все**.  
  
    Далее нужно определить логику модульного теста для хранимой процедуры uspPlaceNewOrder.  
  
#### <a name="to-write-the-sql-server-unit-test-for-uspplaceneworder"></a>Создание модульного теста SQL Server для хранимой процедуры uspPlaceNewOrder  
  
1.  На панели навигации в конструкторе модульных тестов SQL Server щелкните **Sales_uspPlaceNewOrderTest** и убедитесь, что в соседнем списке выделен пункт **Тест**.  
  
    После выполнения этого шага можно создавать скрипт теста для тестового действия, выполняемого в рамках модульного теста.  
  
2.  Обновите инструкции Transact\-SQL в редакторе Transact\-SQL так, чтобы они совпадали со следующими инструкциями:  
  
    ```  
    -- ssNoVersion unit test for Sales.uspPlaceNewOrder  
    DECLARE @RC AS INT, @CustomerID AS INT, @Amount AS INT, @OrderDate AS DATETIME, @Status AS CHAR (1);  
    DECLARE @CustomerName AS NVARCHAR(40);  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @OrderDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- place an order for that customer  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, @Amount, @OrderDate, @Status;  
  
    -- verify that the YTDOrders value is correct.  
    SELECT @RC = [YTDOrders] FROM [Sales].[Customer] WHERE [CustomerID] = @CustomerID  
  
    SELECT @RC AS RC  
    ```  
  
3.  На панели **Условия теста** щелкните условие теста «С неопределенным результатом», а затем щелкните команду **Удалить условие теста**.  
  
4.  На панели **Условия теста** щелкните в списке пункт **Скалярное значение** , а затем щелкните команду **Добавить условие теста**.  
  
5.  В окне **Свойства** для свойства **Ожидаемое значение** установите значение 100.  
  
6.  На панели навигации в конструкторе модульных тестов SQL Server щелкните **Sales_uspPlaceNewOrderTest** и убедитесь, что в соседнем списке выделен пункт **Перед тестом**.  
  
    После выполнения этого шага можно указать инструкции, которые переведут данные в состояние, необходимое для выполнения теста. В этом примере, прежде чем размещать заказ, необходимо создать запись Customer.  
  
7.  Щелкните **Щелкните здесь, чтобы создать**, чтобы создать выполняемый перед тестом скрипт.  
  
8.  Обновите инструкции Transact\-SQL в редакторе Transact\-SQL так, чтобы они совпадали со следующими инструкциями:  
  
    ```  
    /*  
    Add Transact-SQL statements here that you want to run before  
    the test script is run.  
    */  
    -- Add a customer for this test with the name 'Fictitious Customer'  
    DECLARE @NewCustomerID AS INT, @CustomerID AS INT, @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @NewCustomerID = 0,  
       @CustomerID = 0,  
           @CustomerName = N'Fictitious Customer';  
  
    IF NOT EXISTS(SELECT * FROM [Sales].[Customer] WHERE CustomerName = @CustomerName)  
    BEGIN  
    EXECUTE @NewCustomerID = [Sales].[uspNewCustomer] @CustomerName;  
    END  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- delete any old records in the Orders table and clear out the YTD Sales/Orders fields  
    DELETE from [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
    UPDATE [Sales].[Customer] SET YTDOrders = 0, YTDSales = 0 WHERE [CustomerID] = @CustomerID;  
    ```  
  
9. В меню **Файл** выберите команду **Сохранить все**.  
  
    Далее нужно создать модульный тест для хранимой процедуры uspFillOrder.  
  
#### <a name="to-write-the-sql-server-unit-test-for-uspfillorder"></a>Создание модульного теста SQL Server для хранимой процедуры uspFillOrder  
  
1.  На панели навигации в конструкторе модульных тестов SQL Server щелкните **Sales_uspFillOrderTest** и убедитесь, что в соседнем списке выделен пункт **Тест**.  
  
    После выполнения этого шага можно создавать скрипт теста для тестового действия, выполняемого в рамках модульного теста.  
  
2.  Обновите инструкции Transact\-SQL в редакторе Transact\-SQL так, чтобы они совпадали со следующими инструкциями:  
  
    ```  
    -- ssNoVersion unit test for Sales.uspFillOrder  
    DECLARE @RC AS INT, @CustomerID AS INT, @Amount AS INT, @FilledDate AS DATETIME, @Status AS CHAR (1);  
    DECLARE @CustomerName AS NVARCHAR(40), @OrderID AS INT;  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @OrderID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @FilledDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
    -- Get the most recently added order.  
    SELECT @OrderID = MAX([OrderID]) FROM [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
  
    -- fill an order for that customer  
    EXECUTE @RC = [Sales].[uspFillOrder] @OrderID, @FilledDate;  
  
    -- verify that the YTDOrders value is correct.  
    SELECT @RC = [YTDSales] FROM [Sales].[Customer] WHERE [CustomerID] = @CustomerID  
  
    SELECT @RC AS RC;  
    ```  
  
3.  На панели **Условия теста** щелкните условие теста «С неопределенным результатом», а затем щелкните команду **Удалить условие теста**.  
  
4.  На панели **Условия теста** щелкните в списке пункт **Скалярное значение** , а затем щелкните команду **Добавить условие теста**.  
  
5.  В окне **Свойства** для свойства **Ожидаемое значение** установите значение 100.  
  
6.  На панели навигации в конструкторе модульных тестов SQL Server щелкните **Sales_uspFillOrderTest** и убедитесь, что в соседнем списке выделен пункт **Перед тестом**. После выполнения этого шага можно указать инструкции, которые переведут данные в состояние, необходимое для выполнения теста. В этом примере, прежде чем размещать заказ, необходимо создать запись Customer.  
  
7.  Щелкните **Щелкните здесь, чтобы создать**, чтобы создать выполняемый перед тестом скрипт.  
  
8.  Обновите инструкции Transact\-SQL в редакторе Transact\-SQL так, чтобы они совпадали со следующими инструкциями:  
  
    ```  
    /*  
    Add Transact-SQL statements here that you want to run before  
    the test script is run.  
    */  
    BEGIN TRANSACTION  
  
    -- Add a customer for this test with the name 'CustomerB'  
    DECLARE @NewCustomerID AS INT, @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @NewCustomerID = 0,  
           @CustomerName = N'Fictitious Customer';  
  
    IF NOT EXISTS(SELECT * FROM [Sales].[Customer] WHERE CustomerName = @CustomerName)  
    BEGIN  
    EXECUTE @NewCustomerID = [Sales].[uspNewCustomer] @CustomerName;  
    END  
  
    DECLARE @CustomerID AS INT, @Amount AS INT, @OrderDate AS DATETIME, @Status AS CHAR (1);  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @OrderDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- delete any old records in the Orders table and clear out the YTD Sales/Orders fields  
    DELETE from [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
    UPDATE [Sales].[Customer] SET YTDOrders = 0, YTDSales = 0 WHERE [CustomerID] = @CustomerID;  
  
    -- place an order for that customer  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, @Amount, @OrderDate, @Status;  
  
    COMMIT TRANSACTION  
    ```  
  
9. В меню **Файл** выберите команду **Сохранить все**.  
  
#### <a name="to-write-the-sql-server-unit-test-for-uspshoworderdetails"></a>Создание модульного теста SQL Server для хранимой процедуры uspShowOrderDetails  
  
1.  На панели навигации в конструкторе модульных тестов SQL Server щелкните **Sales_uspShowOrderDetailsTest** и убедитесь, что в соседнем списке выделен пункт **Тест**.  
  
    После выполнения этого шага можно создавать скрипт теста для тестового действия, выполняемого в рамках модульного теста.  
  
2.  Обновите инструкции Transact\-SQL в редакторе Transact\-SQL так, чтобы они совпадали со следующими инструкциями:  
  
    ```  
    -- ssNoVersion unit test for Sales.uspFillOrder  
    DECLARE @RC AS INT, @CustomerID AS INT, @Amount AS INT, @FilledDate AS DATETIME, @Status AS CHAR (1);  
    DECLARE @CustomerName AS NVARCHAR(40), @OrderID AS INT;  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @OrderID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @FilledDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- fill an order for that customer  
    EXECUTE @RC = [Sales].[uspShowOrderDetails] @CustomerID;  
  
    SELECT @RC AS RC;  
    ```  
  
3.  На панели **Условия теста** щелкните условие теста «С неопределенным результатом», а затем щелкните команду **Удалить условие теста**.  
  
4.  На панели **Условия теста** щелкните в списке пункт **Ожидаемая схема** и затем щелкните команду **Добавить условие теста**.  
  
5.  В окне **Свойства** напротив свойства **Конфигурация** нажмите кнопку обзора ( **…** ).  
  
6.  В диалоговом окне **Конфигурация для условия expectedSchemaCondition1** укажите соединение с базой данных. Например, если использовалось расположение для развертывания по умолчанию, то есть база данных LocalDB, щелкните **Создать соединение** и укажите **(LocalDB)\Projects**. Затем выберите имя базы данных.  
  
7.  Нажмите **Получить**. (При необходимости щелкайте **Получить** до тех пор, пока не увидите данные.)  
  
    Будет выполнен блок Transact\-SQL модульного теста, после чего в диалоговом окне появится итоговая схема. Поскольку код скрипта, запускаемого перед тестом, не был выполнен, данные не возвращаются. Это нормально, поскольку на этом этапе выполняется проверка схемы, а не данных.  
  
8.  Нажмите кнопку **ОК**.  
  
    Ожидаемая схема сохраняется в условии теста.  
  
9. На панели навигации в конструкторе модульных тестов SQL Server щелкните **Sales_uspShowOrderDetailsTest** и убедитесь, что в соседнем списке выделен пункт **Перед тестом**. После выполнения этого шага можно указать инструкции, которые переведут данные в состояние, необходимое для выполнения теста. В этом примере, прежде чем размещать заказ, необходимо создать запись Customer.  
  
10. Щелкните **Щелкните здесь, чтобы создать**, чтобы создать выполняемый перед тестом скрипт.  
  
11. Обновите инструкции Transact\-SQL в редакторе Transact\-SQL так, чтобы они совпадали со следующими инструкциями:  
  
    ```  
    /*  
    Add Transact-SQL statements here to run before the test script is run.  
    */  
    BEGIN TRANSACTION  
  
    -- Add a customer for this test with the name 'FictitiousCustomer'  
    DECLARE @NewCustomerID AS INT, @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @NewCustomerID = 0,  
           @CustomerName = N'Fictitious Customer';  
  
    IF NOT EXISTS(SELECT * FROM [Sales].[Customer] WHERE CustomerName = @CustomerName)  
    BEGIN  
    EXECUTE @NewCustomerID = [Sales].[uspNewCustomer] @CustomerName;  
    END  
  
    DECLARE @CustomerID AS INT, @Amount AS INT, @OrderDate AS DATETIME, @Status AS CHAR (1);  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @OrderDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- delete any old records in the Orders table and clear out the YTD Sales/Orders fields  
    DELETE from [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
    UPDATE [Sales].[Customer] SET YTDOrders = 0, YTDSales = 0 WHERE [CustomerID] = @CustomerID;  
  
    -- place 3 orders for that customer  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 100, @OrderDate, @Status;  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 50, @OrderDate, @Status;  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 5, @OrderDate, @Status;  
  
    COMMIT TRANSACTION  
    ```  
  
12. На панели навигации в конструкторе модульных тестов SQL Server щелкните **Sales_uspShowOrderDetailsTest** и щелкните пункт **Тест** в соседнем списке.  
  
    Это необходимо сделать, чтобы применить условие контрольной суммы к тесту, а не к действию, выполняемому перед тестом.  
  
13. На панели **Условия теста** щелкните в списке пункт **Контрольная сумма данных** , а затем **Добавить условие теста**.  
  
14. В окне **Свойства** напротив свойства **Конфигурация** нажмите кнопку обзора ( **…** ).  
  
15. В диалоговом окне **Конфигурация для условия checksumCondition1** укажите соединение с базой данных.  
  
16. Замените код Transact\-SQL в этом диалоговом окне (под кнопкой **Изменить соединение**) следующим кодом:  
  
    ```  
    BEGIN TRANSACTION  
  
    -- Add a customer for this test with the name 'CustomerB'  
    DECLARE @NewCustomerID AS INT, @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @NewCustomerID = 0,  
           @CustomerName = N'Fictitious Customer';  
  
    IF NOT EXISTS(SELECT * FROM [Sales].[Customer] WHERE CustomerName = @CustomerName)  
    BEGIN  
    EXECUTE @NewCustomerID = [Sales].[uspNewCustomer] @CustomerName;  
    END  
  
    DECLARE @CustomerID AS INT, @Amount AS INT, @OrderDate AS DATETIME, @Status AS CHAR (1);  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @OrderDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- delete any old records in the Orders table and clear out the YTD Sales/Orders fields  
    DELETE from [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
    UPDATE [Sales].[Customer] SET YTDOrders = 0, YTDSales = 0 WHERE [CustomerID] = @CustomerID;  
  
    -- place 3 orders for that customer  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 100, @OrderDate, @Status;  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 50, @OrderDate, @Status;  
    EXECUTE @RC = [Sales].[uspPlaceNewOrder] @CustomerID, 5, @OrderDate, @Status;  
  
    COMMIT TRANSACTION  
  
    -- ssNoVersion unit test for Sales.uspFillOrder  
    DECLARE @FilledDate AS DATETIME;  
    DECLARE @OrderID AS INT;  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @OrderID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @FilledDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- fill an order for that customer  
    EXECUTE @RC = [Sales].[uspShowOrderDetails] @CustomerID;  
  
    SELECT @RC AS RC;  
    ```  
  
    Этот код объединяет код Transact\-SQL из скрипта, выполняемого перед тестом, с кодом Transact\-SQL самого теста. Нужны оба кода, чтобы получить те же результаты, которые будут получены при запуске теста.  
  
17. Нажмите **Получить**. (При необходимости щелкайте **Получить** до тех пор, пока не увидите данные.)  
  
    Будет выполнен указанный код Transact\-SQL с последующим выполнением контрольной суммы для полученных данных.  
  
18. Нажмите кнопку **ОК**.  
  
    Вычисленная контрольная сумма сохраняется в условии теста. Ожидаемая контрольная сумма появляется в столбце Value условия теста «Контрольная сумма данных».  
  
19. В меню **Файл** выберите команду **Сохранить все**.  
  
    Теперь все готово для запуска тестов.  
  
## <a name="run-sql-server-unit-tests"></a><a name="RunTests"></a>Выполнение модульных тестов SQL Server  
  
#### <a name="to-run-the-sql-server-unit-tests"></a>Чтобы выполнить модульные тесты SQL Server, сделайте следующее:  
  
1.  В меню **Тест** выберите **Окна**, а затем щелкните **Представление теста** (в Visual Studio 2010) или **Обозреватель тестов** (Visual Studio 2012).  
  
2.  В окне **Представление теста** (Visual Studio 2010) нажмите кнопку **Обновить** на панели инструментов, чтобы обновить список тестов. Чтобы отобразить список тестов в **обозревателе тестов** (Visual Studio 2012), выполните сборку решения.  
  
    В окне **Представление теста** или в **обозревателе тестов** содержится список тестов, которые были созданы на предыдущих этапах этого пошагового руководства и в которые были добавлены инструкции Transact\-SQL и условия теста. Тест с именем TestMethod1 пустой и не используется в этом пошаговом руководстве.  
  
3.  Щелкните правой кнопкой мыши **Sales_uspNewCustomerTest** и выберите команду **Выполнить выбранное**.  
  
    Visual Studio воспользуется привилегированным контекстом, который вы указали для подключения к базе данных, и применит план создания данных. Затем Visual Studio переключится в контекст выполнения перед выполнением скрипта Transact\-SQL в тесте. Наконец, Visual Studio проанализирует результаты выполнения скрипта Transact\-SQL с учетом параметров, указанных в условии теста, после чего в окне **Результаты теста** появится результат, информирующий о прохождении или непрохождении теста.  
  
4.  Просмотрите результаты в окне **Результаты теста** .  
  
    «Тест пройден» означает, что инструкция **SELECT** при выполнении возвращает одну строку.  
  
5.  Повторите шаг 3 для тестов Sales_uspPlaceNewOrderTest, Sales_uspFillOrderTest и Sales_uspShowOrderDetailsTest. Результаты должны быть следующими.  
  
    |Тест|Ожидаемый результат|  
    |--------|-------------------|  
    |Sales_uspPlaceNewOrderTest|Успех|  
    |Sales_uspShowOrderDetailsTest|Успех|  
    |Sales_uspFillOrderTest|Сбой со следующей ошибкой: "Сбой условия ScalarValueCondition (scalarValueCondition2): Результирующий набор 1 Строка 1 Столбец 1: значения не соответствуют, действительное значение: –100, ожидаемое значение: 100". Эта ошибка возникает, потому что определение хранимой процедуры содержит незначительную ошибку.|  
  
    На следующем этапе ошибка будет исправлена и тест будет выполнен повторно.  
  
#### <a name="to-correct-the-error-in-salesuspfillorder"></a>Исправление ошибки в хранимой процедуре Sales.uspFillOrder  
  
1.  В **обозревателе объектов SQL Server** в узле "Проекты" для вашей базы данных дважды щелкните хранимую процедуру **uspFillOrder**, чтобы открыть ее определение в редакторе Transact\-SQL.  
  
2.  Найдите в этом определении следующую инструкцию Transact\-SQL:  
  
    ```  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales - @Delta  
        WHERE [CustomerID] = @CustomerID  
    ```  
  
3.  Измените предложение SET в инструкции так, чтобы она совпадала со следующей инструкцией.  
  
    ```  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    ```  
  
4.  В меню **Файл** выберите команду **Save uspFillOrder.sql**.  
  
5.  В окне **Представление теста** щелкните **Sales_uspFillOrderTest** правой кнопкой мыши и выберите команду **Выполнить выбранное**.  
  
    Тест будет пройден.  
  
## <a name="add-a-negative-unit-test"></a><a name="NegativeTest"></a>Добавление отрицательного модульного теста  
Чтобы убедиться, что тест выдает ошибку, когда он должен ее выдавать, можно создать отрицательный тест. Например, если попытаться отменить уже заполненный заказ, тест должен завершиться ошибкой. В этом разделе пошагового руководства будет создан отрицательный модульный тест для хранимой процедуры Sales.uspCancelOrder.  
  
Чтобы создать и проверить отрицательный тест, необходимо выполнить следующие задачи:  
  
-   обновить хранимую процедуру для проверки условий ошибок;  
  
-   определить новый модульный тест;  
  
-   изменить код модульного теста и указать, что он должен завершиться ошибкой;  
  
-   выполнить модульный тест.  
  
#### <a name="to-update-the-stored-procedure"></a>Обновление хранимой процедуры  
  
1.  В узле "Проект" для базы данных SimpleUnitTestDB в **обозревателе объектов SQL Server** поочередно откройте узлы "Программирование" и "Хранимые процедуры", затем дважды щелкните uspCancelOrder.  
  
2.  В редакторе Transact\-SQL измените определение процедуры так, чтобы она совпадала со следующим кодом:  
  
    ```  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
        DECLARE @Delta INT, @CustomerID INT, @PriorStatus CHAR(1)  
        BEGIN TRANSACTION  
            BEGIN TRY  
                IF (NOT EXISTS(SELECT [CustomerID] from [Sales].[Orders] WHERE [OrderID] = @OrderID))  
                BEGIN  
                    -- Specify WITH LOG option so that the error is  
                    -- written to the application log.  
                    RAISERROR( 'That order does not exist.', -- Message text  
                               16, -- severity  
                                1 -- state  
                            ) WITH LOG;  
                END  
  
                SELECT @Delta = [Amount], @CustomerID = [CustomerID], @PriorStatus = [Status]  
                 FROM [Sales].[Orders] WHERE [OrderID] = @OrderID  
  
                IF @PriorStatus <> 'O'   
                BEGIN  
                    -- Specify WITH LOG option so that the error is  
                    -- written to the application log.  
                    RAISERROR ( 'You can only cancel open orders.', -- Message text  
                                16, -- Severity  
                                1 -- State  
                                ) WITH LOG;  
                END  
                ELSE  
                BEGIN  
                    -- If we make it to here, then we can cancel the order. Update the status to 'X' first...  
                    UPDATE [Sales].[Orders]  
                       SET [Status] = 'X'  
                    WHERE [OrderID] = @OrderID  
                    -- and then remove the amount from the YTDOrders for the customer  
                    UPDATE [Sales].[Customer]  
                           SET  
                               YTDOrders = YTDOrders - @Delta  
                    WHERE [CustomerID] = @CustomerID  
                    COMMIT TRANSACTION  
                    RETURN 1; -- indicate success  
                END  
            END TRY  
            BEGIN CATCH  
                DECLARE @ErrorMessage NVARCHAR(4000);  
                DECLARE @ErrorSeverity INT;  
                DECLARE @ErrorState INT;  
  
                SELECT @ErrorMessage = ERROR_MESSAGE(),  
                       @ErrorSeverity = ERROR_SEVERITY(),  
                       @ErrorState = ERROR_STATE();  
  
                ROLLBACK TRANSACTION  
                -- Use RAISERROR inside the CATCH block to return  
                -- error information about the original error that  
                -- caused execution to jump to the CATCH block.  
                RAISERROR (@ErrorMessage, -- Mesasge text  
                           @ErrorSeverity, -- Severity  
                           @ErrorState -- State  
                          );  
                RETURN 0; -- indicate failure  
            END CATCH;  
    END  
    ```  
  
3.  В меню **Файл** выберите команду **Save uspCancelOrder.sql**.  
  
4.  Нажмите клавишу F5, чтобы развернуть **SimpleUnitTestDB**.  
  
    Необходимо развернуть обновления хранимой процедуры uspCancelOrder. Обновляется только хранимая процедура, другие объекты не изменяются.  
  
    Далее нужно определить связанный модульный тест для этой процедуры.  
  
#### <a name="to-write-the-sql-server-unit-test-for-uspcancelorder"></a>Чтобы создать модульный тест SQL Server для хранимой процедуры uspCancelOrder, сделайте следующее:  
  
1.  На панели навигации в конструкторе модульных тестов SQL Server щелкните **Sales_uspCancelOrderTest** и убедитесь, что в соседнем списке выделен пункт **Тест**.  
  
    После выполнения этого шага можно создавать скрипт теста для тестового действия, выполняемого в рамках модульного теста.  
  
2.  Обновите инструкции Transact\-SQL в редакторе Transact\-SQL так, чтобы они совпадали со следующими инструкциями:  
  
    ```  
    -- ssNoVersion unit test for Sales.uspFillOrder  
    DECLARE @RC AS INT, @CustomerID AS INT, @Amount AS INT, @FilledDate AS DATETIME, @Status AS CHAR (1);  
    DECLARE @CustomerName AS NVARCHAR(40), @OrderID AS INT;  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
           @OrderID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @FilledDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
    -- Get the most recently added order.  
    SELECT @OrderID = MAX([OrderID]) FROM [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
  
    -- try to cancel an order for that customer that has already been filled  
    EXECUTE @RC = [Sales].[uspCancelOrder] @OrderID;  
  
    SELECT @RC AS RC;  
    ```  
  
3.  На панели **Условия теста** щелкните условие теста «С неопределенным результатом» и затем щелкните значок **Удалить условие теста** .  
  
4.  На панели **Условия теста** щелкните в списке пункт **Скалярное значение** , а затем щелкните значок **Добавить условие теста** .  
  
5.  В окне **Свойства** для свойства **Ожидаемое значение** установите значение 0.  
  
6.  На панели навигации в конструкторе модульных тестов SQL Server щелкните **Sales_uspCancelOrderTest** и убедитесь, что в соседнем списке выделен пункт **Перед тестом**. После выполнения этого шага можно указать инструкции, которые переведут данные в состояние, необходимое для выполнения теста. В этом примере, прежде чем размещать заказ, необходимо создать запись Customer.  
  
7.  Щелкните **Щелкните здесь, чтобы создать**, чтобы создать выполняемый перед тестом скрипт.  
  
8.  Обновите инструкции Transact\-SQL в редакторе Transact\-SQL так, чтобы они совпадали со следующими инструкциями:  
  
    ```  
    /*  
    Add Transact-SQL statements here to run before the test script is run.  
    */  
    BEGIN TRANSACTION  
  
    -- Add a customer for this test with the name 'CustomerB'  
    DECLARE @NewCustomerID AS INT, @RC AS INT, @CustomerName AS NVARCHAR (40);  
  
    SELECT @RC = 0,  
           @NewCustomerID = 0,  
           @CustomerName = N'Fictitious Customer';  
  
    IF NOT EXISTS(SELECT * FROM [Sales].[Customer] WHERE CustomerName = @CustomerName)  
    BEGIN  
    EXECUTE @NewCustomerID = [Sales].[uspNewCustomer] @CustomerName;  
    END  
  
    DECLARE @CustomerID AS INT, @Amount AS INT, @OrderDate AS DATETIME, @FilledDate AS DATETIME, @Status AS CHAR (1), @OrderID AS INT;  
  
    SELECT @RC = 0,  
           @CustomerID = 0,  
       @OrderID = 0,  
           @CustomerName = N'Fictitious Customer',  
           @Amount = 100,  
           @OrderDate = getdate(),  
       @FilledDate = getdate(),  
           @Status = 'O';  
  
    -- NOTE: Assumes that you inserted a Customer record with CustomerName='Fictitious Customer' in the pre-test script.  
    SELECT @CustomerID = [CustomerID] FROM [Sales].[Customer] WHERE [CustomerName] = @CustomerName;  
  
    -- delete any old records in the Orders table and clear out the YTD Sales/Orders fields  
    DELETE from [Sales].[Orders] WHERE [CustomerID] = @CustomerID;  
    UPDATE [Sales].[Customer] SET YTDOrders = 0, YTDSales = 0 WHERE [CustomerID] = @CustomerID;  
  
    -- place an order for that customer  
    EXECUTE @OrderID = [Sales].[uspPlaceNewOrder] @CustomerID, @Amount, @OrderDate, @Status;  
  
    -- fill the order for that customer  
    EXECUTE @RC = [Sales].[uspFillOrder] @OrderID, @FilledDate;  
  
    COMMIT TRANSACTION  
    ```  
  
9. В меню **Файл** выберите команду **Сохранить все**.  
  
    Теперь все готово для запуска тестов.  
  
#### <a name="to-run-the-sql-server-unit-tests"></a>Чтобы выполнить модульные тесты SQL Server, сделайте следующее:  
  
1.  В разделе **Представление теста** щелкните **Sales_uspCancelOrderTest** правой кнопкой мыши и выберите **Выполнить выбранное**.  
  
2.  Просмотрите результаты в окне **Результаты теста** .  
  
    Тест завершается следующей ошибкой.  
  
    **Метод теста TestProject1.SqlServerUnitTests1.Sales_uspCancelOrderTest вызвал исключение: System.Data.SqlClient.SqlException: вы можете отменить только открытые заказы.**  
  
    Далее необходимо изменить код и указать, что исключение является ожидаемым.  
  
#### <a name="to-modify-the-code-for-the-unit-test"></a>Изменение кода модульного теста  
  
1.  В **обозревателе решений** разверните **TestProject1**, щелкните **SqlServerUnitTests1.cs** правой кнопкой мыши и выберите **Просмотреть код**.  
  
2.  В редакторе кода найдите метод Sales_uspCancelOrderTest. Измените атрибуты метода так, чтобы он совпадал со следующим кодом:  
  
    ```  
    [TestMethod(), ExpectedSqlException(Severity=16, MatchFirstError=false, State=1)]  
    public void Sales_uspCancelOrderTest()  
    ```  
  
    Необходимо указать, что ожидается определенное исключение. Можно дополнительно указать номер ошибки. Если не добавить этот атрибут, модульный тест завершится ошибкой и в окне «Результаты теста» появится сообщение.  
  
    > [!IMPORTANT]  
    > Сейчас Visual Studio 2012 не поддерживает атрибут ExpectedSqlException. Сведения о том, как обойти это ограничение, см. в разделе [Невозможно выполнить модульный тест базы данных типа «Ожидаемый сбой»](https://social.msdn.microsoft.com/Forums/en-US/e74e06ad-e3c9-4cb0-97ad-a6f235a52345/unable-to-run-quotexpected-failurequot-database-unit-test).  
  
3.  В меню «Файл» выберите команду «Сохранить SqlServerUnitTests1.cs».  
  
    Далее необходимо повторно выполнить модульный тест, чтобы убедиться, что он завершается ожидаемой ошибкой.  
  
#### <a name="to-re-run-the-sql-server-unit-tests"></a>Чтобы повторно выполнить модульные тесты SQL Server, сделайте следующее:  
  
1.  В разделе **Представление теста** щелкните **Sales_uspCancelOrderTest** правой кнопкой мыши и выберите **Выполнить выбранное**.  
  
2.  Просмотрите результаты в окне **Результаты теста** .  
  
    Тест выполнен, то есть хранимая процедура завершилась ошибкой в нужном участке кода.  
  
## <a name="next-steps"></a>Next Steps  
В типовом проекте обычно определяются дополнительные модульные тесты для проверки исправной работы всех важнейших объектов базы данных. Когда набор тестов задан, эти тесты заносятся в систему управления версиями и делаются доступными другим участникам группы.  
  
После определения основы можно приступить к созданию и изменению объектов базы данных, а затем создать связанные тесты и проверить, влияют ли изменения на ожидаемое поведение.  
  
## <a name="see-also"></a>См. также:  
[Создание и определение модульных тестов SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Проверка кода базы данных с помощью модульных тестов SQL Server](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
[Руководство. Создание пустого модульного теста SQL Server](../ssdt/how-to-create-an-empty-sql-server-unit-test.md)  
[Руководство. Настройка запуска модульного теста SQL Server](../ssdt/how-to-configure-sql-server-unit-test-execution.md)  
  
