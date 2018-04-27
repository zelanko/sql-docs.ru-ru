---
title: Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code) | Документы Майкрософт
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 102327ecc6357e6e1f5dcfe3cd0a59f5c37a330a
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="run-an-ssis-package-from-visual-studio-code-with-transact-sql"></a>Выполнение пакета служб SSIS из Visual Studio Code с помощью Transact-SQL
В этом кратком руководстве демонстрируется использование Visual Studio Code для подключения к базе данных каталога SSIS и последующее использование инструкций Transact-SQL для запуска пакета служб SSIS, хранящегося в каталоге SSIS.

Visual Studio Code — это редактор кода для Windows, macOS и Linux, который поддерживает расширения, в том числе расширение `mssql` для подключения к Microsoft SQL Server, базе данных SQL Azure или хранилищу данных SQL Azure. Дополнительные сведения о Visual Studio Code см. на странице [Visual Studio Code](https://code.visualstudio.com/).

## <a name="prerequisites"></a>предварительные требования

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
   | **Имя сервера** | Полное имя сервера | При подключении к серверу базы данных SQL Azure используйте следующий формат имени: `<server_name>.database.windows.net`. |
   | **Имя базы данных** | **SSISDB** | Имя базы данных, с которой необходимо установить соединение. |
   | **Проверка подлинности** | Имя входа SQL| В этом кратком руководстве используется проверка подлинности SQL. |
   | **User name** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
   | **Пароль (имя входа SQL)** | Пароль для учетной записи администратора сервера | Это пароль, который был указан при создании сервера. |
   | **Сохранить пароль?** | "Да" или "Нет". | Чтобы каждый раз вводить пароль, выберите "Да". |
   | **Введите имя для этого профиля** | Имя профиля, например **mySSISServer** | Сохранив имя профиля, можно будет быстрее подключаться при последующих операциях входа в систему. | 

5. Чтобы закрыть информационное сообщение о том, что профиль создан и подключен, нажмите клавишу **ESC**.

6. Проверьте состояние подключения в строке состояния.

## <a name="run-the-t-sql-code"></a>Выполнение кода T-SQL
Чтобы запустить пакет SSIS, выполните приведенный ниже код Transact-SQL.

1. В окне **Редактор** введите указанный ниже запрос в пустом окне запроса. (Этот код создается параметром **Скрипт** в диалоговом окне **Выполнение пакета** в SQL Server Management Studio.)

2. Обновите значения параметров в хранимой процедуре `catalog.create_execution` так, чтобы они соответствовали вашей системе.

3. Чтобы выполнить код и запустить пакет, нажмите клавиши **CTRL+SHIFT+E**.

```sql
Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx',
    @execution_id=@execution_id OUTPUT,
    @folder_name=N'Deployed Projects',
      @project_name=N'Integration Services Project1',
    @use32bitruntime=False,
      @reference_id=Null
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,
    @object_type=50,
      @parameter_name=N'LOGGING_LEVEL',
      @parameter_value=@var0
EXEC [SSISDB].[catalog].[start_execution] @execution_id
GO
```

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие варианты выполнения пакета.
    - [Выполнение пакета служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполнение пакета служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Выполнение пакета служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 
