---
title: Использовать расширение mssql кода Visual Studio для SQL Server | Документы Microsoft
description: Этого учебника показано, как использовать расширение mssql для VS Code. Это расширение позволяет редактировать и запускать скрипты Transact-SQL в VS Code.
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.technology: database-engine
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: sql-linux
ms.workload: Active
ms.openlocfilehash: fa3fb3c1d807698ddf1fa28c6c710956a75d30ea
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-for-sql-server"></a>Использование кода Visual Studio для создания и выполнения скриптов Transact-SQL для SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье показано, как использовать **mssql** расширения для Visual Studio код (VS) для разработки баз данных SQL Server.

Код Visual Studio — это редактор графического кода для Linux, macOS и Windows, которая поддерживает расширения. [ **Mssql** расширения VS Code] позволяет подключиться к SQL Server, запрос с помощью Transact-SQL (T-SQL) и просмотреть результаты.

## <a name="install-vs-code"></a>Установить VS Code
1. Если вы еще не установили VS Code [загрузки и установки VS Code] на компьютере.

2. Запуск VS Code.

## <a name="install-the-mssql-extension"></a>Установите расширение mssql
Следующие шаги описывают установку расширения mssql. 

1. Нажмите клавишу **CTRL + SHIFT + P** (или **F1**) для открытия в палитру команд в VS Code. 

2. Выберите **установить расширение** и тип **mssql**.
   > [!TIP] 
   > Для macOS **CMD** ключ равнозначен **CTRL** ключа на Windows и Linux.

2. Нажмите "установить" **mssql**. 
   
   <img src="./media/sql-server-linux-develop-use-vscode/vscode-extension.png" alt="Install the extension" style="width: 600px;"/>

3. **Mssql** расширения занимает до одной минуты для установки. Ожидание, о том, что он успешно установлен.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-install-success-notification.png" alt="Installation success notification" style="width: 600px;"/>

   > [!NOTE]
   > Для macOS необходимо установить OpenSSL. Это является необходимым условием для .net Core, используемый расширением mssql. Выполните **Установка предварительные** шагов в [.Net Core инструкции]. Или можно выполнить следующие команды в вашей macOS терминалов.
   >
   >   ```bash
   >   brew update
   >   brew install openssl
   >   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   >   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   >   ```
   
   > [!NOTE]
   > Для Windows 8.1, Windows Server 2012 или более ранние версии, необходимо загрузить и установить [среды выполнения Windows 10 универсальной C]. Загрузите и откройте ZIP-файл. Затем запустите установщик (MSU-файл), предназначенных для текущей конфигурации операционной системы.

## <a name="create-or-open-a-sql-file"></a>Создать или открыть файл SQL

**Mssql** расширение позволяет mssql команды и T-SQL IntelliSense в редакторе когда задан режим языка **SQL**.

1. Нажмите клавишу **CTRL + N**. Код Visual Studio по умолчанию открывается новый файл «Обычный текст». 

2. Нажмите клавишу **CTRL + K, M** и измените режим языка для **SQL**. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png" alt="SQL language mode" style="width: 500px;" />

3. Кроме того можно откройте существующий файл с расширением файла. Режим языка — автоматически **SQL** для файлов с расширением SQL.  

## <a name="connect-to-sql-server"></a>Подключение к SQL Server

Ниже показано, как подключиться к SQL Server с VS Code.

1. В Visual Studio Code нажмите клавиши **CTRL+SHIFT+P** (или **F1**), чтобы открыть палитру команд.

2. Тип **sql** для отображения команд mssql.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-commands.png" alt="mssql commands" style="width: 500px;" />
   

3. Выберите **MS SQL: подключение** команды. Можно просто ввести **sqlcon** и нажмите клавишу **ввод**.

4. Выберите **создать профиль подключения**. Это создает профиль подключения для экземпляра SQL Server.

5. Следуя указаниям, настройте свойства подключения для нового профиля подключения. После указания каждого значения нажимайте клавишу **ВВОД**, чтобы продолжить. 

   В следующей таблице описаны свойства профиля подключения.

   | Настройка | Описание |
   |-----|-----|
   | **Имя сервера** | Имя экземпляра SQL Server. В этом учебнике использовать **localhost** для подключения к локальному экземпляру SQL Server на компьютере. При подключении к удаленному серверу SQL Server, введите имя машины целевого SQL Server или его IP-адрес. Если требуется указать порт для экземпляра SQL Server, используйте запятую, чтобы изолировать его от имени. Например можно ввести для локального сервера, работающего на порту 1401 **localhost, 1401**. |
   | **[Необязательно] Имя базы данных** | База данных, который вы хотите использовать. В целях этого учебника не указать базу данных и нажмите клавишу **ввод** для продолжения. |
   | **Имя пользователя** | Введите имя пользователя, имеющего доступ к базе данных на сервере. В этом учебнике используется значение по умолчанию **SA** учетную запись, созданную во время установки SQL Server. |
   | **Пароль (имя входа SQL)** | Введите пароль для указанного пользователя. | 
   | **Сохранить пароль?** | Тип **Да** сохранить пароль. В противном случае введите **нет** запрашивается пароль каждый раз используется профиль подключения. |
   | **[Необязательно] Введите имя для этого профиля** | Имя профиля подключения. Например, можно назвать профиль **профиль localhost**. 

   > [!Tip] 
   > Можно создавать и изменять профили подключения в файле параметров пользователя (settings.json). Откройте файл параметров, выбрав **предпочтения** и затем **параметры пользователя** в меню VS Code. Дополнительные сведения см. в разделе [управления профилями подключения].

