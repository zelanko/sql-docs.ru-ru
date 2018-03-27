---
Title: 'Tutorial: Connect and Query SQL Server using SQL Server Management Studio'
description: Учебник по подключению к SQL Server с помощью SQL Server Management Studio и выполнению базовых запросов T-SQL.
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
ms.openlocfilehash: 7b389c5b58dc0afde077f70e2fd8bec7c6cac4d0
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2018
---
# <a name="tutorial-connect-and-query-sql-server-using-sql-server-management-studio"></a>Учебник. Подключение и выполнение запросов к SQL Server с помощью SQL Server Management Studio
В этом учебнике вы научитесь использовать SQL Server Management Studio (SSMS) для подключения к экземпляру SQL Server и выполнению некоторых основных команд Transact-SQL (T-SQL). В этой статье показано, как выполнять следующие задачи:
    - [Подключение к SQL Server](#connect-to-a-sql-server)
    - [Создание базы данных (**TutorialDB**)](#create-a-database)
    - [Создание таблицы (**Customers**) в новой базе данных](#create-a-table)
    - [Вставка строк в новую таблицу **Customers**](#insert-rows)
    - [Выполнение запроса к таблице **Customers** и просмотр результатов](#view-query-results)
    - [Проверка свойств подключения с помощью окна запроса](#verify-your-query-window-connection-properties)
    - [Изменение сервера, к которому подключено окно запроса](#change-server-connection-within-query-window)


## <a name="prerequisites"></a>предварительные требования
Для работы с этим учебником требуется среда SQL Server Management Studio и доступ к SQL Server. 

- Установите [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).

Если у вас нет доступа к SQL Server, выберите платформу по следующим ссылкам (при использовании проверки подлинности SQL обязательно запомните имя для входа и пароль SQL):
- [Windows — скачать выпуск SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [macOS — скачать SQL Server 2017 с Docker](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker)


## <a name="connect-to-a-sql-server"></a>Подключение к SQL Server

1. Запустите среду SQL Server Management Studio (SSMS).
1. При первом запуске SSMS появляется диалоговое окно **Подключение к серверу**. 
      - Если диалоговое окно **Подключение к серверу** не открывается, его можно открыть вручную, нажав в **обозревателе объектов** кнопку **Подключить** (или щелкнув значок рядом с ней) и выбрав пункт **Ядро СУБД**.

        ![Подключение в обозревателе объектов](media/connect-query-sql-server/connectobjexp.png)

1. В диалоговом окне **Подключение к серверу** укажите параметры подключения: 

    - **Тип сервера**: "Ядро СУБД" (обычно выбрано по умолчанию)
    - **Проверка подлинности**: "Проверка подлинности Windows" (в этой статье используется проверка подлинности Windows, однако также поддерживается имя для входа SQL; при его выборе появляется запрос на ввод имени пользователя и пароля)

      ![Соединение](media/connect-query-sql-server/connection.png)

        Вы также можете изменить дополнительные параметры подключения (например, базу данных, к которой вы подключаетесь, время ожидания подключения и сетевой протокол), нажав кнопку **Параметры**. В этом учебнике оставлены все значения по умолчанию. 

1. Заполнив поля, нажмите кнопку **Подключить**. 

1. Чтобы проверить, успешно ли установлено подключение к серверу SQL Server, просмотрите объекты в **обозревателе объектов**. 

   ![Успешное подключение](media/connect-query-sql-server/successfulconnection.png)


## <a name="create-a-database"></a>Создание базы данных
Ниже приведены инструкции по созданию базы данных с именем TutorialDB. 

1. В **обозревателе объектов** щелкните правой кнопкой мыши сервер и выберите команду **Создать запрос**.

   ![Новый запрос](media/connect-query-sql-server/newquery.png)
   
1. Вставьте в окно запроса следующий фрагмент кода T-SQL: 
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
   ```
2. Чтобы выполнить запрос, нажмите кнопку **Выполнить** (или клавишу F5). 

   ![Выполнение запроса](media/connect-query-sql-server/execute.png)
  
 
После того как запрос выполнится, новая база данных **TutorialDB** появится в списке баз данных в **обозревателе объектов**. Если она не видна, щелкните правой кнопкой мыши узел "Базы данных" и выберите пункт **Обновить**.  


## <a name="create-a-table"></a>Создание таблицы
Ниже приведены инструкции по созданию таблицы в новой базе данных **TutorialDB**. Однако редактор запросов все еще открыт в контексте базы данных *master*, а нам нужно создать таблицу в базе данных *TutorialDB*. 

1. Чтобы изменить контекст подключения для запроса с базы данных master на базу данных **TutorialDB**, выберите нужную базу данных в раскрывающемся списке. 

   ![Изменение базы данных](media/connect-query-sql-server/changedb.png)

1. Вставьте в окно запроса следующий фрагмент кода T-SQL, выделите его и нажмите кнопку **Выполнить** (или клавишу F5): 
    - Вы можете заменить имеющийся текст в окне запроса или добавить новый текст в конце. Чтобы выполнить весь код в окне запроса, нажмите кнопку **Выполнить**. Чтобы выполнить часть кода, выделите ее, а затем нажмите кнопку **Выполнить**.  
  
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
После того как запрос выполнится, новая таблица **Customers** появится в списке таблиц в **обозревателе объектов**. Если таблица не видна, щелкните правой кнопкой мыши узел **TutorialDB > Таблицы** в **обозревателе объектов** и выберите пункт **Обновить**.

## <a name="insert-rows"></a>Вставка строк
Далее мы вставим несколько строк в ранее созданную таблицу **Customers**. 

Вставьте в окно запроса следующий фрагмент кода T-SQL и нажмите кнопку **Выполнить**: 


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

## <a name="view-query-results"></a>Просмотр результатов запроса
Результаты запроса выводятся под текстовым окном запроса. С помощью описанных ниже действий можно выполнить запрос к таблице **Customers** и просмотреть ранее вставленные строки.  

1. Вставьте в окно запроса следующий фрагмент кода T-SQL и нажмите кнопку **Выполнить**: 

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```
1. Результаты запроса отображаются под областью, где был введен текст: 

   ![Результаты запроса](media/connect-query-sql-server/queryresults.png)


1.  Способ представления результатов можно изменить, нажав одну из этих кнопок:

     ![результаты](media/connect-query-sql-server/results.png)

    - По умолчанию результаты выводятся **в виде сетки** (средняя кнопка), то есть они отображаются в таблице. 
    - Если нажать первую кнопку, результаты будут выводиться **в виде текста**, как показано на рисунке в следующем разделе.
    - Третья кнопка позволяет сохранить результаты в файл, который по умолчанию имеет расширение RPT.

## <a name="verify-your-query-window-connection-properties"></a>Просмотр свойств подключения в окне запроса
Сведения о свойствах подключения приводятся под результатами запроса. 
- После выполнения запроса из предыдущего раздела просмотрите свойства подключения в нижней части окна запроса.
    - Вы можете определить, к какому серверу и базе данных вы подключены и от имени какого пользователя выполнен вход.
    - Кроме того, можно узнать длительность выполнения запроса и число строк, возвращенных ранее выполненным запросом.
    
    ![Свойства подключения](media/connect-query-sql-server/connectionproperties.png)  
    На рисунке результаты отображаются **в виде текста**.  

## <a name="change-server-connection-within-query-window"></a>Изменение подключения к серверу в окне запроса
Чтобы изменить сервер, к которому подключено текущее окно запроса, выполните указанные ниже действия.
1. Щелкните правой кнопкой мыши в окне запроса и выберите пункты "Соединение" > "Изменить соединение".
2. Снова откроется диалоговое окно **Подключение к серверу**, позволяющее изменить сервер, к которому подключено окно запроса. 
 
   ![Изменить соединение](media/connect-query-sql-server/changeconnection.png)
   - Обратите внимание, что при этом изменяется только сервер, к которому подключено текущее окно запроса, но не **обозреватель объектов**. 



