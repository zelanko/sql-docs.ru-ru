---
title: "Развертывание проекта служб SSIS с помощью Transact-SQL (Visual Studio Code) | Документы Майкрософт"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 41996c43919714a222fa3a453a943529315f957b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="deploy-an-ssis-project-from-visual-studio-code-with-transact-sql"></a>Развертывание проекта служб SSIS из Visual Studio Code с помощью Transact-SQL
В этом кратком руководстве демонстрируется использование Visual Studio Code для подключения к базе данных каталога SSIS и последующее использование инструкций Transact-SQL для развертывания проекта служб SSIS в каталоге SSIS.

> [!NOTE]
> Описываемый в этой статье метод недоступен при подключении к серверу базы данных SQL Azure с помощью Visual Studio Code. Хранимая процедура `catalog.deploy_project` ожидает, что путь к файлу `.ispac` находится в локальной файловой системе.

Visual Studio Code — это редактор кода для Windows, macOS и Linux, который поддерживает расширения, в том числе расширение `mssql` для подключения к Microsoft SQL Server, базе данных SQL Azure или хранилищу данных SQL Azure. Дополнительные сведения о Visual Studio Code см. на странице [Visual Studio Code](https://code.visualstudio.com/).

## <a name="prerequisites"></a>Предварительные требования

Прежде чем приступить к работе, нужно установить последнюю версию Visual Studio Code и загрузить расширение `mssql`. Скачать эти средства можно на следующих страницах:
-   [Скачать Visual Studio Code](https://code.visualstudio.com/Download)
-   [Расширение mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="set-language-mode-to-sql-in-vs-code"></a>Выбор языкового режима SQL в Visual Studio Code

Чтобы иметь возможность выполнять команды `mssql` и пользоваться технологией IntelliSense для T-SQL, выберите в Visual Studio Code языковой режим **SQL**.

1. Откройте редактор Visual Studio Code, а затем откройте новое окно. 

2. В правом нижнем углу строки состояния щелкните **Обычный текст**.
 
3. В открывшемся меню **Выберите языковой режим** выберите или введите **SQL**, а затем нажмите клавишу **ВВОД**, чтобы установить языковой режим SQL. 

## <a name="connect-to-the-ssis-catalog-database"></a>Подключение к базе данных каталога SSIS

С помощью Visual Studio Code установите соединение с каталогом служб SSIS.

> [!IMPORTANT]
> Прежде чем продолжить, необходимо подготовить сведения о сервере, базе данных и имени для входа. Если вы переключитесь из окна Visual Studio Code на другое окно после того, как начнете вводить сведения о профиле подключения, процедуру создания профиля придется начать сначала.

1. В Visual Studio Code нажмите клавиши **CTRL+SHIFT+P** (или **F1**), чтобы открыть палитру команд.

2. Введите **sqlcon** и нажмите клавишу **ВВОД**.

3. Нажмите клавишу **ВВОД**, чтобы выбрать команду **Создать профиль подключения**. На этом шаге создается профиль подключения для экземпляра SQL Server.

4. Следуя указаниям, настройте свойства подключения для нового профиля подключения. После указания каждого значения нажимайте клавишу **ВВОД**, чтобы продолжить. 

   | Настройка       | Предлагаемое значение | Дополнительные сведения |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Имя сервера** | Полное имя сервера |  |
   | **Имя базы данных** | **SSISDB** | Имя базы данных, с которой необходимо установить соединение. |
   | **Проверка подлинности** | Имя входа SQL| В этом кратком руководстве используется проверка подлинности SQL. |
   | **Имя пользователя** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
   | **Пароль (имя входа SQL)** | Пароль для учетной записи администратора сервера | Это пароль, который был указан при создании сервера. |
   | **Сохранить пароль?** | "Да" или "Нет". | Чтобы каждый раз вводить пароль, выберите "Да". |
   | **Введите имя для этого профиля** | Имя профиля, например **mySSISServer** | Сохранив имя профиля, можно будет быстрее подключаться при последующих операциях входа в систему. | 

5. Чтобы закрыть информационное сообщение о том, что профиль создан и подключен, нажмите клавишу **ESC**.

6. Проверьте состояние подключения в строке состояния.

## <a name="run-the-t-sql-code"></a>Выполнение кода T-SQL
Чтобы развернуть проект SSIS, выполните приведенный ниже код Transact-SQL.

1. В окне **Редактор** введите указанный ниже запрос в пустом окне запроса.

2. Обновите значения параметров в хранимой процедуре `catalog.deploy_project` так, чтобы они соответствовали вашей системе.

3. Чтобы выполнить код и развернуть проект, нажмите клавиши **CTRL+SHIFT+E**.

```sql
DECLARE @ProjectBinary AS varbinary(max)
DECLARE @operation_id AS bigint
SET @ProjectBinary = (SELECT * FROM OPENROWSET(BULK '<project_file_path>.ispac', SINGLE_BLOB) AS BinaryData)

EXEC catalog.deploy_project @folder_name = '<target_folder>',
    @project_name = '<project_name',
    @Project_Stream = @ProjectBinary,
    @operation_id = @operation_id out
```

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие варианты развертывания пакета.
    - [Развертывание пакета служб SSIS с помощью SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Развертывание пакета служб SSIS из командной строки](./ssis-quickstart-deploy-cmdline.md)
    - [Развертывание пакета служб SSIS с помощью PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Развертывание пакета служб SSIS с помощью C#](./ssis-quickstart-deploy-dotnet.md) 
- Выполните развернутый пакет. Для выполнения пакета можно использовать различные средства и языки. Дополнительные сведения см. в следующих статьях:
    - [Выполнение пакета служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполнение пакета служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Выполнение пакета служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 
