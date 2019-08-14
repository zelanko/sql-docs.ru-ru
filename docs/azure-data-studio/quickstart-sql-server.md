---
title: Краткое руководство. Подключение и отправка запроса к SQL Server
titleSuffix: Azure Data Studio
description: В этом кратком руководстве показано, как использовать Azure Data Studio для подключения к SQL Server и выполнения запроса.
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
ms.openlocfilehash: 4117d8c16e96252f792e14d282d285527008874f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959394"
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>Краткое руководство. Подключение и отправка запроса к SQL Server с помощью [!INCLUDE[name-sos](../includes/name-sos-short.md)]
В этом кратком руководстве показано, как использовать [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения к SQL Server, а затем с помощью инструкций Transact-SQL (T-SQL) создать базу данных *TutorialDB*, применяемую в руководствах [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="prerequisites"></a>предварительные требования

Для работы с этим кратким руководством потребуется [!INCLUDE[name-sos](../includes/name-sos-short.md)] и доступ к SQL Server.

- [Установите [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md).

Если у вас нет доступа к SQL Server, выберите платформу по следующим ссылкам (обязательно запомните имя для входа и пароль SQL):
- [Windows — скачать выпуск SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads)
- [macOS — скачать SQL Server 2017 с Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)
- [Linux — скачать выпуск SQL Server 2017 Developer Edition](https://docs.microsoft.com/sql/linux/sql-server-linux-overview#install). Необходимо выполнить действия только до этапа *создания и отправки запроса к данным*.


## <a name="connect-to-a-sql-server"></a>Подключение к SQL Server

   
1. Запустите **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** .
1. При первом запуске [!INCLUDE[name-sos](../includes/name-sos-short.md)] должна открыться страница **приветствия**. Если она не отображается, выберите **Справка** > **Приветствие**. Выберите **Создать подключение**, чтобы открыть панель **Подключение**.
   
   ![Значок нового подключения](media/quickstart-sql-server/new-connection-icon.png)

1. В этой статье используется *имя входа SQL*, но поддерживается *проверка подлинности Windows*. Заполните поля следующим образом:
 
    - **Имя сервера:** localhost
    - **Тип проверки подлинности:** Имя входа SQL  
    - **Имя пользователя:** имя пользователя SQL Server  
    - **Пароль:** пароль для SQL Server  
    - **Имя базы данных:** оставьте это поле пустым 
    - **Группа серверов:** \<по умолчанию\>  

   ![Экран нового подключения](media/quickstart-sql-server/new-connection-screen.png)



## <a name="create-a-database"></a>Создание базы данных

Ниже приведены инструкции по созданию базы данных с именем **TutorialDB**.

1. Щелкните правой кнопкой мыши сервер **localhost** и выберите **Создать запрос**.
1. Вставьте в окно запроса следующий фрагмент: 

   ```sql
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
      CREATE DATABASE [TutorialDB];
   GO
   IF SERVERPROPERTY('ProductVersion') > '12'
       ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON;
   GO
   ```
1. Чтобы выполнить запрос, нажмите кнопку **Выполнить**.

После выполнения запроса новая база данных **TutorialDB** появится в списке баз данных. Если она не отображается, щелкните правой кнопкой мыши узел **Базы данных** и выберите пункт **Обновить**.


## <a name="create-a-table"></a>Создание таблицы

Редактор запросов все еще подключен к базе данных *master*, но нам нужно создать таблицу в базе данных *TutorialDB*. 

1. Измените контекст подключения на **TutorialDB**.

   ![Изменение контекста](media/quickstart-sql-server/change-context.png)



1. Вставьте в окно запроса следующий фрагмент и нажмите кнопку **Выполнить**.

   > [!NOTE]
   > Этот фрагмент можно добавить в предыдущий запрос либо можно перезаписать предыдущий запрос в редакторе. Обратите внимание, что при нажатии кнопки **Выполнить** выполняется только выбранный запрос. Если ничего не выбрано, при нажатии кнопки **Выполнить** выполняются все запросы в редакторе.

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
      DROP TABLE dbo.Customers;
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
       CustomerId  int NOT NULL PRIMARY KEY, -- primary key column
       Name        nvarchar(50) NOT NULL,
       Location    nvarchar(50) NOT NULL,
       Email       nvarchar(50) NOT NULL
   );
   GO
   ```

После выполнения запроса новая таблица **Customers** появится в списке таблиц. Может потребоваться щелкнуть **правой кнопкой мыши узел TutorialDB > Таблицы** и выбрать пункт **Обновить**.

## <a name="insert-rows"></a>Вставка строк

- Вставьте в окно запроса следующий фрагмент и нажмите кнопку **Выполнить**.

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId], [Name], [Location], [Email])
   VALUES
      ( 1, N'Orlando', N'Australia', N''),
      ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
      ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
      ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
   GO
   ```



## <a name="view-the-data-returned-by-a-query"></a>Просмотр данных, возвращенных запросом
1. Вставьте в окно запроса следующий фрагмент и нажмите кнопку **Выполнить**.

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Будут отображены результаты запроса:

   ![Выбор результатов](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>Следующие шаги
После успешного подключения к SQL Server и выполнения запроса можно перейти к [руководству по редактору кода](tutorial-sql-editor.md).


