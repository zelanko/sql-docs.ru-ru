---
title: "Развертывание проекта служб SSIS с помощью Transact-SQL (VS Code) | Документы Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: dd20fe12af6f1dcaf378d737961bc2ba354aabe5
ms.openlocfilehash: 2dc6de798ca76b43627a3c381fe628506c3e7480
ms.contentlocale: ru-ru
ms.lasthandoff: 10/04/2017

---
# <a name="deploy-an-ssis-project-from-visual-studio-code-with-transact-sql"></a>Развертывание проекта служб SSIS из кода Visual Studio с помощью Transact-SQL
В этом кратком руководстве показано, как использовать Visual Studio Code для подключения к базе данных каталога служб SSIS, а затем использовать инструкции Transact-SQL для развертывания проекта служб SSIS в каталоге служб SSIS.

> [!NOTE]
> Метод, описанный в этой статье не доступен, при подключении к серверу базы данных SQL Azure с VS Code. `catalog.deploy_project` Хранимая процедура ожидает, что путь к `.ispac` файл в локальной (локально) файловой системы.

Кода Visual Studio — это редактор кода для Windows, macOS и Linux, которая поддерживает расширения, включая `mssql` расширения для подключения к Microsoft SQL Server, базы данных SQL Azure или хранилище данных SQL Azure. Дополнительные сведения о VS Code см. в разделе [кода Visual Studio](https://code.visualstudio.com/).

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, убедитесь, что установлена последняя версия кода Visual Studio и загрузить `mssql` расширения. Чтобы загрузить эти инструменты, содержатся на следующих страницах:
-   [Скачать Visual Studio Code](https://code.visualstudio.com/Download)
-   [расширение MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="set-language-mode-to-sql-in-vs-code"></a>Укажите режим языковой SQL в VS Code

Чтобы включить `mssql` команды и T-SQL IntelliSense, режим языка **SQL** в код Visual Studio.

1. Откройте Visual Studio Code и затем открыть новое окно. 

2. Нажмите кнопку **обычный текст** в правом нижнем углу строки состояния.
 
3. В **режим выбора языка** раскрывающееся меню, откроется, выберите или введите **SQL**и нажмите клавишу **ввод** для установки режима языка SQL. 

## <a name="connect-to-the-ssis-catalog-database"></a>Подключения к базе данных каталога служб SSIS

Используйте Visual Studio Code для установления соединения в каталоге служб SSIS.

> [!IMPORTANT]
> Прежде чем продолжить, убедитесь, что у сервера, базы данных и учетные данные готовы. При изменении фокуса ввода с кодом Visual Studio после начала ввода данных профиля подключения, необходимо перезагрузить для создания профиля подключения.

1. В VS Code нажмите **CTRL + SHIFT + P** (или **F1**) для открытия в палитру команд.

2. Тип **sqlcon** и нажмите клавишу **ввод**.

3. Нажмите клавишу **ввод** установите **создать профиль подключения**. Этот шаг создает профиль подключения для экземпляра SQL Server.

4. Следуйте инструкциям на экране, чтобы задать свойства соединения для нового профиля подключения. После ввода каждого значения, нажмите клавишу **ввод** для продолжения. 

   | Настройка       | Предлагаемое значение | Дополнительные сведения |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Имя сервера** | Полное имя сервера |  |
   | **Имя базы данных** | **SSISDB** | Имя базы данных, к которому выполняется подключение. |
   | **Проверка подлинности** | Имя входа SQL| Это краткое руководство использует проверку подлинности SQL. |
   | **Имя пользователя** | Учетная запись администратора сервера | Это учетная запись, указанную при создании сервера. |
   | **Пароль (имя входа SQL)** | Пароль для учетной записи администратора сервера | Это пароль, указанный при создании сервера. |
   | **Сохранить пароль?** | Да или нет | Если вы не хотите вводить пароль каждый раз, выберите "Да". |
   | **Введите имя для этого профиля** | Имя профиля, такие как **mySSISServer** | Имя сохраненного профиля пропускной способностью подключения на последующих входов в систему. | 

5. Нажмите клавишу **ESC** клавишу, чтобы закрыть информационное сообщение, информирующее о том, что профиль создан и подключены.

6. Проверки подключения в строке состояния.

## <a name="run-the-t-sql-code"></a>Выполнение кода T-SQL
Выполните следующий код Transact-SQL для развертывания проекта служб SSIS.

1. В **редактор** окно, введите следующий запрос в пустое окно запроса.

2. Обновите значения параметров в `catalog.deploy_project` хранимой процедуры для вашей системы.

3. Нажмите клавишу **CTRL + SHIFT + E** для выполнения кода и развернуть проект.

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
- Рассмотрите другие возможности для развертывания пакета.
    - [Развертывание пакета служб SSIS с помощью SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Развертывание пакета служб SSIS из командной строки](./ssis-quickstart-deploy-cmdline.md)
    - [Развертывание пакета служб SSIS с помощью PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Развертывание пакета служб SSIS с помощью C#](./ssis-quickstart-deploy-dotnet.md) 
- Выполнения развернутого пакета. Чтобы запустить пакет, можно выбрать несколько средств и языков. Дополнительные сведения см. в следующих статьях:
    - [Запустить пакет служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполните пакет служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнить пакет служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Запустить пакет служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 

