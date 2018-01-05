---
title: "Краткое руководство: Подключение и отправку запросов SQL Server с помощью операций SQL Studio (Предварительная версия) | Документы Microsoft"
description: "Краткого руководства показано, как использовать Studio операций SQL (Предварительная версия) для подключения к SQL Server и выполнить запрос"
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7588368dcd64316551a9eaa72aeb8ce1d2ea67a6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>Краткое руководство: Подключение и запрос с использованием SQL Server[!INCLUDE[name-sos](../includes/name-sos-short.md)]
Краткого руководства показано, как использовать [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения к SQL Server и затем использовать инструкции Transact-SQL (T-SQL) для создания *TutorialDB* используется в [!INCLUDE[name-sos](../includes/name-sos-short.md)] учебники.

## <a name="prerequisites"></a>предварительные требования

Для выполнения краткого руководства, необходимо [!INCLUDE[name-sos](../includes/name-sos-short.md)]и доступ к SQL Server.

- [Установка [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Если нет доступа к SQL Server, необходимо выбрать платформу по следующим ссылкам (Убедитесь, что вы помните, имя входа SQL и пароля!):
- [Windows - загрузки SQL Server 2017 г Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [macOS - загрузка SQL Server 2017 г. для Docker](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker)
- [Linux — загрузки SQL Server 2017 г Developer Edition](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-overview#install) -достаточно выполнить следующие шаги до *создать и запроса данных*.


## <a name="connect-to-a-sql-server"></a>Подключиться к SQL Server

   
1. Запуск  **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** .
1. При первом запуске  *[!INCLUDE[name-sos](../includes/name-sos-short.md)]*  **подключения** откроется диалоговое окно. Если **подключения** не открывается диалоговое окно, нажмите кнопку **новое подключение** значок в **СЕРВЕРЫ** страницы:
   
   ![Значок нового подключения](media/quickstart-sql-server/new-connection-icon.png)

1. В этой статье используется *входа SQL*, но *проверки подлинности Windows* поддерживается. Заполните поля следующим образом:
 
    - **Имя сервера:** localhost
    - **Тип проверки подлинности:** входа SQL  
    - **Имя пользователя:** имя пользователя для SQL Server  
    - **Пароль:** пароль для SQL Server  
    - **Имя базы данных:** оставьте данное поле пустым 
    - **Группа сервера:** \<по умолчанию\>  

   ![Новый экран подключения](media/quickstart-sql-server/new-connection-screen.png)



## <a name="create-a-database"></a>Создание базы данных

Следующие шаги создания базы данных с именем **TutorialDB**:

1. Щелкните правой кнопкой мыши на вашем сервере **localhost**и выберите **новый запрос.**
1. Вставьте следующий фрагмент кода в окне запроса: 

   ```sql
   USE master
   GO
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
1. Чтобы выполнить запрос, нажмите кнопку **запуска** .

После завершения выполнения запроса нового **TutorialDB** появится в списке баз данных. Если вы не видите его, щелкните правой кнопкой мыши **баз данных** , а затем выберите **обновление**.


## <a name="create-a-table"></a>Создание таблицы

Редактор запросов подключен *master* требуется создание таблицы в базу данных, но мы *TutorialDB* базы данных. 

1. Изменить контекст подключения к **TutorialDB**:

   ![Контекст изменения](media/quickstart-sql-server/change-context.png)



1. Вставьте следующий фрагмент кода в окне запроса:

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

После завершения выполнения запроса нового **клиентов** таблицы появится в списке таблиц. Щелкните правой кнопкой мыши может потребоваться **TutorialDB > таблиц** , а затем выберите **обновление**.

## <a name="insert-rows"></a>Вставка строк

1. Вставьте следующий фрагмент кода в окне запроса:
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

1. Чтобы выполнить запрос, нажмите кнопку **запуска**.


## <a name="view-the-data-returned-by-a-query"></a>Просмотр данных, возвращаемых запросом
1. Вставьте следующий фрагмент кода в окне запроса:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Чтобы выполнить запрос, нажмите кнопку **запуска**.

   ![Выберите результаты](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>Следующие шаги
Теперь, когда вы успешно подключились к SQL Server и выполнения запроса, Попробуйте поработать [учебник редактора кода](tutorial-sql-editor.md).


