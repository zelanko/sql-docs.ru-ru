---
title: Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code) | Документы Майкрософт
ms.date: 05/21/2018
ms.topic: quickstart
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5533f3425cd301b6d69904d346031c4143870f88
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921865"
---
# <a name="run-an-ssis-package-from-visual-studio-code-with-transact-sql"></a>Выполнение пакета служб SSIS из Visual Studio Code с помощью Transact-SQL

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


В этом кратком руководстве демонстрируется использование Visual Studio Code для подключения к базе данных каталога SSIS и последующее использование инструкций Transact-SQL для запуска пакета служб SSIS, хранящегося в каталоге SSIS.

Visual Studio Code — это редактор кода для Windows, macOS и Linux, который поддерживает расширения, в том числе расширение `mssql` для подключения к Microsoft SQL Server, базе данных SQL Azure или хранилищу данных SQL Azure. Дополнительные сведения о Visual Studio Code см. на странице [Visual Studio Code](https://code.visualstudio.com/).

## <a name="prerequisites"></a>предварительные требования

Прежде чем приступить к работе, нужно установить последнюю версию Visual Studio Code и загрузить расширение `mssql`. Скачать эти средства можно на следующих страницах:
-   [Скачать Visual Studio Code](https://code.visualstudio.com/Download)
-   [Расширение mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="supported-platforms"></a>Поддерживаемые платформы

Сведения, приведенные в этом кратком руководстве, можно использовать для выполнения пакета SSIS на следующих платформах:

-   SQL Server в Windows.

-   База данных SQL Azure. Дополнительные сведения о развертывании и запуске пакетов в Azure см. в разделе [Перенос рабочих нагрузок SQL Server Integration Services в облако](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md).

Сведения, приведенные в этом кратком руководстве, не могут быть использованы для выполнения пакета SSIS в Linux. Дополнительные сведения о запуске пакетов на Linux см. в разделе [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](../linux/sql-server-linux-migrate-ssis.md).

## <a name="set-language-mode-to-sql-in-vs-code"></a>Выбор языкового режима SQL в Visual Studio Code

Чтобы иметь возможность выполнять команды `mssql` и пользоваться технологией IntelliSense для T-SQL, выберите в Visual Studio Code языковой режим **SQL**.

1. Откройте редактор Visual Studio Code, а затем откройте новое окно. 

2. В правом нижнем углу строки состояния щелкните **Обычный текст**.

3. В открывшемся меню **Выберите языковой режим** выберите или введите **SQL**, а затем нажмите клавишу **ВВОД**, чтобы установить языковой режим SQL. 

## <a name="for-azure-sql-database-get-the-connection-info"></a>Получение сведений о подключении для базы данных SQL Azure

Для запуска пакета в базе данных SQL Azure вам нужны сведения, необходимые для подключения к базе данных каталога служб SSIS (SSISDB). В описанных ниже процедурах вам потребуется полное имя сервера и имя для входа.

1. Войдите на [портал Azure](https://portal.azure.com/).
2. Выберите **Базы данных SQL** в меню слева, а затем на странице **Базы данных SQL** — базу данных SSISDB. 
3. На странице **Обзор** для базы данных просмотрите полное имя сервера. Чтобы увидеть параметр **Щелкните, чтобы скопировать**, наведите указатель мыши на имя сервера. 
4. Если вы забыли данные для входа на сервер Базы данных SQL Azure, перейдите на соответствующую страницу, чтобы просмотреть имя администратора сервера. При необходимости вы можете сбросить пароль.

## <a name="connect-to-the-ssis-catalog-database"></a>Подключение к базе данных каталога SSIS

С помощью Visual Studio Code установите соединение с каталогом служб SSIS.

> [!IMPORTANT]
> Прежде чем продолжить, необходимо подготовить сведения о сервере, базе данных и имени для входа. Если вы переключитесь из окна Visual Studio Code на другое окно после того, как начнете вводить сведения о профиле подключения, процедуру создания профиля придется начать сначала.

1. В Visual Studio Code нажмите клавиши **CTRL+SHIFT+P** (или **F1**), чтобы открыть палитру команд.

2. Введите **sqlcon** и нажмите клавишу **ВВОД**.

3. Нажмите клавишу **ВВОД**, чтобы выбрать команду **Создать профиль подключения**. На этом шаге создается профиль подключения для экземпляра SQL Server.

4. Следуя указаниям, настройте свойства подключения для нового профиля подключения. После указания каждого значения нажимайте клавишу **ВВОД**, чтобы продолжить. 

   | Параметр       | Рекомендуемое значение | Дополнительные сведения |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Имя сервера** | Полное имя сервера | При подключении к серверу базы данных SQL Azure используйте следующий формат имени: `<server_name>.database.windows.net`. |
   | **Имя базы данных** | **SSISDB** | Имя базы данных, с которой необходимо установить соединение. |
   | **Аутентификация** | Имя входа SQL | Используйте проверку подлинности SQL Server для подключения к SQL Server или к базе данных SQL Azure. Если вы подключаетесь к серверу базы данных SQL Azure, вы не можете использовать проверку подлинности Windows. |
   | **User name** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
   | **Пароль (имя входа SQL)** | Пароль для учетной записи администратора сервера | Это пароль, который был указан при создании сервера. |
   | **Сохранить пароль?** | "Да" или "Нет". | Чтобы каждый раз вводить пароль, выберите "Да". |
   | **Введите имя для этого профиля** | Имя профиля, например **mySSISServer** | Сохранив имя профиля, можно будет быстрее подключаться при последующих операциях входа в систему. | 

5. Чтобы закрыть информационное сообщение о том, что профиль создан и подключен, нажмите клавишу **ESC**.

6. Проверьте состояние подключения в строке состояния.

## <a name="run-the-t-sql-code"></a>Выполнение кода T-SQL
Чтобы запустить пакет SSIS, выполните приведенный ниже код Transact-SQL.

1. В окне **Редактор** введите указанный ниже запрос в пустом окне запроса. (Этот код создается параметром **Скрипт** в диалоговом окне **Выполнение пакета** в SQL Server Management Studio.)

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

## <a name="next-steps"></a>Дальнейшие действия
- Рассмотрите другие варианты выполнения пакета.
    - [Выполнение пакета служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполнение пакета служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Выполнение пакета служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 
