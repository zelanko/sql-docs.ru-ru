---
title: "Запустите проект служб SSIS с кодом .NET (C#) | Документы Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: 65a8db27af80e5cd7001e9a8777dde3c59e9c55e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-with-c-code-in-a-net-app"></a>Запустить пакет служб SSIS с кодом C# в приложении .NET
Этого краткого руководства показано, как написать код C# для подключения к серверу базы данных и запуска пакета служб SSIS.

Чтобы создать приложение C# можно использовать Visual Studio, Visual Studio Code или другого средства по своему усмотрению.

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, убедитесь, что установить Visual Studio или Visual Studio Code. Загрузите бесплатный выпуск Community edition Visual Studio или свободного кода Visual Studio, с [загрузки Visual Studio](https://www.visualstudio.com/downloads/).

> [!NOTE]
> Сервер базы данных SQL Azure прослушивает порт 1433. Если вы пытаетесь подключиться к серверу базы данных SQL Azure внутри корпоративного брандмауэра, этот порт должен быть открыт в корпоративный брандмауэр, для успешного подключения.

## <a name="get-the-connection-info-if-deployed-to-sql-database"></a>Получение сведений о соединении, если развернуто для базы данных SQL

При развертывании пакетов с базой данных SQL Azure, получите сведения о соединении, необходимые для подключения к базе данных каталога служб SSIS (SSISDB). Требуется полное имя и имя входа сведения о сервере для приведенных ниже процедурах.

1. Войдите на [портал Azure](https://portal.azure.com/).
2. Выберите **баз данных SQL** в левом меню и щелкните база данных SSISDB **баз данных SQL** страницы. 
3. На **Обзор** страниц для базы данных, просмотрите полное имя сервера. Чтобы вызвать **нажмите, чтобы скопировать** параметр, наведите на него имя сервера. 
4. Если вы забыли учетные данные входа для сервера базы данных SQL Azure, перейдите к страницы базы данных SQL server, чтобы просмотреть имя администратора сервера. При необходимости можно сбросить пароль.
5. Нажмите кнопку **Показать строки подключения базы данных**.
6. Полный **ADO.NET** строку подключения. В примере кода используется `SqlConnectionStringBuilder` воссоздать эту строку подключения с помощью значений отдельных параметров, предоставляемых вами.

## <a name="create-a-new-visual-studio-project"></a>Создайте новый проект Visual Studio

1. В Visual Studio выберите **файл**, **New**, **проекта**. 
2. В **новый проект** диалоговое окно и разверните **Visual C#**.
3. Выберите **консольного приложения** и введите *run_ssis_project* для имени проекта.
4. Нажмите кнопку **ОК** для создания и открытия нового проекта в Visual Studio.

## <a name="add-references"></a>Добавление ссылок
1. В обозревателе решений щелкните правой кнопкой мыши **ссылки** папку и выберите **добавить ссылку**. **Диспетчер ссылок** откроется диалоговое окно.
2. В **диспетчер ссылок** диалогового окна разверните **сборки** и выберите **расширения**.
3. Выберите следующие две ссылки для добавления:
    -   Microsoft.SqlServer.Management.Sdk.Sfc
    -   Microsoft.SqlServer.Smo
4. Нажмите кнопку **Обзор** кнопку, чтобы добавить ссылку на **Microsoft.SqlServer.Management.IntegrationServices**. (Эта сборка устанавливается только в глобальный кэш сборок (GAC).) **Выберите файлы для ссылки на** откроется диалоговое окно.
5. В **выберите файлы для ссылки на** диалоговом окне перейдите в папку глобального кэша СБОРОК, содержащий сборку. Обычно эта папка является `C:\Windows\assembly\GAC_MSIL\Microsoft.SqlServer.Management.IntegrationServices\14.0.0.0__89845dcd8080cc91`.
6. Выберите сборку (DLL-файл) в папку и нажмите кнопку **добавить**.
7. Нажмите кнопку **ОК** закрыть **диспетчер ссылок** диалоговое окно и добавить три ссылки. Чтобы убедиться в том, существуют ли ссылки, проверьте **ссылки** списка в обозревателе решений.

## <a name="add-the-c-code"></a>Добавьте код на C# 
1. Откройте **Program.cs**.

2. Замените содержимое **Program.cs** следующим кодом. Добавьте соответствующие значения для сервера, базы данных, пользователя и пароль.

> [!NOTE]
> Следующий пример использует проверку подлинности Windows. Чтобы использовать проверку подлинности SQL Server, замените `Integrated Security=SSPI;` аргумент с `User ID=<user name>;Password=<password>;`.


```csharp
using Microsoft.SqlServer.Management.IntegrationServices;
using System.Data.SqlClient;

namespace run_ssis_package
{
    class Program
    {
        static void Main(string[] args)
        {
            // Variables
            string targetServerName = "localhost";
            string folderName = "Project1Folder";
            string projectName = "Integration Services Project1";
            string packageName = "Package.dtsx";

            // Create a connection to the server
            string sqlConnectionString = "Data Source=" + targetServerName +
                ";Initial Catalog=master;Integrated Security=SSPI;";
            SqlConnection sqlConnection = new SqlConnection(sqlConnectionString);

            // Create the Integration Services object
            IntegrationServices integrationServices = new IntegrationServices(sqlConnection);

            // Get the Integration Services catalog
            Catalog catalog = integrationServices.Catalogs["SSISDB"];

            // Get the folder
            CatalogFolder folder = catalog.Folders[folderName];

            // Get the project
            ProjectInfo project = folder.Projects[projectName];

            // Get the package
            PackageInfo package = project.Packages[packageName];

            // Run the package
            package.Execute(false, null);

        }
    }
}
```

## <a name="run-the-code"></a>Выполнение кода

1. Чтобы запустить приложение, нажмите клавишу **F5**.
2. Убедитесь, что прогоне пакета, как ожидалось, а затем закройте окно приложения.

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие возможности для выполнения пакета.
    - [Запустить пакет служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (среда SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Запустить пакет служб SSIS с помощью Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполните пакет служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнить пакет служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)

