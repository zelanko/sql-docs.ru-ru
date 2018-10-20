---
title: 'Краткое руководство: Подключение и запрос к базе данных Azure SQL, студии данных Azure | Документация Майкрософт'
description: В этом кратком руководстве показано, как использовать Studio данных Azure для подключения к базе данных SQL и выполнить запрос
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: a1d39e8ebd3d986825141b1acadd0ebc782083a6
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356045"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>Краткое руководство: Использование [!INCLUDE[name-sos](../includes/name-sos-short.md)] подключение и запрос базы данных Azure SQL

В этом кратком руководстве показано, как использовать *[!INCLUDE[name-sos](../includes/name-sos-short.md)]* для соединения с базой данных Azure SQL, а затем с помощью инструкций Transact-SQL (T-SQL) для создания *TutorialDB* используется в [!INCLUDE[name-sos](../includes/name-sos-short.md)] руководства.

## <a name="prerequisites"></a>предварительные требования

Для работы в этом кратком руководстве, требуется [!INCLUDE[name-sos](../includes/name-sos-short.md)]и сервер Azure SQL.

- [Установка [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Если у вас еще нет на сервере Azure SQL, выполните одно из следующих кратких руководств базы данных SQL Azure (Помните, имя сервера и учетные данные для входа!).

- [Создание базы данных - портала](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [Создание базы данных - CLI](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [Создание базы данных — PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Подключение к серверу базы данных SQL Azure

Используйте [!INCLUDE[name-sos](../includes/name-sos-short.md)] установить подключение к серверу базы данных SQL Azure.

1. При первом запуске [!INCLUDE[name-sos](../includes/name-sos-short.md)] **подключения** должна открыться страница. Если вы не видите **подключения** щелкните **добавить подключение**, или **новое подключение** значок в **СЕРВЕРЫ** боковой панели:
   
   ![Значок "Создать подключение"](media/quickstart-sql-database/new-connection-icon.png)

2. В этой статье используется *имя входа SQL*, но *проверки подлинности Windows* также поддерживается. Заполните поля следующим образом с помощью имени сервера, имя пользователя и пароль для *вашей* Azure SQL server:

   | Настройка       | Предлагаемое значение | Описание |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Имя сервера** | Полное имя сервера | Имя должно быть примерно таким: **servername.database.windows.net** |
   | **Проверка подлинности** | Имя входа SQL| В этом руководстве используется проверка подлинности SQL. |
   | **Имя пользователя** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
   | **Пароль (имя входа SQL)** | Пароль для учетной записи администратора сервера | Это пароль, который был указан при создании сервера. |
   | **Сохранить пароль?** | "Да" или "Нет". | Выберите "Да", если вы не хотите вводить пароль каждый раз. |
   | **Имя базы данных** | *Оставьте поле пустым* | Имя базы данных, которую вы хотите подключиться. |
   | **Группы серверов** | Выберите <Default> | Если вы создали группу серверов, можно разместить в конкретную группу серверов. | 

   ![Значок "Создать подключение"](media/quickstart-sql-database/new-connection-screen.png)  

3. Если сервер не имеет правило брандмауэра, разрешающее Studio данных Azure для подключения, **создать новое правило брандмауэра** открывается форма. Заполните форму для создания нового правила брандмауэра. Дополнительные сведения см. в разделе [правила брандмауэра](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Новое правило брандмауэра](media/quickstart-sql-database/firewall.png)  

4. После успешного подключения сервера откроется в *серверы* боковой панели.

## <a name="create-the-tutorial-database"></a>Создать базу данных учебника

Следующие разделы создают *TutorialDB* базы данных, который используется в нескольких [!INCLUDE[name-sos](../includes/name-sos-short.md)] учебники.

1. Щелкните правой кнопкой нужный сервер Azure SQL на боковой панели СЕРВЕРОВ и выберите **новый запрос.**

1. Вставьте следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

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



## <a name="create-a-table"></a>Создание таблицы

Редактор запросов подключен *master* базы данных, но нам нужно создать таблицу в *TutorialDB* базы данных. 

1. Изменить контекст подключения к **TutorialDB**:

   ![Изменение контекста](media/quickstart-sql-database/change-context.png)



1. Вставьте следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

   > [!NOTE]
   > Можно добавить ее, или перезаписать предыдущий запрос в редакторе. Обратите внимание, что нажатие кнопки **запуска** выполняет запрос, который выбран. Если ничего не выбрано, после нажатия кнопки **запуска** выполняет все запросы в редакторе.

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


## <a name="insert-rows"></a>Вставка строк

- Вставьте следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

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
1. Вставьте следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Результаты запроса отображаются:

   ![Результаты SELECT](media/quickstart-sql-database/select-results.png)


## <a name="clean-up-resources"></a>Очистка ресурсов

Другие статьи в этой коллекции созданы на основе этого краткого руководства. Если вы планируете продолжать работу с этими руководствами, не удаляйте ресурсы, созданные в этом кратком руководстве. Если вы не планируете продолжать работу, следуйте инструкциям ниже, чтобы удалить ресурсы, созданные на портале Azure.
Очистка ресурсов путем удаления группы ресурсов, которые больше не нужны. Дополнительные сведения см. в разделе [очистки ресурсов](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources).

## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы успешно подключились к базе данных Azure SQL и запущен запрос, попробуйте [учебник редактора кода](tutorial-sql-editor.md).
