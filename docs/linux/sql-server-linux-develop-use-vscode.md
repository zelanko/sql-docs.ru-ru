---
title: С помощью расширения mssql Visual Studio Code для SQL Server в Linux | Документация Майкрософт
description: Используйте расширение mssql для Visual Studio Code для редактирования и выполнять скрипты Transact-SQL для SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/18/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: sql-linux
ms.openlocfilehash: 583c7ac13b49370b333e80568c4b52885b58dcf3
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100569"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-on-linux"></a>Использование Visual Studio Code для создания и выполнения скриптов Transact-SQL в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье показано, как использовать *mssql* расширения для Visual Studio Code для разработки баз данных SQL Server в Linux.

## <a name="install-and-start-visual-studio-code"></a>Установите и запустите Visual Studio Code

Visual Studio Code — графический редактор кода для Linux, macOS и Windows, который поддерживает расширения. 

1. [Скачайте и установите Visual Studio Code] на вашем компьютере.
   
1. Запустите Visual Studio Code.
   
   >[!NOTE]
   >Если Visual Studio Code не запускается, когда вы подключены через сеанс удаленного рабочего стола xrdp, см. в разделе [VS Code, не работает в Ubuntu, при подключении по протоколу XRDP](https://github.com/Microsoft/vscode/issues/3451).

## <a name="install-the-mssql-extension"></a>Установка расширения mssql

[Расширение mssql для Visual Studio Code] позволяет подключаться к SQL Server, запрос с помощью Transact-SQL (T-SQL) и просмотреть результаты.

1. В Visual Studio Code, выберите **представление** > **палитру команд**, или нажмите клавишу **Ctrl**+**Shift** + **P**, или нажмите клавишу **F1** открыть **палитру команд**. 
   
1. В **палитру команд**выберите **расширения: Установка расширений** из раскрывающегося списка. 
   
1. В **расширения** введите *mssql*.
   
1. Выберите **SQL Server (mssql)** расширения, а затем выберите **установить**. 
   
   ![Установка расширения mssql](./media/sql-server-linux-develop-use-vscode/vscode-extension.png)   
   
1. После завершения установки выберите **перезагрузить** включить расширение. 

## <a name="create-or-open-a-sql-file"></a>Создайте или откройте файл SQL

Расширение mssql включает команды mssql и T-SQL IntelliSense в редакторе кода при языка используется режим **SQL**.

1. Выберите **файл** > **новый файл** или нажмите клавишу **Ctrl**+**N**. Visual Studio Code Откроется новый обычный текстовый файл по умолчанию. 

1. Выберите **обычный текст** в нижней строке состояния, или нажмите клавишу **Ctrl**+**K** > **M**и выберите **SQL** из раскрывающегося списка языков. 
   
   ![Языковой режим SQL](./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png)   
   
Если открыть существующий файл, имеющий *.sql* расширение файла, языковой режим автоматически присваивается SQL.  

## <a name="connect-to-sql-server"></a>Подключение к SQL Server

Выполните следующие действия, чтобы создать профиль подключения и подключиться к SQL Server.

> [!TIP] 
> Можно также создавать и изменять профили подключений в файле параметров пользователя (*settings.json*). Чтобы открыть файл параметров, выберите **файл** > **предпочтения** > **параметры**. Дополнительные сведения см. в разделе [Управление профилями подключения].
   
1. Нажмите клавишу **Ctrl**+**Shift**+**P** или **F1** открыть **палитру команд**. 
   
1. Тип *sql* для отображения mssql команд или тип *sqlcon*, а затем выберите **MS SQL: Подключение** из раскрывающегося списка.
   
   ![команды MSSQL](./media/sql-server-linux-develop-use-vscode/vscode-commands.png)   
   
   >[!NOTE]
   >Файл SQL, таких как пустой файл SQL, который вы создали, фокус должен быть в редакторе кода перед выполнением команды mssql. 

1. Выберите **создать профиль подключения** для создания нового профиля подключения для SQL Server.
   
1. Следуйте инструкциям на экране, чтобы задать свойства для нового профиля подключения. После указания каждого значения, нажмите клавишу **ввод** для продолжения. 
   
   1. **Имя сервера или строка подключения ADO**: Укажите имя экземпляра SQL Server. Используйте *localhost* для подключения к экземпляру SQL Server на локальном компьютере. Чтобы подключиться к удаленному серверу SQL Server, введите имя целевого SQL Server, или его IP-адрес. Если вам нужно указать порт, используйте запятую, чтобы отделить его от имени. Например, для локального сервера, работающего на порт 1401, введите *localhost, 1401*. 
      
      >[!NOTE]
      >Также можно ввести строку подключения ADO для базы данных, нажмите клавишу **ввод**, при необходимости имя профиля подключения, а затем нажмите клавишу **ввод** еще раз, чтобы подключиться и создать профиль. 
      
   1. **Имя базы данных** (необязательно): База данных, который вы хотите использовать. Чтобы создать новую базу данных, не указать базу данных имя и нажмите клавишу **ввод** для продолжения. 
      
   1. **Тип проверки подлинности**: Нажмите клавишу **ввод** для выбора **имя входа SQL**. 
      
   1. **Имя пользователя**: Введите имя пользователя, имеющего доступ к базе данных на сервере.
      
   1. **Пароль**: Введите пароль для указанного пользователя.
      
   1. **Сохранить пароль**: Нажмите клавишу **ввод** для выбора **Да** и сохранять пароль. Выберите **нет** запрашивается пароль каждый раз, используется профиль подключения. 
      
   1. **Имя профиля** (необязательно): Введите имя для профиля подключения, такие как *профиль localhost*. 
   
   После выбора **ввод**, Visual Studio Code создает профиль подключения и подключается к SQL Server. 
   
   > [!TIP]
   > Если подключение отсутствует, попробуйте для диагностики проблемы из сообщения об ошибке в **вывода** панели в Visual Studio Code. Чтобы открыть **выходные данные** панели, выберите **представление** > **вывода**. Кроме того, просмотрите [рекомендации по устранению неполадок подключения].
   
1. Проверка подключения в нижней строке состояния.
   
  ![Состояние подключения](./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png)   
   
## <a name="create-a-sql-database"></a>Создание базы данных SQL

1. В новый файл SQL, который был запущен ранее, введите *sql* для отображения списка фрагментов кода для редактирования. 

  ![Фрагменты кода SQL](./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png)   
   
1. Выберите **sqlCreateDatabase**.
   
1. В указанном фрагменте кода замените `DatabaseName` с `TutorialDB`:
   
   ```sql
   -- Create a new database called 'TutorialDB'
   -- Connect to the 'master' database to run this snippet
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
   
1. Нажмите клавишу **Ctrl**+**Shift**+**E** для выполнения команд Transact-SQL. Просмотрите результаты в окне запроса.
   
  ![Создание базы данных сообщений](./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png)   
   
> [!TIP]
> Вы можете настроить сочетания клавиш для команды mssql. См. в разделе [Настройка сочетания клавиш].

## <a name="create-a-table"></a>Создание таблицы

1. Удалите содержимое окна редактора кода.
   
1. Нажмите клавишу **Ctrl**+**Shift**+**P** или **F1** открыть **палитру команд**. 
   
1. Тип *sql* для отображения mssql команд или тип *sqluse*и выберите **базы данных SQL: USE MS** команды.
   
1. Выберите новый **TutorialDB** базы данных. 
   
   ![Использование базы данных](./media/sql-server-linux-develop-use-vscode/vscode-use-database.png)   
   
1. В редакторе кода введите *sql* для отображения фрагменты кода, выберите **sqlCreateTable**, а затем нажмите клавишу **ввод**.
   
1. В приведенном фрагменте введите *сотрудников* имя таблицы и *dbo* для имени схемы.
   
1. Создайте столбцы, как показано в следующем коде:
   
   ```sql
   -- Create a new table called 'Employees' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Employees', 'U') IS NOT NULL
   DROP TABLE dbo.Employees
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Employees
   (
      EmployeesId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location   [NVARCHAR](50)  NOT NULL
   );
   GO
   ```
   
1. Нажмите клавишу **Ctrl**+**Shift**+**E** для создания таблицы.

## <a name="insert-and-query"></a>Вставка и запрос

1. Добавьте следующие инструкции, чтобы вставить четыре строки в **сотрудников** таблицы. 

   ```sql
   -- Insert rows into table 'Employees'
   INSERT INTO Employees
      ([EmployeesId],[Name],[Location])
   VALUES
      ( 1, N'Jared', N'Australia'),
      ( 2, N'Nikita', N'India'),
      ( 3, N'Tom', N'Germany'),
      ( 4, N'Jake', N'United States')   
   GO   
   -- Query the total count of employees
   SELECT COUNT(*) as EmployeeCount FROM dbo.Employees;
   -- Query all employee information
   SELECT e.EmployeesId, e.Name, e.Location 
   FROM dbo.Employees as e
   GO
   ```
   
   > [!TIP]
   > При вводе, используйте IntelliSense для T-SQL для выполнения инструкций.
   >![T-SQL IntelliSense](./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png)   
   
1. Нажмите клавишу **Ctrl**+**Shift**+**E** для выполнения команд. Два привести отображения наборов в **результаты** окна. 
   
   ![Результаты](./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png)   

## <a name="view-and-save-the-result"></a>Просмотреть и сохранить результаты
   
1. Выберите **представление** > **редактор макета** > **перевернуть макета** переключиться на макет вертикальные или горизонтальные разделения.
   
1. Выберите **результатов** и **сообщений** панели заголовки для свертывания и развертывания панелей.
   
   ![Переключить заголовки](./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png)   
   
   > [!TIP]
   > Можно настроить поведение по умолчанию расширения mssql. См. в разделе [Настройка параметров расширения].
   
1. Выберите значок сетки "Развернуть" на второй таблицы результатов для увеличения изображения на этих результатов.
   
   ![Максимально увеличить сетки](./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png)   
   
   > [!NOTE]
   > Значок "Развернуть" отображается, когда скрипт T-SQL создает табличной сетки результатов в двух или более.
   
1. Откройте контекстное меню сетки, щелкните правой кнопкой мыши в сетке. 
   
   ![Контекстное меню](./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png)   
   
1. Выберите **выбрать все**.
   
1. Снова откройте контекстное меню для сетки и выберите **Сохранить как JSON** сохранить результат *.json* файла.
   
1. Укажите имя файла для JSON-файла. 
   
1. Убедитесь, что JSON-файл сохраняет и открывается в Visual Studio Code.
   
   ![сохранить в формате JSON.](./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png)   

Если вам нужно сохранить и последующего выполнения скриптов SQL для администрирования или более крупного проекта разработки Сохранение скриптов с *.sql* расширения.

## <a name="next-steps"></a>Следующие шаги

Если вы не знакомы с T-SQL, см. в разделе [Учебник. Написание инструкций Transact-SQL] и [Справочник по Transact-SQL (ядро СУБД)].

Дополнительные сведения о с помощью или способствовать низкой расширения mssql см. в разделе [вики-сайте проекта расширения mssql].

Дополнительные сведения об использовании Visual Studio Code см. в разделе [документации Visual Studio Code](https://code.visualstudio.com/docs).

[расширение MSSQL для Visual Studio Code]:https://aka.ms/mssql-marketplace
[Скачайте и установите Visual Studio Code]:https://code.visualstudio.com/Download
[.Net Core instructions]:https://www.microsoft.com/net/core
[Управление профилями подключения]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[рекомендации по устранению неполадок подключения]:./sql-server-linux-troubleshooting-guide.md#connection
[Настройка сочетания клавиш]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[Учебник. Написание инструкций Transact-SQL]:https://docs.microsoft.com/sql/t-sql/tutorial-writing-transact-sql-statements
[Справочник по Transact-SQL (ядро СУБД)]:https://docs.microsoft.com/sql/t-sql/language-reference
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 Universal C Runtime]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[Настройка параметров расширения]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[вики-сайте проекта расширения MSSQL]: https://github.com/Microsoft/vscode-mssql/wiki
