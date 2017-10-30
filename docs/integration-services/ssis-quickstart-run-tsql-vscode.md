---
title: "Запустить пакет служб SSIS с помощью Transact-SQL (VS Code) | Документы Microsoft"
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
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: a912bf7f7944d4af3d41c5596e67aa77f3214112
ms.contentlocale: ru-ru
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-visual-studio-code-with-transact-sql"></a>Запустить пакет служб SSIS из кода Visual Studio с помощью Transact-SQL
В этом кратком руководстве показано, как использовать Visual Studio Code для подключения к базе данных каталога служб SSIS, а затем использовать инструкции Transact-SQL для выполнения пакета служб SSIS, сохраненные в каталоге служб SSIS.

Кода Visual Studio — это редактор кода для Windows, macOS и Linux, которая поддерживает расширения, включая `mssql` расширения для подключения к Microsoft SQL Server, базы данных SQL Azure или хранилище данных SQL Azure. Дополнительные сведения о VS Code см. в разделе [Visual Studio Cod](https://code.visualstudio.com/).

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, убедитесь, что установлена последняя версия кода Visual Studio и загрузить `mssql` расширения. Чтобы загрузить эти инструменты, содержатся на следующих страницах:
-   [Скачать Visual Studio Code](https://code.visualstudio.com/Download)
-   [расширение MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="set-language-mode-to-sql-in-vs-code"></a>Укажите режим языковой SQL в VS Code

Чтобы включить `mssql` команды и T-SQL IntelliSense, указывает режим языка задается **SQL** в код Visual Studio.

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

   | Настройка       | Предлагаемое значение | Дополнительные сведения |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Имя сервера** | Полное имя сервера | При подключении к серверу базы данных SQL Azure, называется в следующем формате: `<server_name>.database.windows.net`. |
   | **Имя базы данных** | **SSISDB** | Имя базы данных, к которому выполняется подключение. |
   | **Проверка подлинности** | Имя входа SQL| Это краткое руководство использует проверку подлинности SQL. |
   | **Имя пользователя** | Учетная запись администратора сервера | Это учетная запись, указанную при создании сервера. |
   | **Пароль (имя входа SQL)** | Пароль для учетной записи администратора сервера | Это пароль, указанный при создании сервера. |
   | **Сохранить пароль?** | Да или нет | Если вы не хотите вводить пароль каждый раз, выберите "Да". |
   | **Введите имя для этого профиля** | Имя профиля, такие как **mySSISServer** | Имя сохраненного профиля пропускной способностью подключения на последующих входов в систему. | 

5. Нажмите клавишу **ESC** клавишу, чтобы закрыть информационное сообщение, информирующее о том, что профиль создан и подключены.

6. Проверки подключения в строке состояния.

## <a name="run-the-t-sql-code"></a>Выполнение кода T-SQL
Выполните следующий код Transact-SQL для выполнения пакета служб SSIS.

1. В **редактор** окно, введите следующий запрос в пустое окно запроса. (Данный пример кода является код, сгенерированный **сценарий** в диалоговом окне **выполнение пакета** диалоговое окно в среде SSMS.)

2. Обновите значения параметров в `catalog.create_execution` хранимой процедуры для вашей системы.

3. Нажмите клавишу **CTRL + SHIFT + E** для выполнения кода и выполнение пакета.

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
- Рассмотрите другие возможности для выполнения пакета.
    - [Запустить пакет служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполните пакет служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнить пакет служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Запустить пакет служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 

