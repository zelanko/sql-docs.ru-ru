---
title: Развертывание проекта служб SSIS с помощью Transact-SQL (Visual Studio Code) | Документы Майкрософт
ms.date: 05/21/2018
ms.topic: quickstart
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: befa64e6c79a1f1e4fe0604014dbb7c583bf830e
ms.sourcegitcommit: ef830f565ee07dc7d4388925cc3c86c5d2cfb4c7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2019
ms.locfileid: "74947176"
---
# <a name="deploy-an-ssis-project-from-visual-studio-code-with-transact-sql"></a>Развертывание проекта служб SSIS из Visual Studio Code с помощью Transact-SQL

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


В этом кратком руководстве демонстрируется подключение к базе данных каталога SSIS в Visual Studio Code и развертывание проекта SSIS в каталоге SSIS с помощью инструкций Transact-SQL.

Visual Studio Code — это редактор кода для Windows, macOS и Linux, который поддерживает расширения, в том числе расширение `mssql` для подключения к Microsoft SQL Server, базе данных SQL Azure или хранилищу данных SQL Azure. Дополнительные сведения о Visual Studio Code см. на странице [Visual Studio Code](https://code.visualstudio.com/).

## <a name="prerequisites"></a>предварительные требования

Прежде чем приступить к работе, нужно установить последнюю версию Visual Studio Code и загрузить расширение `mssql`. Скачать эти средства можно на следующих страницах:
-   [Скачать Visual Studio Code](https://code.visualstudio.com/Download)
-   [Расширение mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="supported-platforms"></a>Поддерживаемые платформы

Сведения, приведенные в этом кратком руководстве, можно использовать для развертывания проекта SSIS на следующих платформах:

-   SQL Server в Windows.

Сведения в этом кратком руководстве неприменимы для развертывания пакета SSIS в базе данных SQL Azure. Хранимая процедура `catalog.deploy_project` ожидает, что путь к файлу `.ispac` находится в локальной файловой системе. Дополнительные сведения о развертывании и запуске пакетов в Azure см. в разделе [Перенос рабочих нагрузок SQL Server Integration Services в облако](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md).

Сведения, приведенные в этом кратком руководстве, не могут быть использованы для развертывания пакета SSIS на SQL Server в Linux. Дополнительные сведения о запуске пакетов на Linux см. в разделе [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](../linux/sql-server-linux-migrate-ssis.md).

## <a name="set-language-mode-to-sql-in-vs-code"></a>Выбор языкового режима SQL в Visual Studio Code

Чтобы иметь возможность выполнять команды `mssql` и пользоваться технологией IntelliSense для T-SQL, выберите в Visual Studio Code языковой режим **SQL**.

1. Откройте редактор Visual Studio Code, а затем откройте новое окно. 

2. В правом нижнем углу строки состояния щелкните **Обычный текст**.
 
3. В открывшемся меню **Выберите языковой режим** выберите или введите **SQL**, а затем нажмите клавишу **ВВОД**, чтобы установить языковой режим SQL. 

## <a name="supported-authentication-method"></a>Поддерживаемые методы проверки подлинности

См. [методы проверки подлинности для развертывания](ssis-quickstart-deploy-ssms.md#authentication-methods-for-deployment).

## <a name="connect-to-the-ssis-catalog-database"></a>Подключение к базе данных каталога SSIS

С помощью Visual Studio Code установите соединение с каталогом служб SSIS.

1. В Visual Studio Code нажмите клавиши **CTRL+SHIFT+P** (или **F1**), чтобы открыть палитру команд.

2. Введите **sqlcon** и нажмите клавишу **ВВОД**.

3. Нажмите клавишу **ВВОД**, чтобы выбрать команду **Создать профиль подключения**. На этом шаге создается профиль подключения для экземпляра SQL Server.

4. Следуя указаниям, настройте свойства подключения для нового профиля подключения. После указания каждого значения нажимайте клавишу **ВВОД**, чтобы продолжить. 

   | Параметр       | Рекомендуемое значение | Дополнительные сведения |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Имя сервера** | Полное имя сервера |  |
   | **Имя базы данных** | **SSISDB** | Имя базы данных, с которой необходимо установить соединение. |
   | **Аутентификация** | Имя входа SQL | |
   | **User name** | Учетная запись администратора сервера | Это учетная запись, которая была указана при создании сервера. |
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

## <a name="next-steps"></a>Дальнейшие действия
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
