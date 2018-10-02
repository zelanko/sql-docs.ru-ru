---
title: Выполнение проекта SSIS с кодом .NET (C#) | Документы Майкрософт
ms.date: 05/21/2018
ms.topic: quickstart
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 49fece6dd4ef883272160f035a308cb7245bdc09
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718562"
---
# <a name="run-an-ssis-package-with-c-code-in-a-net-app"></a>Выполнение пакета служб SSIS с кодом C# в приложении .NET
В этом кратком руководстве показано, как написать код C# для подключения к серверу базы данных и для выполнения пакета SSIS.

Чтобы создать приложение C#, вы можете использовать Visual Studio, Visual Studio Code или другое средство.

## <a name="prerequisites"></a>предварительные требования

Прежде чем начать, убедитесь, что у вас установлено средство Visual Studio или Visual Studio Code. Скачайте бесплатный выпуск Community средства Visual Studio или бесплатное средство Visual Studio Code на странице [скачивания Visual Studio](https://www.visualstudio.com/downloads/).

Сервер базы данных SQL Azure прослушивает порт 1433. Если вы пытаетесь подключиться к серверу базы данных SQL Azure изнутри корпоративного брандмауэра, для успешного подключения в этом брандмауэре должен быть открыт данный порт.

## <a name="for-azure-sql-database-get-the-connection-info"></a>Получение сведений о подключении для базы данных SQL Azure

Для запуска пакета в базе данных SQL Azure вам нужны сведения, необходимые для подключения к базе данных каталога служб SSIS (SSISDB). В описанных ниже процедурах вам потребуется полное имя сервера и имя для входа.

1. Войдите на [портал Azure](https://portal.azure.com/).
2. Выберите **Базы данных SQL** в меню слева, а затем на странице **Базы данных SQL** — базу данных SSISDB. 
3. На странице **Обзор** для базы данных просмотрите полное имя сервера. Чтобы увидеть параметр **Щелкните, чтобы скопировать**, наведите указатель мыши на имя сервера. 
4. Если вы забыли учетные данные входа на сервер базы данных SQL Azure, перейдите на страницу этого сервера, чтобы узнать имя его администратора. При необходимости вы можете сбросить пароль.
5. Щелкните **Показать строки подключения к базам данных**.
6. Просмотрите полную строку подключения **ADO.NET**. В примере кода также можно использовать `SqlConnectionStringBuilder`, чтобы воссоздать эту строку подключения с указанными вами параметрами.

## <a name="create-a-new-visual-studio-project"></a>Создание проекта Visual Studio

1. В Visual Studio выберите **Файл**, **Создать**, **Проект**. 
2. В диалоговом окне **Создание проекта** разверните узел **Visual C#**.
3. Выберите **Консольное приложение** и введите *run_ssis_project* в качестве имени проекта.
4. Нажмите кнопку **ОК**, чтобы создать и открыть проект в Visual Studio.

## <a name="add-references"></a>Добавление ссылок
1. В обозревателе решений щелкните правой кнопкой мыши папку **Ссылки** и выберите **Добавить ссылку**. Открывается диалоговое окно **Диспетчер ссылок**.
2. В окне **Диспетчер ссылок** разверните узел **Сборки** и выберите **Расширения**.
3. Выберите следующие две ссылки для добавления:
    -   Microsoft.SqlServer.Management.Sdk.Sfc
    -   Microsoft.SqlServer.Smo
4. Нажмите кнопку **Обзор**, чтобы добавить ссылку на **Microsoft.SqlServer.Management.IntegrationServices**. (Эта сборка устанавливается только в глобальный кэш сборок.) Открывается диалоговое окно **Выберите файлы, на которые нужно установить ссылки**.
5. В диалоговом окне **Выберите файлы, на которые нужно установить ссылки** перейдите в папку глобального кэша сборок, содержащую нужную сборку. Обычно это папка `C:\Windows\assembly\GAC_MSIL\Microsoft.SqlServer.Management.IntegrationServices\14.0.0.0__89845dcd8080cc91`.
6. Выберите сборку (DLL-файл) в папке и нажмите кнопку **Добавить**.
7. Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Диспетчер ссылок** и добавить три ссылки. Чтобы убедиться, что ссылки на месте, проверьте список **Ссылки** в обозревателе решений.

## <a name="add-the-c-code"></a>Добавление кода C# 
1. Откройте **Program.cs**.

2. Замените содержимое **Program.cs** приведенным ниже кодом. Добавьте соответствующие значения для сервера, базы данных, пользователя и пароля.

> [!NOTE]
> В следующем примере используется проверка подлинности Windows. Чтобы использовать проверку подлинности SQL Server, замените аргумент `Integrated Security=SSPI;` на `User ID=<user name>;Password=<password>;`. Если вы подключаетесь к серверу базы данных SQL Azure, вы не можете использовать проверку подлинности Windows.


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

## <a name="run-the-code"></a>Запуск кода

1. Чтобы запустить приложение, нажмите клавишу **F5**.
2. Убедитесь, что пакет выполняется правильно, а затем закройте окно приложения.

## <a name="next-steps"></a>Следующие шаги
- Рассмотрите другие варианты выполнения пакета.
    - [Выполнение пакета служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполнение пакета служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
