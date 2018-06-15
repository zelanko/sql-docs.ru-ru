---
title: 'Краткое руководство: Подключение и отправку запросов SQL Server с помощью операций SQL Studio (Предварительная версия) | Документы Microsoft'
description: Краткого руководства показано, как использовать Studio операций SQL (Предварительная версия) для подключения к SQL Server и выполнить запрос
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
ms.openlocfilehash: 94a760c815b9933ff4d8d7da3dd24c292fcdc641
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235394"
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>Краткое руководство: Подключение и запрос с использованием SQL Server [!INCLUDE[name-sos](../includes/name-sos-short.md)]
Краткого руководства показано, как использовать [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения к SQL Server и затем использовать инструкции Transact-SQL (T-SQL) для создания *TutorialDB* используется в [!INCLUDE[name-sos](../includes/name-sos-short.md)] учебники.

## <a name="prerequisites"></a>предварительные требования

Для выполнения краткого руководства, необходимо [!INCLUDE[name-sos](../includes/name-sos-short.md)]и доступ к SQL Server.

- [Установка [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Если нет доступа к SQL Server, необходимо выбрать платформу по следующим ссылкам (Убедитесь, что вы помните, имя входа SQL и пароля!):
- [Windows — скачать выпуск SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [macOS — скачать SQL Server 2017 с Docker](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker)
- [Linux — загрузки SQL Server 2017 г Developer Edition](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-overview#install) -достаточно выполнить следующие шаги до *создать и запроса данных*.


## <a name="connect-to-a-sql-server"></a>Подключение к SQL Server

   
1. Запуск **[!INCLUDE[name-sos](../includes/name-sos-short.md)]**.
1. При первом запуске *[!INCLUDE[name-sos](../includes/name-sos-short.md)]* **подключения** откроется диалоговое окно. Если **подключения** не открывается диалоговое окно, нажмите кнопку **новое подключение** значок в **СЕРВЕРЫ** страницы:
   
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



1. Вставьте следующий фрагмент кода в окно запроса и нажмите кнопку **запуска**:

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
      CustomerId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```

После завершения выполнения запроса нового **клиентов** таблицы появится в списке таблиц. Щелкните правой кнопкой мыши может потребоваться **TutorialDB > таблиц** , а затем выберите **обновление**.

## <a name="insert-rows"></a>Вставка строк

- Вставьте следующий фрагмент кода в окно запроса и нажмите кнопку **запуска**:

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



## <a name="view-the-data-returned-by-a-query"></a>Просмотр данных, возвращаемых запросом
1. Вставьте следующий фрагмент кода в окно запроса и нажмите кнопку **запуска**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Отображаются результаты запроса:

   ![Выберите результаты](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>Следующие шаги
Теперь, когда вы успешно подключились к SQL Server и выполнения запроса, Попробуйте поработать [учебник редактора кода](tutorial-sql-editor.md).


