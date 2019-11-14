---
title: Запуск Помощник по миграции данных из командной строки
description: Сведения о запуске Помощник по миграции данных из командной строки для оценки SQL Server баз данных для миграции
ms.custom: seo-lt-2019
ms.date: 05/06/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.openlocfilehash: 3fbf2429a384ad64b1b416e3920a193d92a6c387
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056617"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Запуск Помощник по миграции данных из командной строки

В версии 2,1 и выше при установке Помощник по миграции данных также будет установлен дмакмд. exe в *% ProgramFiles%\\Помощник по миграции данных (Майкрософт)\\* . Используйте дмакмд. exe для оценки баз данных в автоматическом режиме и вывода результата в JSON-или CSV-файл. Этот метод особенно полезен при оценке нескольких баз данных или огромных баз данных. 

> [!NOTE]
> Дмакмд. exe поддерживает только выполнение оценок. В настоящее время миграция не поддерживается.

## <a name="assessments-using-the-command-line-interface-cli"></a>Оценки с помощью интерфейса командной строки (CLI)

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentSourcePlatform="SourcePlatform"]
\[/AssessmentTargetPlatform="TargetPlatform"\]
/AssessmentEvaluateRecommendations|/AssessmentEvaluateCompatibilityIssues
\[/AssessmentOverwriteResult\]
/AssessmentResultJson="file"|/AssessmentResultCsv="file"
```

|Аргумент  |Описание  | Обязательный (Y/N)
|---------|---------|---------------|
| `/help or /?`     | Использование текста справки дмакмд. exe        | Нет
|`/AssessmentName`     |   Имя проекта оценки   | Да
|`/AssessmentDatabases`     | Разделенный пробелами список строк подключения. Имя базы данных (начальный каталог) учитывает регистр. | Да
|`/AssessmentSourcePlatform`     | Исходная платформа для оценки: <br>Поддерживаемые значения для оценки: Склонпрем, Рдссклсервер (по умолчанию) <br>Поддерживаемые значения для оценки готовности к оценке: Склонпрем, Рдссклсервер (по умолчанию), Cassandra (Предварительная версия)   | Нет
|`/AssessmentTargetPlatform`     | Целевая платформа для оценки:  <br> Поддерживаемые значения для оценки: AzureSqlDatabase, Манажедсклсервер, SqlServer2012, SqlServer2014, SqlServer2016, SqlServerLinux2017 и SqlServerWindows2017 (по умолчанию)  <br> Поддерживаемые значения для оценки готовности к оценке: Манажедсклсервер (по умолчанию), CosmosDB (Предварительная версия)   | Нет
|`/AssessmentEvaluateFeatureParity`  | Выполнение правил четности для компонентов. Если исходная платформа — Рдссклсервер, оценка четности для компонентов не поддерживается для целевой платформы AzureSqlDatabase  | Нет
|`/AssessmentEvaluateCompatibilityIssues`     | Запуск правил совместимости  | Да <br> (Требуется либо Ассессментевалуатекомпатибилитиссуес, либо Ассессментевалуатерекоммендатионс.)
|`/AssessmentEvaluateRecommendations`     | Запуск рекомендаций по функциям        | Да <br> (Требуется либо Ассессментевалуатекомпатибилитиссуес, либо Ассессментевалуатерекоммендатионс)
|`/AssessmentOverwriteResult`     | Перезаписать файл результатов    | Нет
|`/AssessmentResultJson`     | Полный путь к файлу результатов JSON     | Да <br> (Требуется либо Ассессментресултжсон, либо Ассессментресултксв)
|`/AssessmentResultCsv`    | Полный путь к файлу результатов CSV   | Да <br> (Требуется либо Ассессментресултжсон, либо Ассессментресултксв)
|`/Action`    | Используйте Скурекоммендатион для получения рекомендаций по SKU, используйте Ассесстаржетреадинесс для оценки готовности к целевой службе.   | Нет
|`/SourceConnections`    | Список строк подключения, разделенных пробелами. Имя базы данных (начальный каталог) является необязательным. Если имя базы данных не указано, оцениваются все базы данных в источнике.   | Да <br> (Обязательно, если Action-"Ассесстаржетреадинесс")
|`/TargetReadinessConfiguration`    | Полный путь к XML-файлу, описывающему значения имени, исходных соединений и файла результатов.   | Да <br> (Требуется либо Таржетреадинессконфигуратион, либо Саурцеконнектионс)
|`/FeatureDiscoveryReportJson`    | Путь к отчету JSON обнаружения компонентов. Если этот файл создан, его можно использовать для повторного выполнения целевой оценки готовности без подключения к источнику. | Нет
|`/ImportFeatureDiscoveryReportJson`    | Путь к созданному ранее отчету JSON обнаружения компонентов. Этот файл будет использоваться вместо исходных соединений.   | Нет

## <a name="examples-of-assessments-using-the-cli"></a>Примеры оценок с помощью интерфейса командной строки

**Дмакмд. exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Оценка одной базы данных с использованием проверки подлинности Windows и выполнение правил совместимости**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```

