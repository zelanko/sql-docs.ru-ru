---
title: 'Краткое руководство: Подключение и запрос SQL Server с помощью SQL Operations Studio (Предварительная версия) | Документация Майкрософт'
description: В этом кратком руководстве показано, как использовать SQL Operations Studio (Предварительная версия) для подключения к SQL Server и выполнить запрос
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
ms.openlocfilehash: 7f8963de448c39709a4df102cdf764a361b7654c
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985076"
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>Краткое руководство: Подключение и запрос с помощью SQL Server [!INCLUDE[name-sos](../includes/name-sos-short.md)]
В этом кратком руководстве показано, как использовать [!INCLUDE[name-sos](../includes/name-sos-short.md)] для подключения к SQL Server, а затем с помощью инструкций Transact-SQL (T-SQL) для создания *TutorialDB* используется в [!INCLUDE[name-sos](../includes/name-sos-short.md)] учебники.

## <a name="prerequisites"></a>предварительные требования

Для работы в этом кратком руководстве, требуется [!INCLUDE[name-sos](../includes/name-sos-short.md)]и доступ к SQL Server.

- [Установка [!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md).

Если у вас нет доступа к SQL Server, выберите платформу по следующим ссылкам (Убедитесь, что вы помните, имя входа SQL и пароль!):
- [Windows — скачать выпуск SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [macOS — скачать SQL Server 2017 с Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)
- [Linux — загрузки SQL Server 2017 Developer Edition](https://docs.microsoft.com/sql/linux/sql-server-linux-overview#install) -необходимо выполните действия до *Создание и запрос данных*.


## <a name="connect-to-a-sql-server"></a>Подключение к SQL Server

   
1. Запуск **[!INCLUDE[name-sos](../includes/name-sos-short.md)]**.
1. При первом запуске *[!INCLUDE[name-sos](../includes/name-sos-short.md)]* **подключения** откроется диалоговое окно. Если **подключения** диалоговое окно не открывается, щелкните **новое подключение** значок в **СЕРВЕРЫ** страницы:
   
   ![Значок "Создать подключение"](media/quickstart-sql-server/new-connection-icon.png)

1. В этой статье используется *имя входа SQL*, но *проверки подлинности Windows* поддерживается. Заполните поля следующим образом:
 
    - **Имя сервера:** localhost
    - **Тип проверки подлинности:** имя входа SQL  
    - **Имя пользователя:** имя пользователя для SQL Server  
    - **Пароль:** пароль для SQL Server  
    - **Имя базы данных:** оставьте это поле пустым 
    - **Группа сервера:** \<по умолчанию\>  

   ![Новый экран подключения](media/quickstart-sql-server/new-connection-screen.png)



## <a name="create-a-database"></a>Создание базы данных

Ниже приведены инструкции по созданию базы данных с именем **TutorialDB**:

1. Щелкните правой кнопкой мыши на своем сервере **localhost**и выберите **новый запрос.**
1. Вставьте следующий фрагмент в окно запроса: 

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
1. Чтобы выполнить запрос, нажмите **запуска** .

После завершения выполнения запроса, новый **TutorialDB** появится в списке баз данных. Если вы не видите его, щелкните правой кнопкой мыши **баз данных** узел и выберите **обновить**.


## <a name="create-a-table"></a>Создание таблицы

Редактор запросов подключен *master* базы данных, но нам нужно создать таблицу в *TutorialDB* базы данных. 

1. Изменить контекст подключения к **TutorialDB**:

   ![Изменение контекста](media/quickstart-sql-server/change-context.png)



1. Вставьте следующий фрагмент в окно запроса и нажмите кнопку **запуска**:

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

После завершения выполнения запроса, новый **клиентов** таблица появится в списке таблиц. Щелкните правой кнопкой мыши может потребоваться **TutorialDB > таблицы** узел и выберите **обновить**.

## <a name="insert-rows"></a>Вставка строк

- Вставьте следующий фрагмент в окно запроса и нажмите кнопку **запуска**:

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
1. Вставьте следующий фрагмент в окно запроса и нажмите кнопку **запуска**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. Результаты запроса отображаются:

   ![Результаты SELECT](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>Следующие шаги
Теперь, когда вы успешно подключились к SQL Server и выполнения запроса, попробуйте [учебник редактора кода](tutorial-sql-editor.md).


