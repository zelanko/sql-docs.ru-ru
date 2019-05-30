---
title: С помощью расширения mssql Visual Studio Code для SQL Server
titleSuffix: SQL Server
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
ms.openlocfilehash: 3643e66e190ec1b45961f36af471498a56924cb0
ms.sourcegitcommit: 02df4e7965b2a858030bb508eaf8daa9bc10b00b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66265379"
---
# <a name="use-visual-studio-code-to-create-and-run-transact-sql-scripts"></a>Использование Visual Studio Code для создания и выполнения скриптов Transact-SQL

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье показано, как использовать **mssql** расширения для Visual Studio Code для разработки баз данных SQL Server. Поскольку Visual Studio Code является кроссплатформенной, можно использовать **mssql** расширения в Linux, macOS и Windows.

## <a name="install-and-start-visual-studio-code"></a>Установите и запустите Visual Studio Code

Visual Studio Code — это редактор кода между различными платформами, графические, который поддерживает расширения.

1. [Скачайте и установите Visual Studio Code](https://code.visualstudio.com/) на вашем компьютере.

1. Запустите Visual Studio Code.

   >[!NOTE]
   >Если Visual Studio Code не запускается, когда вы подключены через сеанс удаленного рабочего стола xrdp, см. в разделе [VS Code, не работает в Ubuntu, при подключении по протоколу XRDP](https://github.com/Microsoft/vscode/issues/3451).

## <a name="install-the-mssql-extension"></a>Установка расширения mssql

[Расширение mssql для Visual Studio Code](https://aka.ms/mssql-marketplace) позволяет подключаться к SQL Server, запрос с помощью Transact-SQL (T-SQL) и просмотреть результаты.

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

   > [!NOTE]
   > Если это в первый раз вы использовали расширения, расширение устанавливает вспомогательных средств SQL Server.

Если открыть существующий файл, имеющий *.sql* расширение файла, языковой режим автоматически присваивается SQL.  

## <a name="connect-to-sql-server"></a>Подключение к SQL Server

Выполните следующие действия, чтобы создать профиль подключения и подключиться к SQL Server.

1. Нажмите клавишу **Ctrl**+**Shift**+**P** или **F1** открыть **палитру команд**. 

1. Тип *sql* для отображения mssql команд или тип *sqlcon*, а затем выберите **MS SQL: Подключение** из раскрывающегося списка.

   ![команды MSSQL](./media/sql-server-linux-develop-use-vscode/vscode-commands.png)

   >[!NOTE]
   >Файл SQL, таких как пустой файл SQL, который вы создали, фокус должен быть в редакторе кода перед выполнением команды mssql.

1. Выберите **MS SQL: Управление профилями подключения** команды.

1. Затем выберите **создать** для создания нового профиля подключения для SQL Server.

1. Следуйте инструкциям на экране, чтобы задать свойства для нового профиля подключения. После указания каждого значения, нажмите клавишу **ввод** для продолжения.

   | Свойства подключения | Описание |
   |---|---|
   | **Имя сервера или строка подключения ADO** | Укажите имя экземпляра SQL Server. Используйте *localhost* для подключения к экземпляру SQL Server на локальном компьютере. Чтобы подключиться к удаленному серверу SQL Server, введите имя целевого SQL Server, или его IP-адрес. Чтобы подключиться к контейнеру SQL Server, укажите IP-адрес контейнера хост-компьютере. Если вам нужно указать порт, используйте запятую, чтобы отделить его от имени. Например, для сервера прослушивает порт 1401, введите `<servername or IP>,1401`.<br/><br/>В качестве альтернативы можно ввести строку подключения ADO для своей базы данных. |
   | **Имя базы данных** (необязательно) | База данных, который вы хотите использовать. Чтобы подключиться к базе данных по умолчанию, не указывайте имя базы данных. |
   | **Тип проверки подлинности** | Выберите либо **интегрированной** или **имя входа SQL**. |
   | **Имя пользователя** | Если вы выбрали **имя входа SQL**, введите имя пользователя, имеющего доступ к базе данных на сервере. |
   | **Пароль** | Введите пароль для указанного пользователя. |
   | **Сохранить пароль** | Нажмите клавишу **ввод** для выбора **Да** и сохранять пароль. Выберите **нет** запрашивается пароль каждый раз, используется профиль подключения. |
   | **Имя профиля** (необязательно) | Введите имя для профиля подключения, такие как *профиль localhost*. |

   После ввода всех значений и выберите **ввод**, Visual Studio Code создает профиль подключения и подключается к SQL Server.

   > [!TIP]
   > Если подключение отсутствует, попробуйте для диагностики проблемы из сообщения об ошибке в **вывода** панели в Visual Studio Code. Чтобы открыть **выходные данные** панели, выберите **представление** > **вывода**. Кроме того, просмотрите [рекомендации по устранению неполадок подключения](./sql-server-linux-troubleshooting-guide.md#connection).

1. Проверка подключения в нижней строке состояния.

   ![Состояние подключения](./media/sql-server-linux-develop-use-vscode/vscode-connection-status.png)

В качестве альтернативы к предыдущим шагам, можно также создавать и изменять профили подключения в файле параметров пользователя (*settings.json*). Чтобы открыть файл параметров, выберите **файл** > **предпочтения** > **параметры**. Дополнительные сведения см. в разделе [управления профилями подключения](https://github.com/Microsoft/vscode-mssql/wiki/manage-connection-profiles).

## <a name="create-a-sql-database"></a>Создание базы данных SQL

1. В новый файл SQL, который был запущен ранее, введите *sql* для отображения списка фрагментов кода для редактирования. 

   ![Фрагменты кода SQL](./media/sql-server-linux-develop-use-vscode/vscode-sql-snippets.png)

1. Выберите **sqlCreateDatabase**.

1. В приведенном фрагменте введите `TutorialDB` для замены «DatabaseName»:

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
   > Вы можете настроить сочетания клавиш для команды mssql. См. в разделе [Настройка клавиш](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts).

## <a name="create-a-table"></a>Создание таблицы

1. Удалите содержимое окна редактора кода.

1. Нажмите клавишу **Ctrl**+**Shift**+**P** или **F1** открыть **палитру команд**. 

1. Тип *sql* для отображения mssql команд или тип *sqluse*, а затем выберите **MS SQL: Использовать базу данных** команды.

1. Выберите новый **TutorialDB** базы данных. 

   ![Использование базы данных](./media/sql-server-linux-develop-use-vscode/vscode-use-database.png)

1. В редакторе кода введите *sql* для отображения фрагменты кода, выберите **sqlCreateTable**, а затем нажмите клавишу **ввод**.

1. В приведенном фрагменте введите `Employees` имя таблицы.

1. Нажмите клавишу **вкладке** перейти к следующему полю, а затем введите `dbo` для имени схемы.

1. Замените определения столбцов со следующими столбцами:

   ```sql
   EmployeesId INT NOT NULL PRIMARY KEY,
   Name [NVARCHAR](50)  NOT NULL,
   Location [NVARCHAR](50)  NOT NULL
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

   При вводе, T-SQL IntelliSense помогает для выполнения инструкций:

   ![T-SQL IntelliSense](./media/sql-server-linux-develop-use-vscode/vscode-intellisense.png)

   > [!TIP]
   > Расширение mssql также содержит команды для создания инструкций INSERT и SELECT. Они не использовались в предыдущем примере.

1. Нажмите клавишу **Ctrl**+**Shift**+**E** для выполнения команд. Два привести отображения наборов в **результаты** окна. 

   ![Результаты](./media/sql-server-linux-develop-use-vscode/vscode-result-grid.png)

## <a name="view-and-save-the-result"></a>Просмотреть и сохранить результаты

1. Выберите **представление** > **редактор макета** > **перевернуть макета** переключиться на макет вертикальные или горизонтальные разделения.

1. Выберите **результатов** и **сообщений** панели заголовки для свертывания и развертывания панелей.

   ![Переключить заголовки](./media/sql-server-linux-develop-use-vscode/vscode-toggle-messages-pannel.png)

   > [!TIP]
   > Можно настроить поведение по умолчанию расширения mssql. См. в разделе [настройки параметров расширения](https://github.com/Microsoft/vscode-mssql/wiki/customize-options).

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

Если вы не знакомы с T-SQL, см. в разделе [руководства: Написание инструкций Transact-SQL](https://docs.microsoft.com/sql/t-sql/tutorial-writing-transact-sql-statements) и [Справочник по Transact-SQL (ядро СУБД)](https://docs.microsoft.com/sql/t-sql/language-reference).

Дополнительные сведения о с помощью или способствовать низкой расширения mssql см. в разделе [вики-сайте проекта расширения mssql](https://github.com/Microsoft/vscode-mssql/wiki).

Дополнительные сведения об использовании Visual Studio Code см. в разделе [документации Visual Studio Code](https://code.visualstudio.com/docs).