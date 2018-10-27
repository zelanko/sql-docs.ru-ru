---
title: Запустите помощник по миграции данных из командной строки (SQL Server) | Документация Майкрософт
description: Узнайте, как запустить помощник по миграции данных из командной строки для оценки базы данных SQL Server для миграции
ms.custom: ''
ms.date: 10/20/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
author: pochiraju
ms.author: rajpo
manager: craigg
ms.openlocfilehash: c308dc9e0f05ec8abed83a75a3a1d0ea396fd46c
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49643992"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Запустите помощник по миграции данных из командной строки
В версии 2.1 и выше, когда установки помощника по миграции данных, также устанавливается dmacmd.exe в *% ProgramFiles %\\Microsoft Data Migration Assistant\\*. Используйте dmacmd.exe для оценки баз данных в автоматическом режиме и вывода результата JSON или CSV-файл. Этот метод особенно полезен при оценке в нескольких базах данных или огромных баз данных. 

> [!NOTE]
> Dmacmd.exe поддерживает только оценки. В настоящее время не поддерживается миграция.


## <a name="assessments-using-the-command-line-interface-cli"></a>Оценки, с помощью интерфейса командной строки (CLI)

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentTargetPlatform="TargetPlatform"\]
/AssessmentEvaluateRecommendations|/AssessmentEvaluateCompatibilityIssues
\[/AssessmentOverwriteResult\]
/AssessmentResultJson="file"|/AssessmentResultCsv="file"
```

|Аргумент  |Описание  | Требуется (Y/N)
|---------|---------|---------------|
| `/help or /?`     | Как использовать dmacmd.exe текст справки        | Нет
|`/AssessmentName`     |   Имя проекта оценки   | Да
|`/AssessmentDatabases`     | Разделенный пробелами список строк подключения. Имя базы данных (начальный каталог) учитывается регистр. | Да
|`/AssessmentTargetPlatform`     | Целевая платформа для оценки, поддерживаемые значения: SqlServer2012 "," SqlServer2014 "," SqlServer2016 "и" AzureSqlDatabaseV12. Значение по умолчанию — SqlServer2016   | Нет
|`/AssessmentEvaluateFeatureParity`  | Запустить правила равенства  | Нет
|`/AssessmentEvaluateCompatibilityIssues`     | Выполнение правил совместимости  | Да <br> (AssessmentEvaluateCompatibilityIssues или AssessmentEvaluateRecommendations является обязательным.)
|`/AssessmentEvaluateRecommendations`     | Выполните рекомендуемые возможности        | Да <br> (AssessmentEvaluateCompatibilityIssues или AssessmentEvaluateRecommendationsis требуется)
|`/AssessmentOverwriteResult`     | Перезаписать файл результатов    | Нет
|`/AssessmentResultJson`     | Полный путь к файлу результатов JSON     | Да <br> (AssessmentResultJson или AssessmentResultCsv является обязательным)
|`/AssessmentResultCsv`    | Полный путь к CSV-файл результатов   | Да <br>(AssessmentResultJson или AssessmentResultCsv является обязательным)


## <a name="examples-of-assessments-using-the-cli"></a>Примеры оценки, с помощью интерфейса командной строки

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Оценки одного-базы данных, с помощью правил совместимости проверки подлинности и выполнения Windows**


```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***Integrated Security=true*"**
***/AssessmentEvaluateCompatibilityIssues*** /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```

**Оценки одного-базы данных, с помощью рекомендаций функции проверки подлинности и запуска SQL Server**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***User Id=myUsername;Password=myPassword;***"
***/AssessmentEvaluateRecommendations*** /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**Оценки одного-базы данных для целевой платформы SQL Server 2012, сохранить результаты в файл, файл JSON и CSV-файл**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
***/AssessmentTargetPlatform="SqlServer2012"***
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
***/AssessmentResultJson***="C:\\temp\\Results\\AssessmentReport.json"
***/AssessmentResultCsv***="C:\\temp\\Results\\AssessmentReport.csv"
```

**Оценки одного-базы данных для целевой платформы базы данных SQL Azure, сохранить результаты в файл, файл JSON и CSV-файл**

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

**Оценка нескольких-базы данных**

```
DmaCmd.exe /AssessmentName="TestAssessment"
***/AssessmentDatabases="Server=SQLServerInstanceName1;Initial
Catalog=DatabaseName1;Integrated Security=true"
"Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated
Security=true" "Server=SQLServerInstanceName2;Initial
Catalog=DatabaseName3;Integrated Security=true"***
/AssessmentTargetPlatform="SqlServer2016"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
/AssessmentResultJson="C:\\Results\\test2016.json"
```

