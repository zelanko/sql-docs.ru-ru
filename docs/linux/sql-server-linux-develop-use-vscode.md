---
title: С помощью расширения mssql Visual Studio Code для SQL Server | Документация Майкрософт
description: Этом руководстве показано, как с помощью расширения mssql для Visual STUDIO Code. Это расширение позволяет изменять и выполнять скрипты Transact-SQL в VS Code.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9766ee75-32d3-4045-82a6-4c7968bdbaa6
ms.custom: sql-linux
ms.openlocfilehash: b1ae9056ecbaf158b275798d69d691ae64e6ef06
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033631"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts-for-sql-server"></a>Использование Visual Studio Code для создания и выполнения скриптов Transact-SQL для SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье показано, как использовать **mssql** расширение для Visual Studio Code (VS Code) для разработки баз данных SQL Server.

Visual Studio Code — графический редактор кода для Linux, macOS и Windows, который поддерживает расширения. [**mssql** расширения VS Code] позволяет подключиться к SQL Server, запрос с помощью Transact-SQL (T-SQL) и просмотреть результаты.

## <a name="install-vs-code"></a>Установка VS Code
1. Если вы еще не установили VS Code, [Скачайте и установите Visual STUDIO Code] на вашем компьютере.

2. Запустите VS Code.

## <a name="install-the-mssql-extension"></a>Установка расширения mssql
Следующие шаги описывают установку расширения mssql. 

1. Нажмите клавишу **CTRL + SHIFT + P** (или **F1**) чтобы открыть палитру команд в VS Code. 

2. Выберите **Установка расширения** и тип **mssql**.
   > [!TIP] 
   > Для macOS **CMD** ключ равнозначен **CTRL** ключей в Linux и Windows.

2. Щелкните "установить" **mssql**. 
   
   <img src="./media/sql-server-linux-develop-use-vscode/vscode-extension.png" alt="Install the extension" style="width: 600px;"/>

3. **Mssql** расширения занимает до одной минуты для установки. Ожидание, указывающее, что он успешно установлен.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-install-success-notification.png" alt="Installation success notification" style="width: 600px;"/>

   > [!NOTE]
   > Для macOS необходимо установить OpenSSL. Это является необходимым условием для.Net Core, используемый с помощью расширения mssql. Выполните **установите компоненты** шагов в [Инструкции по.Net Core]. Или можно выполнить следующие команды в терминале macOS.
   >
   >   ```bash
   >   brew update
   >   brew install openssl
   >   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   >   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   >   ```
   
   > [!NOTE]
   > Для Windows 8.1, Windows Server 2012 или более ранние версии, необходимо загрузить и установить [Windows 10 универсальная среда выполнения C]. Скачайте и откройте ZIP-файл. Запустите установщик (MSU-файл), предназначенных для текущей конфигурации операционной системы.

## <a name="create-or-open-a-sql-file"></a>Создайте или откройте файл SQL

**Mssql** расширение включает команды mssql и T-SQL IntelliSense в редакторе при языка используется режим **SQL**.

1. Нажмите клавишу **CTRL + N**. Visual Studio Code Откроется новый файл «Обычный текст» по умолчанию. 

2. Нажмите клавишу **CTRL + K, M** и измените режим языка для **SQL**. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-language-mode.png" alt="SQL language mode" style="width: 500px;" />

3. Кроме того можно откройте существующий файл с расширением .sql. Языковой режим является автоматически **SQL** для файлов с расширением .sql.  

## <a name="connect-to-sql-server"></a>Подключение к SQL Server

Ниже показано, как подключиться к SQL Server с помощью VS Code.

1. В Visual Studio Code нажмите клавиши **CTRL+SHIFT+P** (или **F1**), чтобы открыть палитру команд.

2. Тип **sql** для отображения команды mssql.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-commands.png" alt="mssql commands" style="width: 500px;" />
   

