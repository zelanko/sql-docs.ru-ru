---
title: Обновленные документы по службам Integration Services для SQL Server | Документы Майкрософт
description: Отрывки из недавно обновленного содержимого в документации по службам Integration Services для Microsoft SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: ssis
ms.date: 04/28/2018
ms.openlocfilehash: f1d0c96c7ee0a835c1fc1cf6db6e3cf1e03ca9d6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-integration-services-for-sql-server"></a>Новые и обновленные статьи по службам Integration Services для SQL Server



Почти каждый день корпорация Майкрософт вносит изменения в свои статьи на веб-сайте документации [Docs.Microsoft.com](http://docs.microsoft.com/). В этой статье приводятся отрывки из обновленных недавно статей, а также ссылки на новые статьи.

Статья создается программой и периодически обновляется. Отрывки из измененных статей могут иметь неидеальный формат или разметку исходной статьи. Картинки здесь не отображаются.

Последние обновления соответствуют следующему периоду времени и предметной области:



- *Даты обновлений:* &nbsp; **02.03.2018**&nbsp;–&nbsp;**28.04.2018**
- *Предметная область:* &nbsp; **Службы Integration Services для SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Недавно созданные статьи

Приведенные ниже ссылки указывают на новые статьи, которые добавлены недавно.


1. [Загрузка данных в приложение Excel или из него с помощью служб SQL Server Integration Services (SSIS)](load-data-to-from-excel-with-ssis.md)
2. [Загрузка данных из SQL Server в хранилище данных SQL Azure с помощью служб SQL Server Integration Services (SSIS)](load-data-to-sql-data-warehouse.md)
3. [Поддержка Scale Out для обеспечения высокой доступности с помощью экземпляра отказоустойчивого кластера SQL Server](scale-out/scale-out-failover-cluster-instance.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Обновленные статьи с отрывками

В этом разделе приводятся отрывки из статей, в которые недавно внесены значительные изменения.

Отрывки отображаются отдельно от соответствующего семантического контекста. Кроме того, иногда фрагмент отделяется от синтаксиса разметки, окружающей саму статью. Таким образом, эти отрывки приводятся только для общего сведения. Они позволяют понять, стоит ли вам перейти по ссылке и прочитать всю статью полностью.

По этой и другим причинам не копируйте код из этих отрывков и не воспринимайте содержание этих отрывков как однозначно верное. Вместо этого пройдите по ссылке и ознакомьтесь с фактическим текстом статьи.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Сокращенный список недавно обновленных статей

В этом сокращенном списке приводятся ссылки на все обновленные статьи, перечисленные в разделе "Отрывки".

1. [Установка служб Integration Services](#TitleNum_1)
2. [Развертывание, запуск и отслеживание пакета служб SSIS в Azure](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-install-integration-servicesinstall-windowsinstall-integration-servicesmd"></a>1. &nbsp; [Установка служб Integration Services](install-windows/install-integration-services.md)

*Обновление: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Далее](#TitleNum_2))

<!-- Source markdown line 75.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 49551f3b1138f805e6d5e0f6099a100e2f3b3e7a 97caaafc1587b2326f4c357dd5eb21f2de7d358f  (PR=5676  ,  Filename=install-integration-services.md  ,  Dirpath=docs\integration-services\install-windows\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**Полная установка служб Integration Services**


Чтобы произвести полную установку служб *{Included-Content-Goes-Here}*, выберите нужные компоненты из списка ниже:

-   **Службы Integration Services (SSIS)**. Установите службы SSIS с помощью мастера установки SQL Server. При выборе служб SSIS устанавливаются следующие компоненты:
    -   поддержка каталога SSIS в ядре СУБД SQL Server;
    -   дополнительный компонент SSIS Scale Out, который состоит из главной и рабочих ролей;
    -   32-и 64-разрядные компоненты служб SSIS;
    -   При установке служб SSIS **не** устанавливаются средства, необходимые для проектирования и разработки пакетов SSIS.
-   **Ядро СУБД SQL Server**. Установите ядро СУБД с помощью мастера установки SQL Server. При выборе ядра СУБД можно создать и разместить базу данных каталога SSIS `SSISDB`, которая служит для хранения, выполнения и мониторинга пакетов SSIS, а также управления ими.
-   **SQL Server Data Tools (SSDT)**. См. дополнительные сведения по [скачиванию SQL Server Data Tools (SSDT)]. Установив SSDT, вы сможете разрабатывать и развертывать пакеты SSIS. В составе SSDT устанавливаются следующие компоненты:
    -   средства проектирования и разработки пакетов SSIS, включая конструктор служб SSIS;
    -   только 32-разрядные компоненты служб SSIS;
    -   версия Visual Studio с ограниченными возможностями (если еще не установлен один из выпусков Visual Studio);
    -   Visual Studio Tools for Applications (VSTA), редактор скриптов, используемый задачей "Скрипт" и компонентом "Скрипт" службы SSIS;
    -   мастеры служб SSIS, включая мастер развертывания и мастер обновления пакетов;
    -   мастер импорта и экспорта SQL Server.
-   **Пакет дополнительных компонентов служб Integration Services для Azure**. Чтобы скачать и установить пакет дополнительных компонентов, перейдите на страницу [пакета дополнительных компонентов служб Microsoft SQL Server 2017 Integration Services для Azure](https://www.microsoft.com/download/details.aspx?id=54798). Установка пакета дополнительных компонентов позволяет пакетам подключаться к службам хранения и анализа данных в облаке Azure, включая следующие службы:



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-deploy-run-and-monitor-an-ssis-package-on-azurelift-shiftssis-azure-deploy-run-monitor-tutorialmd"></a>2. &nbsp; [Развертывание, запуск и отслеживание пакета служб SSIS в Azure](lift-shift/ssis-azure-deploy-run-monitor-tutorial.md)

*Обновлено: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Назад](#TitleNum_1))

<!-- Source markdown line 99.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 07f2b752818f2e786c4380fb822099190c59f302 54de9497353bac2d6a8a87e546fc6ab9e444a734  (PR=5676  ,  Filename=ssis-azure-deploy-run-monitor-tutorial.md  ,  Dirpath=docs\integration-services\lift-shift\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**Развертывание проекта с помощью PowerShell**


Чтобы развернуть проект с помощью PowerShell в базе данных SSISDB, размещенной в базе данных SQL Azure, приспособьте следующий скрипт под свои требования. Скрипт перечисляет дочерние папки в `$ProjectFilePath` и проекты в каждой дочерней папке, а затем создает те же папки в базе данных SSISDB и развертывает в них проекты.

На компьютере, где будет выполняться этот скрипт, должны быть установлены SQL Server Data Tools 17.x или среда SQL Server Management Studio.

```
**Variables**

$ProjectFilePath = "C:\<folder>"
$SSISDBServerEndpoint = "<servername>.database.windows.net"
$SSISDBServerAdminUserName = "<username>"
$SSISDBServerAdminPassword = "<password>"

**Load the IntegrationServices Assembly**

[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices") | Out-Null;

**Store the IntegrationServices Assembly namespace to avoid typing it every time**

$ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"

Write-Host "Connecting to server ..."

**Create a connection to the server**

$sqlConnectionString = "Data Source=" + $SSISDBServerEndpoint + ";User ID="+ $SSISDBServerAdminUserName +";Password="+ $SSISDBServerAdminPassword + ";Initial Catalog=SSISDB"
$sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString

**Create the Integration Services object**

$integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection

**Get the catalog**

$catalog = $integrationServices.Catalogs['SSISDB']

write-host "Enumerating all folders..."

$folders = ls -Path $ProjectFilePath -Directory

if ($folders.Count -gt 0)
{
    foreach ($filefolder in $folders)
    {
        Write-Host "Creating Folder " $filefolder.Name " ..."

        # Create a new folder
        $folder = New-Object $ISNamespace".CatalogFolder" ($catalog, $filefolder.Name, "Folder description")
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Статьи, близкие к новым или измененным статьям

Этот раздел содержит статьи, очень близкие к недавно измененным статьям из других предметных областей в общедоступном репозитории GitHub.com: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Предметные области, *содержащие* новые или недавно обновленные статьи

- [Новые + обновленные (11+6): &nbsp; &nbsp;**Углубленная аналитика для SQL** (документация)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Новые + обновленные (18+0): &nbsp;&nbsp;**Analysis Services для SQL** (документация)](../analysis-services/new-updated-analysis-services.md)
- [Новые + обновленные (218+14):  **Подключение к SQL** (документация)](../connect/new-updated-connect.md)
- [Новые + обновленные (14+0): &nbsp; &nbsp;**Ядро СУБД для SQL** (документация)](../database-engine/new-updated-database-engine.md)
- [Новые + обновленные (3+2): &nbsp; &nbsp;**Integration Services для SQL** (документация)](../integration-services/new-updated-integration-services.md)
- [Новые + обновленные (3+3): &nbsp; &nbsp;**Linux для SQL** (документация)](../linux/new-updated-linux.md)
- [Новые + обновленные (7+10): &nbsp; &nbsp;**Реляционные базы данных для SQL** (документация)](../relational-databases/new-updated-relational-databases.md)
- [Новые + обновленные (0+2): &nbsp; **&nbsp;Reporting Services для SQL** (документация)](../reporting-services/new-updated-reporting-services.md)
- [Новые + обновленные (1+3): &nbsp; &nbsp;**SQL Operations Studio** (документация)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Новые + обновленные(2+3): &nbsp; &nbsp;**Microsoft SQL Server** (документация)](../sql-server/new-updated-sql-server.md)
- [Новые + обновленные (1+1): &nbsp; &nbsp;**SQL Server Data Tools (SSDT)** (документация)](../ssdt/new-updated-ssdt.md)
- [Новые + обновленные (5+2): &nbsp; &nbsp;**SQL Server Management Studio (SSMS)** (документация)](../ssms/new-updated-ssms.md)
- [Новые + обновленные (0+2): &nbsp; &nbsp;**Transact-SQL** (документация)](../t-sql/new-updated-t-sql.md)
- [Новые + обновленные (1+1): &nbsp;**&nbsp;Инструменты для SQL** (документация)](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Предметные области, *не* содержащие новые или недавно обновленные статьи

- [Новые + обновленные (0+0):  **Analytics Platform System для SQL** (документация)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Новые + обновленные (0+0): **Data Quality Services для SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Новые + обновленные (0+0): **расширения интеллектуального анализа данных (DMX) для SQL**](../dmx/new-updated-dmx.md)
- [Новые + обновленные (0+0): документация **Master Data Services (MDS) для SQL**](../master-data-services/new-updated-master-data-services.md)
- [Новые + обновленные (0+0): **многомерные выражения (MDX) для SQL**](../mdx/new-updated-mdx.md)
- [Новые + обновленные (0+0): **ODBC (Open Database Connectivity) для SQL**](../odbc/new-updated-odbc.md)
- [Новые + обновленные (0+0): **PowerShell для SQL**](../powershell/new-updated-powershell.md)
- [Новые + обновленные (0+0): **примеры для SQL**](../samples/new-updated-samples.md)
- [Новые + обновленные (0+0): **помощник по миграции SQL Server (SSMA)**](../ssma/new-updated-ssma.md)
- [Новые + обновленные (0+0): **XQuery для SQL**](../xquery/new-updated-xquery.md)