**Оценка одной базы данных с помощью SQL Server проверки подлинности и выполнения рекомендаций**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;User Id=myUsername;Password=myPassword;"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**Оценка одной базы данных для целевой платформы SQL Server 2012, сохранение результатов в JSON-и CSV-файл**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="SqlServer2012"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**Оценка одной базы данных для целевой платформы SQL Azure база данных, сохранение результатов в JSON-и CSV-файл**

```
DmaCmd.exe /AssessmentName="TestAssessment" 
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="AzureSqlDatabaseV12"
/AssessmentEvaluateCompatibilityIssues /AssessmentEvaluateFeatureParity
/AssessmentOverwriteResult 
/AssessmentResultCsv="C:\\temp\\AssessmentReport.csv" 
/AssessmentResultJson="C:\\temp\\AssessmentReport.json"
```

**Оценка нескольких баз данных**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName1;Initial
Catalog=DatabaseName1;Integrated Security=true"
"Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated
Security=true" "Server=SQLServerInstanceName2;Initial
Catalog=DatabaseName3;Integrated Security=true"
/AssessmentTargetPlatform="SqlServer2016"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
/AssessmentResultJson="C:\\Results\\test2016.json"
```

**Оценка готовности целевого объекта базы данных с использованием проверки подлинности Windows**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;Integrated Security=true" 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"
```

**Оценка готовности целевого объекта базы данных с использованием проверки подлинности SQL Server**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;User Id=myUsername;Password=myPassword;" /AssessmentEvaluateRecommendations 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json" 

```

**Оценка одной базы данных для целевой платформы SQL Azure база данных, сохранение результатов в JSON-и CSV-файл**

```
DmaCmd.exe /AssessmentName="TestAssessment" 
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentSourcePlatform="SqlOnPrem"
/AssessmentTargetPlatform="AzureSqlDatabase"
/AssessmentEvaluateCompatibilityIssues /AssessmentEvaluateFeatureParity
/AssessmentOverwriteResult 
/AssessmentResultCsv="C:\\temp\\AssessmentReport.csv" 
/AssessmentResultJson="C:\\temp\\AssessmentReport.json"

```

**Оценка готовности к работе с несколькими базами данных**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/AssessmentSourcePlatform=SourcePlatform
/AssessmentTargetPlatform=TargetPlatform
/SourceConnections="Server=SQLServerInstanceName1;Initial Catalog=DatabaseName1;Integrated Security=true" "Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated Security=true" "Server=SQLServerInstanceName2;Initial Catalog=DatabaseName3;Integrated Security=true"
/AssessmentOverwriteResult  
/AssessmentResultJson="C:\Results\test2016.json"

(/AssessmentSourcePlatform and /AssessmentTargetPlatform are optional.)
```

**Оценка готовности к оценке для всех баз данных на сервере с проверкой подлинности Windows**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/SourceConnections="Server=SQLServerInstanceName;Integrated Security=true"
/AssessmentOverwriteResult
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**Оценка целевой готовности путем импорта отчета об обнаружении компонентов, созданного ранее**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/ImportFeatureDiscoveryReportJson="c:\temp\feature_report.json" 
/AssessmentOverwriteResult
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**Оценка целевой готовности путем предоставления файла конфигурации**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/TargetReadinessConfiguration=.\Config.xml
```

Содержимое файла конфигурации при использовании исходных соединений:

```
<?xml version="1.0" encoding="utf-8" ?>
<TargetReadinessConfiguration xmlns="https://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
  <AssessmentName>name</AssessmentName>
  <SourcePlatform>Source Platform</SourcePlatform> <!-- Optional. The default is SqlOnPrem -->
  <TargetPlatform>TargetPlatform</TargetPlatform> <!-- Optional. The default is ManagedSqlServer -->
  <SourceConnections>
    <SourceConnection>connection string 1</SourceConnection>
    <SourceConnection>connection string 2</SourceConnection>
    <!-- ... -->
    <SourceConnection>connection string n</SourceConnection>
  </SourceConnections>
  <AssessmentResultJson>path\to\file.json</AssessmentResultJson>
  <FeatureDiscoveryReportJson>path\to\featurediscoveryreport.json</FeatureDiscoveryReportJson>
  <OverwriteResult>true</OverwriteResult> <!-- or false -->
</TargetReadinessConfiguration>
```

Содержимое файла конфигурации при импорте отчета об обнаружении компонентов:

```
<TargetReadinessConfiguration xmlns="https://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
  <AssessmentName>name</AssessmentName>
  <ImportFeatureDiscoveryReportJson>path\to\featurediscoveryfile.json</ImportFeatureDiscoveryReportJson>
  <AssessmentResultJson>path\to\resultfile.json</AssessmentResultJson>
  <OverwriteResult>true</OverwriteResult><!-- or false -->
