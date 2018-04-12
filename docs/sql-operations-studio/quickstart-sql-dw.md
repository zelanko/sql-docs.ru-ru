---
title: 'Краткое руководство: Подключение и отправку запросов хранилища данных SQL Azure с помощью SQL Operations Studio (preview) | Документы Microsoft'
description: Краткого руководства показано, как использовать для подключения к базе данных SQL и выполнить запрос SQL Operations Studio (preview)
ms.custom: tools|sos
ms.date: 03/08/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d4ed7d25abb2780c719c5b8201ecae54e8e86bf
ms.sourcegitcommit: 6c06267f3eeeb3f0d6fc4c57e1387621720ca8bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2018
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-data-in-azure-sql-data-warehouse"></a>Краткое руководство: Использование [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения и запроса данных в хранилище данных SQL Azure

Это краткое руководство демонстрирует использование [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения к хранилищу данных Azure SQL и затем использовать инструкции Transact-SQL для создания, вставки и выбора данных. 

## <a name="prerequisites"></a>предварительные требования
Для выполнения краткого руководства, необходимо [!INCLUDE[name-sos](../includes/name-sos-short.md)]и хранилище данных Azure SQL.

- [Установка [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Если у вас еще нет хранилища данных SQL, см. раздел [создать хранилище данных SQL](https://docs.microsoft.com/en-us/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision).

Помните, имя сервера и учетные данные входа!


## <a name="connect-to-your-data-warehouse"></a>Подключение к хранилищу данных

Используйте [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения к серверу хранилища данных SQL Azure.

1. При первом запуске [!INCLUDE[name-sos](../includes/name-sos-short.md)] **подключения** должна открыться страница. Если вы не видите **подключения** щелкните **добавить подключение**, или **новое подключение** значок в **СЕРВЕРЫ** боковой панели:
   
   ![Значок нового подключения](media/quickstart-sql-dw/new-connection-icon.png)

2. В этой статье используется *входа SQL*, но *проверки подлинности Windows* также поддерживается. Заполните поля следующим образом с помощью имени сервера, имя пользователя и пароль для *вашей* Azure SQL server:

   | Настройка       | Предлагаемое значение | Описание |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Имя сервера** | Полное имя сервера | Имя должно быть примерно следующим образом: **sqldwsample.database.windows.net** |
   | **Проверка подлинности** | Имя входа SQL| В этом учебнике используется проверка подлинности SQL. |
   | **Имя пользователя** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
   | **Пароль (имя входа SQL)** | Пароль для учетной записи администратора сервера | Это пароль, который был указан при создании сервера. |
   | **Сохранить пароль?** | "Да" или "Нет". | Если вы не хотите вводить пароль каждый раз, нажмите кнопку "Да". |
   | **Имя базы данных** | *Не указывайте* | Имя базы данных, с которой необходимо установить соединение. |
   | **Группы серверов** | Выберите <Default> | Если вы создали группу серверов, можно задать конкретную группу серверов. | 

   ![Значок нового подключения](media/quickstart-sql-dw/new-connection-screen.png) 

3. Если ваш сервер не имеет правило брандмауэра, разрешающее SQL Operations Studio для подключения, **создать новое правило брандмауэра** открывается форма. Заполните форму для создания нового правила брандмауэра. Дополнительные сведения см. в разделе [правила брандмауэра](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Новое правило брандмауэра](media/quickstart-sql-dw/firewall.png)  

4. После успешного подключения к серверу открывается в *серверы* боковой панели.

## <a name="create-the-tutorial-data-warehouse"></a>Создать хранилище данных учебника по службам
1. Щелкните правой кнопкой мыши сервер в обозревателе объектов и выберите **новый запрос.**

1. Следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

   ```sql
    IF NOT EXISTS (
       SELECT name
       FROM sys.databases
       WHERE name = N'TutorialDB'
    )
    CREATE DATABASE [TutorialDB] (EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');
    GO  
    
    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
   ```


## <a name="create-a-table"></a>Создание таблицы

Редактор запросов подключен *master* требуется создание таблицы в базу данных, но мы *TutorialDB* базы данных. 

1. Изменить контекст подключения к **TutorialDB**:

   ![Контекст изменения](media/quickstart-sql-database/change-context.png)


1. Следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

   > [!NOTE]
   > Этот параметр, чтобы добавить или заменить предыдущий запрос в редакторе. Обратите внимание, что нажатие кнопки **запуска** выполняет запрос, который выбран. Если ничего не выделено, щелкнув **запуска** выполняет все запросы в редакторе.

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT     NOT NULL,
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```


## <a name="insert-rows"></a>Вставка строк

1. Следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
      SELECT 1, N'Orlando',N'Australia', N'' UNION ALL
      SELECT 2, N'Keith', N'India', N'keith0@adventure-works.com' UNION ALL
      SELECT 3, N'Donna', N'Germany', N'donna0@adventure-works.com' UNION ALL
      SELECT 4, N'Janet', N'United States', N'janet1@adventure-works.com'
   ```


## <a name="view-the-result"></a>Просмотреть результаты
1. Следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Отображаются результаты запроса:

   ![Выберите результаты](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>Очистка ресурсов

Другие статьи в этой коллекции созданы на основе краткого руководства. Если вы планируете продолжить работу с последующей краткие руководства, очищает ресурсы, созданные в этом кратком руководстве. Если вы не планируете продолжить работу, выполните следующие действия, чтобы удалить ресурсы, созданные на портале Azure краткого руководства.
Очистка ресурсов путем удаления группы ресурсов, которые больше не нужны. Дополнительные сведения см. в разделе [очистки ресурсов](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-get-started-portal#clean-up-resources).


## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы успешно подключились к хранилищу данных Azure SQL и запущен запрос, Попробуйте поработать [учебник редактора кода](tutorial-sql-editor.md).