3. Выберите **MS SQL: подключение** команды. Можно просто ввести **sqlcon** и нажмите клавишу **ввод**.

4. Выберите **создать профиль подключения**. Это создает профиль подключения для экземпляра SQL Server.

5. Следуя указаниям, настройте свойства подключения для нового профиля подключения. После указания каждого значения нажимайте клавишу **ВВОД**, чтобы продолжить. 

   В следующей таблице описаны свойства профиля подключения.

   | Настройка | Описание |
   |-----|-----|
   | **Имя сервера** | Имя экземпляра SQL Server. Для этого руководства используйте **localhost** для подключения к локальному экземпляру SQL Server на компьютере. При подключении к удаленному серверу SQL Server, введите имя целевого компьютера SQL Server или его IP-адрес. Если вам нужно указать порт для экземпляра SQL Server, используйте запятую, чтобы отделить его от имени. Например можно ввести для локального сервера, работающего на порт 1401 **localhost, 1401**. |
   | **[Необязательно] Имя базы данных** | База данных, который вы хотите использовать. Для целей данного учебника, не указать базу данных и нажмите клавишу **ввод** для продолжения. |
   | **Имя пользователя** | Введите имя пользователя, имеющего доступ к базе данных на сервере. В этом руководстве используйте значение по умолчанию **SA** учетной записи, созданной во время работы программы установки SQL Server. |
   | **Пароль (имя входа SQL)** | Введите пароль для указанного пользователя. | 
   | **Сохранить пароль?** | Тип **Да** для сохранения пароля. В противном случае введите **нет** запрашивается пароль каждый раз, используется профиль подключения. |
   | **[Необязательно] Введите имя для этого профиля** | Имя профиля подключения. Например, можно назвать профиля **профиль localhost**. 

   > [!Tip] 
   > Можно создавать и изменять профили подключений в файле параметров пользователя (settings.json). Откройте файл параметров, выбрав **предпочтения** и затем **параметры пользователя** в меню Visual STUDIO Code. Дополнительные сведения см. в разделе [Управление профилями подключения].

6. Чтобы закрыть информационное сообщение о том, что профиль создан и подключен, нажмите клавишу **ESC**.

   > [!TIP]
   > Если возникнет ошибка подключения, сначала попробуйте узнать проблему из сообщения об ошибке в **вывода** панели в VS Code (выберите **выходные данные** на **представление** меню). Затем ознакомьтесь с [рекомендациями по устранению неполадок с подключением].

7. Проверьте состояние подключения в строке состояния.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png" alt="Connection status" style="width: 500px;" />

## <a name="create-a-database"></a>Создание базы данных

1. В редакторе, введите **sql** откроется список фрагментов кода для редактирования. 

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
   > Вы можете настроить сочетания клавиш для команды расширения mssql. См. в разделе [Настройка сочетания клавиш].

## <a name="create-a-table"></a>Создание таблицы

1. Удаляет содержимое окна редактора.

2. Нажмите клавишу **F1** чтобы отобразить палитру команд.

3. Тип **sql** в палитре команд для отображения команд SQL или тип **sqluse** для **базы данных SQL: USE MS** команды.

4. Нажмите кнопку **базы данных SQL: USE MS**и выберите **TutorialDB** базы данных. Это изменяет контекст, в новую базу данных, созданные в предыдущем разделе.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-use-database.png" alt="use database" style="width: 500px;" />

3. В редакторе, введите **sql** для отображения фрагменты кода, а затем выберите **sqlCreateTable** и нажмите клавишу **введите**.

4. В приведенном фрагменте введите **сотрудников** имя таблицы.

5. Нажмите клавишу **вкладке**, а затем введите **dbo** для имени схемы.

   > [!NOTE]
   > После добавления в фрагменте кода, необходимо ввести имена таблицы и схемы без изменения фокуса из редактора VS Code.