</TargetReadinessConfiguration>
```

## <a name="azure-sql-databasemanaged-instance-sku-recommendations-using-the-cli"></a>Рекомендации по использованию базы данных SQL Azure/SKU управляемого экземпляра с помощью интерфейса командной строки

Эти команды поддерживают рекомендации для развертывания одиночной базы данных SQL Azure и управляемого экземпляра.

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true 
```

|Аргумент  |Описание  | Обязательный (Y/N)
|---------|---------|---------------|
|`/Action=SkuRecommendation` | Выполнение оценки номера SKU с помощью командной строки DMA | Да
|`/SkuRecommendationInputDataFilePath` | Полный путь к файлу счетчика производительности, полученному с компьютера, на котором размещены базы данных | Да
|`/SkuRecommendationTsvOutputResultsFilePath` | Полный путь к файлу в формате TSV | Да <br> (Требуется путь к файлу в формате TSV или JSON или HTML)
|`/SkuRecommendationJsonOutputResultsFilePath` | Полный путь к файлу результатов JSON | Да <br> (Требуется путь к файлу в формате TSV или JSON или HTML)
|`/SkuRecommendationHtmlResultsFilePath` | Полный путь к файлу результатов в формате HTML | Да <br> (Требуется путь к файлу в формате TSV или JSON или HTML)
|`/SkuRecommendationPreventPriceRefresh` | Предотвращает обновление цены. Используйте, если выполняется в автономном режиме (например, true). | Да <br> (Выберите либо этот аргумент для статических цен, либо для получения последних цен необходимо выбрать все аргументы ниже)
|`/SkuRecommendationCurrencyCode` | Валюта, в которой отображаются цены (например, "USD") | Да <br> (Для последних цен)
|`/SkuRecommendationOfferName` | Имя предложения (например, MS-AZR-0003P). Дополнительные сведения см. на странице [сведений о предложении Microsoft Azure](https://azure.microsoft.com/support/legal/offer-details/) . | Да <br> (Для последних цен)
|`/SkuRecommendationRegionName` | Имя региона (например, "WestUS") | Да <br> (Для последних цен)
|`/SkuRecommendationSubscriptionId` | Идентификатор подписки. | Да <br> (Для последних цен)
|`/SkuRecommendationDatabasesToRecommend` | Список баз данных с разделителями-пробелами (например, "Database1" "Database2" "Database3"). В именах учитывается регистр, и их необходимо заключить в двойные кавычки. Если этот параметр опущен, для всех баз данных предоставляются рекомендации. | Нет
|`/AzureAuthenticationTenantId` | Клиент проверки подлинности. | Да <br> (Для последних цен)
|`/AzureAuthenticationClientId` | Идентификатор клиента приложения AAD, используемого для проверки подлинности. | Да <br> (Для последних цен)
|`/AzureAuthenticationInteractiveAuthentication` | Задайте значение true для всплывающего окна. | Да <br> (Для последних цен) <br>(Выберите один из трех параметров проверки подлинности — вариант 1)
|`/AzureAuthenticationCertificateStoreLocation` | Задайте расположение хранилища сертификатов (например, "CurrentUser"). | Да <br>(Для последних цен) <br> (Выберите один из трех параметров проверки подлинности — вариант 2)
|`/AzureAuthenticationCertificateThumbprint` | Задайте для параметра значение отпечаток сертификата. | Да <br> (Для последних цен) <br>(Выберите один из трех параметров проверки подлинности — вариант 2)
|`/AzureAuthenticationToken` | Задайте для маркера сертификата. | Да <br> (Для последних цен) <br>(Выберите один из трех параметров проверки подлинности — вариант 3)

## <a name="examples-of-sku-assessments-using-the-cli"></a>Примеры оценки SKU с помощью интерфейса командной строки

**Дмакмд. exe**

`Dmacmd.exe /? or DmaCmd.exe /help`

**Рекомендации по SKU базы данных SQL Azure/MI с обновлением цен (получение последних цен) — интерактивная проверка подлинности** 

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationInteractiveAuthentication=true 
```

**Рекомендации по SKU базы данных SQL Azure/MI с обновлением цен (получение последних цен) — проверка подлинности сертификата**

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationCertificateStoreLocation=<Your Certificate Store Location>
/AzureAuthenticationCertificateThumbprint=<Your Certificate Thumbprint>  
```

**Рекомендации по SKU и MI базы данных SQL Azure с обновлением цен (получение последних цен) — проверка подлинности маркеров и указание баз данных для получения рекомендаций**
  
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationDatabasesToRecommend=“TPCDS1G,EDW_3G,TPCDS10G”
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationToken=<Your Authentication Token> 
```

**Рекомендация по SKU базы данных SQL Azure (MI) без обновления цены (используйте статические цены)** 
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true  
```

## <a name="see-also"></a>См. также:
- [Помощник по миграции данных](https://aka.ms/get-dma) загрузить.
- В этой статье [указывается правильный номер SKU базы данных SQL Azure для локальной базы данных](https://aka.ms/dma-sku-recommend-sqldb).
