---
title: Краткое руководство. Подключение и запрос к базе данных Azure SQL
titleSuffix: Azure Data Studio
description: В этом кратком руководстве показано, как использовать Studio данных Azure для подключения к базе данных SQL и выполнить запрос
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
ms.openlocfilehash: bdb1a9c8efb8ebdf5d2e35c1da00c12578ade7d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959438"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>Краткое руководство. Используйте [!INCLUDE[name-sos](../includes/name-sos-short.md)] подключение и запрос базы данных Azure SQL

В этом кратком руководстве вы будете использовать [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения к серверу базы данных SQL Azure. Затем запустим инструкций Transact-SQL (T-SQL) для создания и запроса к базе данных TutorialDB, которая используется в других [!INCLUDE[name-sos](../includes/name-sos-short.md)] учебники.

## <a name="prerequisites"></a>предварительные требования

Для работы в этом кратком руководстве, требуется [!INCLUDE[name-sos](../includes/name-sos-short.md)]и сервер базы данных SQL Azure.

- [Установка [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)

Если у вас нет, сервер Azure SQL, выполните одно из следующих кратких руководств базы данных SQL Azure. Помните, полное имя сервера и войдите в учетных данных для выполнения дальнейших действий:

- [Создание базы данных - портала](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [Создание базы данных - CLI](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [Создание базы данных — PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Подключение к серверу базы данных SQL Azure

Используйте [!INCLUDE[name-sos](../includes/name-sos-short.md)] установить подключение к серверу базы данных SQL Azure.

1. При первом запуске [!INCLUDE[name-sos](../includes/name-sos-short.md)] **приветствия** должна открыться страница. Если вы не видите **приветствия** выберите **помочь** > **приветствия**. Выберите **новое подключение** открыть **подключения** области:
   
   ![Значок "Создать подключение"](media/quickstart-sql-database/new-connection-icon.png)

2. В этой статье используется вход SQL, но также поддерживает проверку подлинности Windows. Заполните следующие поля, используя имя сервера, имя пользователя и пароль для сервера Azure SQL:

   | Параметр       | Предлагаемое значение | Описание |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Имя сервера** | Полное имя сервера | Например: **servername.database.windows.net**. |
   | **Authentication** | Имя входа SQL| В этом учебнике используется проверка подлинности SQL. |
   | **Имя пользователя** | Имя пользователя учетной записи администратора сервера | Имя пользователя из учетной записи, используемой для создания сервера. |
   | **Пароль (имя входа SQL)** | Пароль учетной записи администратора сервера | Пароль из учетной записи, используемой для создания сервера. |
   | **Сохранить пароль?** | "Да" или "Нет". | Выберите **Да** Если вы не хотите вводить пароль каждый раз. |
   | **Имя базы данных** | *Оставьте поле пустым* | Только вы подключаетесь к серверу здесь. |
   | **Группы серверов** | Выберите <Default> | Это поле можно задать в конкретную группу серверов, созданный. | 

   ![Значок "Создать подключение"](media/quickstart-sql-database/new-connection-screen.png)  

3. Выберите **Подключиться**.

4. Если сервер не имеет правило брандмауэра, разрешающее Studio данных Azure для подключения, **создать новое правило брандмауэра** открывается форма. Заполните форму для создания нового правила брандмауэра. Дополнительные сведения см. в разделе [правила брандмауэра](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Новое правило брандмауэра](media/quickstart-sql-database/firewall.png)  

После успешного подключения откроется ваш сервер в **СЕРВЕРЫ** боковой панели.

## <a name="create-the-tutorial-database"></a>Создать базу данных учебника

В следующих разделах Создание базы данных TutorialDB, которая используется в других [!INCLUDE[name-sos](../includes/name-sos-short.md)] учебники.

1. Щелкните правой кнопкой мыши на сервере Azure SQL в **СЕРВЕРЫ** боковой панели и выберите **новый запрос**.

1. Вставьте этот SQL в редакторе запросов.

   ```sql
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO

   ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
   GO
   ```

1. На панели инструментов выберите **запуска**. Уведомления появляются в **сообщений** области, показывающая ход выполнения запроса.

## <a name="create-a-table"></a>Создание таблицы

Редактор запросов подключен к **master** базы данных, но нам нужно создать таблицу в **TutorialDB** базы данных. 

1. Подключение к **TutorialDB** базы данных.

   ![Изменение контекста](media/quickstart-sql-database/change-context2.png)



1. Создание `Customers` таблицы. 

   Замените предыдущий запрос в редакторе запросов с этой и выберите **запуска**.

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```


## <a name="insert-rows-into-the-table"></a>Вставка строк в таблице

Замените предыдущий запрос с этой и выберите **запуска**.

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
   VALUES
      ( 1, N'Orlando', N'Australia', N''),
      ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
      ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
      ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
   GO
   ```

## <a name="view-the-result"></a>Просмотреть результат

Замените предыдущий запрос с этой и выберите **запуска**.

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

Отобразить результаты запроса:

   ![Результаты SELECT](media/quickstart-sql-database/select-results2.png)


## <a name="clean-up-resources"></a>Очистка ресурсов

Более поздние версии кратких руководствах созданы на ресурсы, созданные здесь. Если вы планируете работать в этих статьях, не забудьте не удалить эти ресурсы. В противном случае на портале Azure, удалите ресурсы, которые больше не требуется. Дополнительные сведения см. в разделе [очистки ресурсов](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources).

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы успешно подключились на базы данных Azure SQL и запустите запрос, попробуйте [учебник редактора кода](tutorial-sql-editor.md).