6. Чтобы закрыть информационное сообщение о том, что профиль создан и подключен, нажмите клавишу **ESC**.

   > [!TIP]
   > Если появляется ошибка подключения, сначала будет предпринята попытка диагностировать проблемы из сообщения об ошибках в **выходные данные** панель в VS Code (выберите **вывода** на **представление** меню). Затем ознакомьтесь с [рекомендациями по устранению неполадок с подключением].

7. Проверьте состояние подключения в строке состояния.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png" alt="Connection status" style="width: 500px;" />

## <a name="create-a-database"></a>Создание базы данных

1. В редакторе, введите **sql** Чтобы вывести список фрагментов кода для редактирования. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png" alt="SQL snippets" style="width: 500px;" />

2. Выберите **sqlCreateDatabase**.

3. В приведенном фрагменте введите **TutorialDB** для имени базы данных.

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
   
4. Нажмите клавишу **CTRL + SHIFT + E** для выполнения команд Transact-SQL. Просмотрите результаты в окне запроса.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-create-database-messages.png" alt="create database messages" style="width: 500px;" />

   > [!TIP]
   > Вы можете настроить привязок сочетаний клавиш для команд расширения mssql. В разделе [настроить сочетания клавиш].

## <a name="create-a-table"></a>Создание таблицы

1. Удаление содержимого окна редактора.

2. Нажмите клавишу **F1** для отображения в палитру команд.

3. Тип **sql** в палитру команд для отображения команд SQL или тип **sqluse** для **базы данных SQL: USE MS** команды.

4. Нажмите кнопку **базы данных SQL: USE MS**и выберите **TutorialDB** базы данных. Это изменяет контекст, в новую базу данных, созданных в предыдущем разделе.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-use-database.png" alt="use database" style="width: 500px;" />

3. В редакторе, введите **sql** для отображения фрагменты кода, а затем выберите **sqlCreateTable** и нажмите клавишу **введите**.

4. В приведенном фрагменте введите **сотрудников** имя таблицы.

5. Нажмите клавишу **вкладке**, а затем введите **dbo** для имени схемы.

   > [!NOTE]
   > После добавления фрагмента кода, необходимо ввести имена таблицы и схемы без изменения фокус редактора VS Code.

6. Изменить имя столбца для **Column1** для **имя** и **Column2** для **расположение**.

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

7. Нажмите клавишу **CTRL + SHIFT + E** для создания таблицы.

## <a name="insert-and-query"></a>Вставка и запрос

1. Добавьте следующие инструкции, чтобы вставить четыре строки в **сотрудников** таблицы. Выберите все строки.

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
   > Во время ввода, с помощью помощника T-SQL IntelliSense.
   >   <img src="./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 500px;" />

2. Нажмите клавишу **CTRL + SHIFT + E** для выполнения команд. Два привести отображения наборов в **результатов** окна. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png" alt="Results" style="width: 300px;" />

## <a name="view-and-save-the-result"></a>Просмотр и сохранение результата

1. На **представление** последовательно выберите пункты **макетом группы Переключить редактор** переключиться на вертикальную или горизонтальную разбиение макета.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-split.png" alt="Vertical split" style="width: 500px;" />

2. Нажмите кнопку **результатов** и **сообщений** заголовок панели, чтобы развернуть или свернуть панель.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 500px;" />

   > [!TIP]
   > Можно настроить поведение по умолчанию расширения mssql. В разделе [настройки параметров расширения].

2. Щелкните значок развернуть сетки на второй сетки, чтобы увеличить масштаб.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png" alt="Maximize grid" style="width: 500px;" />

   > [!NOTE]
   > Значок «развернуть» отображает при сценария T-SQL имеет два или более табличной сетки результатов.

3. Откройте контекстное меню сетке с правой кнопкой мыши по сетке. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png" alt="Context menu" style="width: 500px;" />

4. Выберите **выбрать все**.

5. Откройте контекстное меню для сетки и выберите **сохранение JSON** сохранение результата в JSON-файл.

6. Укажите имя файла для файла JSON. В этом учебнике введите **employees.json**.

7. Убедитесь, что JSON-файл сохранен и открыт в VS Code.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png" alt="Save as Json" style="width: 500px;" />

## <a name="next-steps"></a>Следующие шаги

В реальном сценарии, можно создать сценарий, необходимый для сохранения и выполнения более поздней версии (для администрирования или в рамках более крупного проекта разработки). В этом случае можно сохранить скрипт с **.sql** расширения.

Если вы не знакомы с T-SQL, см. раздел [учебника: написание инструкций Transact-SQL] и [Справочник по Transact-SQL (компонент Database Engine)].

Дополнительные сведения о с помощью или способствовали расширения mssql. в разделе [на вики-сайте mssql расширения проекта].

Дополнительные сведения об использовании VS Code см. в разделе [документации Visual Studio Code](https://code.visualstudio.com/docs).

[**mssql** расширения VS Code]:https://aka.ms/mssql-marketplace
[загрузки и установки VS Code]:https://code.visualstudio.com/Download
[.Net Core инструкции]:https://www.microsoft.com/net/core
[управления профилями подключения]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[рекомендациями по устранению неполадок с подключением]:./sql-server-linux-troubleshooting-guide.md#connection
[настроить сочетания клавиш]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[учебника: написание инструкций Transact-SQL]:https://msdn.microsoft.com/library/ms365303.aspx
[Справочник по Transact-SQL (компонент Database Engine)]:https://msdn.microsoft.com/library/bb510741.aspx
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[среды выполнения Windows 10 универсальной C]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[настройки параметров расширения]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[на вики-сайте mssql расширения проекта]: https://github.com/Microsoft/vscode-mssql/wiki