6. Изменить имя столбца в параметре **Column1** для **имя** и **Column2** для **расположение**.

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
   > При вводе, используйте помощи T-SQL IntelliSense.
   >   <img src="./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png" alt="TSQL IntelliSense" style="width: 500px;" />

2. Нажмите клавишу **CTRL + SHIFT + E** для выполнения команд. Два привести отображения наборов в **результаты** окна. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png" alt="Results" style="width: 300px;" />

## <a name="view-and-save-the-result"></a>Просмотреть и сохранить результаты

1. На **представление** меню, выберите **макета группы Переключить редактор** переключиться на макет вертикальные или горизонтальные разделения.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-split.png" alt="Vertical split" style="width: 500px;" />

2. Нажмите кнопку **результатов** и **сообщений** заголовок панели, чтобы сворачивать и разворачивать панели.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png" alt="Toggle Messages" style="width: 500px;" />

   > [!TIP]
   > Можно настроить поведение по умолчанию расширения mssql. См. в разделе [Настройка параметров расширения].

2. Щелкните значок сетки "Развернуть" на второй таблицы результатов, чтобы увеличить масштаб.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-maximize-grid.png" alt="Maximize grid" style="width: 500px;" />

   > [!NOTE]
   > Значок "Развернуть" отображает при сценария T-SQL имеет два или более табличной сетки результатов.

3. Откройте контекстное меню сетке с правой кнопкой мыши по сетке. 

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-grid-context-menu.png" alt="Context menu" style="width: 500px;" />

4. Выберите **выбрать все**.

5. Откройте контекстное меню для сетки и выберите **Сохранить как JSON** сохранение результата в JSON-файл.

6. Укажите имя файла для JSON-файла. Для этого учебника введите **employees.json**.

7. Убедитесь, что JSON-файл сохранен и открыть в VS Code.

   <img src="./media/sql-server-linux-develop-use-vscode/vscode-save-as-json.png" alt="Save as Json" style="width: 500px;" />

## <a name="next-steps"></a>Следующие шаги

В реальной ситуации, можно создать скрипт, который необходимо сохранить и запустить более поздней версии (для администрирования или как часть более крупного проекта разработки). В этом случае можно сохранить скрипт с **.sql** расширения.

Если вы не знакомы с T-SQL, изучите разделы [Учебник. Составление инструкций Transact-SQL] (Руководство: написание инструкций Transact-SQL) и [Справочник по Transact-SQL (ядро СУБД)] (Справочник по Transact-SQL (ядро СУБД)).

Дополнительные сведения о с помощью или способствовать низкой расширения mssql см. в разделе [вики-сайте проекта для расширения mssql].

Дополнительные сведения об использовании VS Code см. в разделе [документации Visual Studio Code](https://code.visualstudio.com/docs).

[**mssql** расширения VS Code]:https://aka.ms/mssql-marketplace
[Скачайте и установите Visual STUDIO Code]:https://code.visualstudio.com/Download
[Инструкции по.Net Core]:https://www.microsoft.com/net/core
[Управление профилями подключения]:https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles
[рекомендациями по устранению неполадок с подключением]:./sql-server-linux-troubleshooting-guide.md#connection
[Настройка сочетания клавиш]:https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts
[Учебник. Составление инструкций Transact-SQL]:https://msdn.microsoft.com/library/ms365303.aspx
[Справочник по Transact-SQL (ядро СУБД)]:https://msdn.microsoft.com/library/bb510741.aspx
[Visual Studio Code documentation]:https://code.visualstudio.com/docs
[Windows 10 универсальная среда выполнения C]:https://github.com/Microsoft/vscode-mssql/wiki/windows10-universal-c-runtime-requirement
[Настройка параметров расширения]: https://github.com/Microsoft/vscode-mssql/wiki/customize-options
[вики-сайте проекта для расширения mssql]: https://github.com/Microsoft/vscode-mssql/wiki
