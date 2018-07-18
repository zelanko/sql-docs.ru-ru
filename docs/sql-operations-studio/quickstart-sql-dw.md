---
title: 'Краткое руководство: Подключение и запросы к хранилищу данных SQL Azure с помощью SQL Operations Studio (Предварительная версия) | Документация Майкрософт'
description: В этом кратком руководстве показано, как использовать SQL Operations Studio (Предварительная версия) для подключения к базе данных SQL и выполнить запрос
ms.custom: tools|sos
ms.date: 03/08/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 8439dd5881629a5761b1a7a5581489ee47296358
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980496"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-data-in-azure-sql-data-warehouse"></a>Краткое руководство: Использование [!INCLUDE[name-sos](../includes/name-sos-short.md)] подключение и запрос данных в хранилище данных SQL Azure

В этом кратком руководстве показано, как использовать [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения к хранилищу данных Azure SQL, а затем с помощью инструкций Transact-SQL для создания, вставки и выбора данных. 

## <a name="prerequisites"></a>предварительные требования
Для работы в этом кратком руководстве, требуется [!INCLUDE[name-sos](../includes/name-sos-short.md)]и в хранилище данных Azure SQL.

- [Установка [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Если у вас еще нет хранилища данных SQL, см. в разделе [Создание хранилища данных SQL](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision).

Запомните имя сервера и учетные данные для входа!


## <a name="connect-to-your-data-warehouse"></a>Подключение к хранилищу данных

Используйте [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения к серверу хранилища данных SQL Azure.

1. При первом запуске [!INCLUDE[name-sos](../includes/name-sos-short.md)] **подключения** должна открыться страница. Если вы не видите **подключения** щелкните **добавить подключение**, или **новое подключение** значок в **СЕРВЕРЫ** боковой панели:
   
   ![Значок "Создать подключение"](media/quickstart-sql-dw/new-connection-icon.png)

2. В этой статье используется *имя входа SQL*, но *проверки подлинности Windows* также поддерживается. Заполните поля следующим образом с помощью имени сервера, имя пользователя и пароль для *вашей* Azure SQL server:

   | Настройка       | Предлагаемое значение | Описание |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Имя сервера** | Полное имя сервера | Имя должно быть примерно таким: **sqldwsample.database.windows.net** |
   | **Проверка подлинности** | Имя входа SQL| В этом руководстве используется проверка подлинности SQL. |
   | **Имя пользователя** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
   | **Пароль (имя входа SQL)** | Пароль для учетной записи администратора сервера | Это пароль, который был указан при создании сервера. |
   | **Сохранить пароль?** | "Да" или "Нет". | Выберите "Да", если вы не хотите вводить пароль каждый раз. |
   | **Имя базы данных** | *Оставьте поле пустым* | Имя базы данных, с которой необходимо установить соединение. |
   | **Группы серверов** | Выберите <Default> | Если вы создали группу серверов, можно разместить в конкретную группу серверов. | 

   ![Значок "Создать подключение"](media/quickstart-sql-dw/new-connection-screen.png) 

3. Если сервер не имеет правило брандмауэра, разрешающее SQL Operations Studio для подключения, **создать новое правило брандмауэра** открывается форма. Заполните форму для создания нового правила брандмауэра. Дополнительные сведения см. в разделе [правила брандмауэра](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure).

   ![Новое правило брандмауэра](media/quickstart-sql-dw/firewall.png)  

4. После успешного подключения сервера откроется в *серверы* боковой панели.

## <a name="create-the-tutorial-data-warehouse"></a>Создание хранилища данных учебника по службам
1. Щелкните правой кнопкой мыши на сервере, в обозревателе объектов и выберите **новый запрос.**

1. Вставьте следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

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
      CustomerId        INT     NOT NULL,
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```


## <a name="insert-rows"></a>Вставка строк

1. Вставьте следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
      SELECT 1, N'Orlando',N'Australia', N'' UNION ALL
      SELECT 2, N'Keith', N'India', N'keith0@adventure-works.com' UNION ALL
      SELECT 3, N'Donna', N'Germany', N'donna0@adventure-works.com' UNION ALL
      SELECT 4, N'Janet', N'United States', N'janet1@adventure-works.com'
   ```


## <a name="view-the-result"></a>Просмотреть результат
1. Вставьте следующий фрагмент кода в редакторе запросов и нажмите кнопку **запуска**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Результаты запроса отображаются:

   ![Результаты SELECT](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>Очистка ресурсов

Другие статьи в этой коллекции созданы на основе этого краткого руководства. Если вы планируете продолжать работу с этими руководствами, не удаляйте ресурсы, созданные в этом кратком руководстве. Если вы не планируете продолжать работу, следуйте инструкциям ниже, чтобы удалить ресурсы, созданные на портале Azure.
Очистка ресурсов путем удаления группы ресурсов, которые больше не нужны. Дополнительные сведения см. в разделе [очистки ресурсов](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources).


## <a name="next-steps"></a>Следующие шаги

Теперь, когда вы успешно подключились к в хранилище данных Azure SQL и запущен запрос, попробуйте [учебник редактора кода](tutorial-sql-editor.md).