## <a name="azure-sql-database-sku-recommendations-using-the-cli"></a>Рекомендации SKU базы данных SQL Azure с помощью интерфейса командной строки

> [!IMPORTANT]
> SKU рекомендации для базы данных SQL Azure в настоящее время доступны для миграции из SQL Server 2016 или более поздней версии.

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
/AzureAuthenticationInteractiveAuthentication=true
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
```

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true 
```

|Аргумент  |Описание  | Требуется (Y/N)
|---------|---------|---------------|
|`/Action=SkuRecommendation` | Выполнение оценки SKU, с помощью DMA командной строки | Да
|`/SkuRecommendationInputDataFilePath`  | Полный путь к файлу счетчика производительности, собранные с компьютера, на котором размещены ваши базы данных |    Да
|`/SkuRecommendationTsvOutputResultsFilePath`   | Полный путь к файлу результата TSV |    Да <br>(Необходим путь к файлу TSV или JSON или HTML)
|`/SkuRecommendationJsonOutputResultsFilePath`  | Полный путь к файлу результатов JSON |   Да <br>(Необходим путь к файлу TSV или JSON или HTML)
|`/SkuRecommendationHtmlResultsFilePath` |  Полный путь к файлу результата HTML | Да <br>(Необходим путь к файлу TSV или JSON или HTML)
|`/SkuRecommendationPreventPriceRefresh` |  Запрещает обновление цены. Используйте, если выполняется в автономном режиме. |    Да <br>(Этот аргумент выбран статический цены или все аргументы, которые ниже нужно выбрать для получения последних цены)
|`/SkuRecommendationCurrencyCode` | Валюта, в которой отображаются цены (например) «ДОЛЛ. США)» | Да <br>(Если вы хотите получить последние цены)
|`/SkuRecommendationOfferName` |    Предложение name (например) "MS-AZR - 0003 P»). Дополнительные сведения см. в разделе [сведения о предложении Microsoft Azure](https://azure.microsoft.com/support/legal/offer-details/) страницы. |   Да <br>(Если вы хотите получить последние цены)
|`/SkuRecommendationRegionName` |   Области имя (например) «WestUS») |   Да <br>(Если вы хотите получить последние цены)
|`/SkuRecommendationSubscriptionId` | Идентификатор подписки. |    Да <br>(Если вы хотите получить последние цены)
|`/AzureAuthenticationTenantId` | Клиент проверки подлинности. |  Да <br>(Если вы хотите получить последние цены)
|`/AzureAuthenticationClientId` | Идентификатор клиента приложения AAD, используемый для проверки подлинности. | Да <br>(Если вы хотите получить последние цены)
|`/AzureAuthenticationInteractiveAuthentication`    | Значение true для всплывающие окна. |   Да <br>(Если вы хотите получить последние цены) <br>(Выберите один из вариантов проверки подлинности 3 — вариант 1)
|`/AzureAuthenticationCertificateStoreLocation` | Значение в расположении хранилища сертификатов (например) «CurrentUser»). | Да <br>(Если вы хотите получить последние цены) <br>(Выберите один из вариантов проверки подлинности 3 — вариант 2)
|`/AzureAuthenticationCertificateThumbprint`    | Задается для отпечатка сертификата. | Да <br>(Если вы хотите получить последние цены) <br>(Выберите один из вариантов проверки подлинности 3 — вариант 2)
|`/AzureAuthenticationToken` |  Значение маркера сертификата. | Да <br>(Если вы хотите получить последние цены) <br>(Выберите один из вариантов проверки подлинности 3 — вариант 3)

## <a name="examples-of-sku-assessments-using-the-cli"></a>Примеры Конфигураций тестов, с помощью интерфейса командной строки

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Рекомендации Azure SQL DB SKU с стоимость обновления (get последними ценами) - интерактивной проверки подлинности** 
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

**Рекомендации Azure SQL DB SKU с стоимость обновления (get последними ценами) — проверка подлинности сертификата**
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

**Рекомендации Azure SQL DB SKU с стоимость обновления (get последними ценами) - маркер проверки подлинности**  
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
/AzureAuthenticationToken=<Your Authentication Token> 
```

**Рекомендации Azure SQL DB SKU без обновления цены (используйте статические цены)** 
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true  
```

## <a name="see-also"></a>См. также
- [Помощник по миграции данных](https://aka.ms/get-dma) загрузки.
- Статья [определить нужный номер SKU базы данных Azure SQL для базы данных в локальной](https://aka.ms/dma-sku-recommend-sqldb).
