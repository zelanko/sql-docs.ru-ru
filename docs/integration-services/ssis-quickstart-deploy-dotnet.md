---
title: Развертывание проекта SSIS с кодом .NET (C#) | Документы Майкрософт
ms.date: 05/21/2018
ms.topic: quickstart
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 43820f44e789330ed437c104e385090a8179a2b3
ms.sourcegitcommit: ef830f565ee07dc7d4388925cc3c86c5d2cfb4c7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2019
ms.locfileid: "74947126"
---
# <a name="deploy-an-ssis-project-with-c-code-in-a-net-app"></a>Развертывание проекта служб SSIS с кодом C# в приложении .NET

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


В этом кратком руководстве показано, как написать код C# для подключения к серверу базы данных и для развертывания проекта SSIS.

Чтобы создать приложение C#, вы можете использовать Visual Studio, Visual Studio Code или другое средство.

## <a name="prerequisites"></a>предварительные требования

Прежде чем начать, убедитесь, что у вас установлено средство Visual Studio или Visual Studio Code. Скачайте бесплатный выпуск Community средства Visual Studio или бесплатное средство Visual Studio Code на странице [скачивания Visual Studio](https://www.visualstudio.com/downloads/).

Сервер Базы данных SQL Azure прослушивает порт 1433. Если вы пытаетесь подключиться к серверу базы данных SQL Azure изнутри корпоративного брандмауэра, для успешного подключения в этом брандмауэре должен быть открыт данный порт.

## <a name="supported-platforms"></a>Поддерживаемые платформы

Сведения, приведенные в этом кратком руководстве, можно использовать для развертывания проекта SSIS на следующих платформах:

-   SQL Server в Windows.

-   База данных SQL Azure. Дополнительные сведения о развертывании и запуске пакетов в Azure см. в разделе [Перенос рабочих нагрузок SQL Server Integration Services в облако](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md).

Сведения, приведенные в этом кратком руководстве, не могут быть использованы для развертывания пакета SSIS на SQL Server в Linux. Дополнительные сведения о запуске пакетов на Linux см. в разделе [Извлечение, преобразование и загрузка данных в Linux с помощью служб SSIS](../linux/sql-server-linux-migrate-ssis.md).

## <a name="for-azure-sql-database-get-the-connection-info"></a>Получение сведений о подключении для базы данных SQL Azure

Для развертывания проекта в базе данных SQL Azure вам нужны сведения, необходимые для подключения к базе данных каталога служб SSIS (SSISDB). В описанных ниже процедурах вам потребуется полное имя сервера и имя для входа.

1. Войдите на [портал Azure](https://portal.azure.com/).
2. Выберите **Базы данных SQL** в меню слева, а затем на странице **Базы данных SQL** — базу данных SSISDB. 
3. На странице **Обзор** для базы данных просмотрите полное имя сервера. Чтобы увидеть параметр **Щелкните, чтобы скопировать**, наведите указатель мыши на имя сервера. 
4. Если вы забыли данные для входа на сервер Базы данных SQL Azure, перейдите на соответствующую страницу, чтобы просмотреть имя администратора сервера. При необходимости вы можете сбросить пароль.
5. Щелкните **Показать строки подключения к базам данных**.
6. Просмотрите полную строку подключения **ADO.NET**. В примере кода также можно использовать `SqlConnectionStringBuilder`, чтобы воссоздать эту строку подключения с указанными вами параметрами.

## <a name="supported-authentication-method"></a>Поддерживаемые методы проверки подлинности

См. [методы проверки подлинности для развертывания](ssis-quickstart-deploy-ssms.md#authentication-methods-for-deployment).

## <a name="create-a-new-visual-studio-project"></a>Создание проекта Visual Studio

1. В Visual Studio выберите **Файл**, **Создать**, **Проект**. 
2. В диалоговом окне **Создание проекта** разверните узел **Visual C#** .
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
using System;
using System.Data.SqlClient;
using System.IO;

namespace deploy_ssis_project
{
    class Program
    {
        static void Main(string[] args)
        {
            // Variables
            string targetServerName = "localhost";
            string targetFolderName = "Project1Folder";
            string projectName = "Integration Services Project1";
            string projectFilePath = @"C:\Projects\Integration Services Project1\Integration Services Project1\bin\Development\Integration Services Project1.ispac";

            // Create a connection to the server
            string sqlConnectionString = "Data Source=" + targetServerName +
                ";Initial Catalog=master;Integrated Security=SSPI;";
            SqlConnection sqlConnection = new SqlConnection(sqlConnectionString);

            // Create the Integration Services object
            IntegrationServices integrationServices = new IntegrationServices(sqlConnection);

            // Get the Integration Services catalog
            Catalog catalog = integrationServices.Catalogs["SSISDB"];

            // Create the target folder
            CatalogFolder folder = new CatalogFolder(catalog,
                targetFolderName, "Folder description");
            folder.Create();

            Console.WriteLine("Deploying " + projectName + " project.");

            byte[] projectFile = File.ReadAllBytes(projectFilePath);
            folder.DeployProject(projectName, projectFile);

            Console.WriteLine("Done.");
        }
    }
}
```

## <a name="run-the-code"></a>Выполнение кода

1. Чтобы запустить приложение, нажмите клавишу **F5**.
2. В среде SSMS убедитесь, что проект был развернут.

## <a name="next-steps"></a>Дальнейшие действия
- Рассмотрите другие варианты развертывания пакета.
    - [Развертывание пакета служб SSIS с помощью SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Развертывание пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Развертывание пакета служб SSIS из командной строки](./ssis-quickstart-deploy-cmdline.md)
    - [Развертывание пакета служб SSIS с помощью PowerShell](ssis-quickstart-deploy-powershell.md)
- Выполните развернутый пакет. Для выполнения пакета можно использовать различные средства и языки. Дополнительные сведения см. в следующих статьях:
    - [Выполнение пакета служб SSIS с помощью SSMS](./ssis-quickstart-run-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Выполнение пакета служб SSIS с помощью Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Выполнение пакета служб SSIS из командной строки](./ssis-quickstart-run-cmdline.md)
    - [Выполнение пакета служб SSIS с помощью PowerShell](ssis-quickstart-run-powershell.md)
    - [Выполнение пакета служб SSIS с помощью C#](./ssis-quickstart-run-dotnet.md) 
