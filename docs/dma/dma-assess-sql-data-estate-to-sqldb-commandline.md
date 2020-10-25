---
title: 'ДМАКМД: Оценка готовности SQL Server к миграции в SQL Azure'
titleSuffix: Data Migration Assistant
description: Узнайте, как использовать средство командной строки Помощник по миграции данных (ДМАКМД) для оценки SQL Serverного объема данных для миграции в SQL Azure.
ms.date: 10/02/2020
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
author: rajeshsetlem
ms.author: rajpo
ms.custom: ''
ms.openlocfilehash: 35465a761258fb5a7865e711e2809d740b9b9fee
ms.sourcegitcommit: d35d0901296580bfceda6e0ab2e14cf2b7e99a0f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/24/2020
ms.locfileid: "92496817"
---
# <a name="dmacmd-assess-readiness-of-a-sql-server-data-estate-migrating-to-azure-sql"></a>ДМАКМД: Оценка готовности SQL Serverного пространства данных для переноса в Azure SQL 

Во многих организациях, пытающихся перейти на Azure, важно оценить существующие локальные SQL Server экземпляры и определить правильный целевой объект SQL Azure: база данных SQL Azure, Azure SQL Управляемый экземпляр или SQL Server на виртуальных машинах Azure. 

[Помощник по миграции данных (DMA)](dma-overview.md) помогает оценить экземпляр SQL Server для конкретного целевого объекта SQL Azure и оценить готовность баз данных SQL Server к миграции в Azure SQL. Отправка результатов оценки DMA в центр миграции Azure для централизованного представления готовности к работе с данными. 

В этой статье описывается, как выполнять оценку в масштабе и отправлять результаты в центр миграции Azure с помощью интерфейса командной строки DMA (ДМАКМД). Кроме того, для выполнения оценки можно использовать [графический интерфейс DMA](dma-assess-sql-data-estate-to-sqldb.md) .

Дополнительные сведения см. в следующем видео Channel9:

>
> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/How-to-Assess-Readiness-of-SQL-Server-Data-Estate-Migrating-to-Azure-SQL/player?WT.mc_id=dataexposed-c9-niner]

## <a name="prerequisites"></a>Обязательные условия 

Чтобы использовать ДМАКМД для выполнения оценки и передачи результатов в центр миграции Azure, вам потребуется следующее: 

- [Последняя версия помощник по миграции данных (DMA)](https://www.microsoft.com/en-us/download/details.aspx?id=53595).
- Проект службы " [Миграция Azure](dma-assess-sql-data-estate-to-sqldb.md#create-a-project-and-add-a-tool)". 
- Роль участника доступ к ресурсу проекта "миграция Azure".

## <a name="use-dmacmd"></a>Использование ДМАКМД

Используйте XML-файл в качестве входных данных для выполнения оценок в масштабе с помощью интерфейса командной строки (DMACMD.exe). 

Используйте следующий пример команды, чтобы передать XML-файл в ДМАКМД и начать оценку:

```console
C:\Program Files\Microsoft Data Migration Assistant\DmaCmd.exe /Action=Assess /AssessmentConfiguration= C:\Demo\ScaleAssessment\Assess-for-AzureSQLMI.xml
```

Содержимое образца `Assess-for-AzureSQLMI.xml` определяет элементы для оценки экземпляров SQL Server для целевого объекта SQL управляемый экземпляр: 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<AssessmentConfiguration xmlns="http://microsoft.com/schemas/SqlServer/Advisor/AssessmentConfiguration">
   <AssessmentName>Scale-Assessment-for-AzureSQLManagedInstance</AssessmentName>
   <AssessmentSourcePlatform>SqlOnPrem</AssessmentSourcePlatform>
   <AssessmentTargetPlatform>ManagedSqlServer</AssessmentTargetPlatform>
   <AssessmentDatabases>
      <AssessmentDatabase>Server=ServerName\SQL2017;Integrated Security=true</AssessmentDatabase>
      <AssessmentDatabase>Server=ServerName\SQL2016;Integrated Security=true;Initial Catalog=AdventureWorks2016</AssessmentDatabase>
      <AssessmentDatabase>Server=ServerName\SQL2016;Integrated Security=true;Initial Catalog=TestDB</AssessmentDatabase>
   </AssessmentDatabases>
   <AssessmentResultDma>C:\Demo\ScaleAssessment\AssessmentConfiguration\Scale-Assessment-for-AzureSQLManagedInstance.dma</AssessmentResultDma>
   <AssessmentResultJson>C:\Demo\ScaleAssessment\AssessmentConfiguration\Scale-Assessment-for-AzureSQLManagedInstance.json</AssessmentResultJson>
   <AssessmentResultCsv>C:\Demo\ScaleAssessment\AssessmentConfiguration\Scale-Assessment-for-AzureSQLManagedInstance.csv</AssessmentResultCsv>
   <AssessmentOverwriteResult>true</AssessmentOverwriteResult>
   <AssessmentEvaluateCompatibilityIssues>true</AssessmentEvaluateCompatibilityIssues>
   <AssessmentEvaluateFeatureParity>true</AssessmentEvaluateFeatureParity>
   <AzureCloudEnvironment>Azure</AzureCloudEnvironment>
   <SubscriptionId>xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx</SubscriptionId>
   <AzureMigrateProjectName>Scale-Assessment-for-AzureSQLMI</AzureMigrateProjectName>
   <ResourceGroupName>Resource-Group-Name</ResourceGroupName>
   <AzureAuthenticationInteractiveAuthentication>true</AzureAuthenticationInteractiveAuthentication>
   <AzureAuthenticationTenantId>xxxxxxxx-xxxx-xxxxxxxx</AzureAuthenticationTenantId>
   <EnableAssessmentUploadToAzureMigrate>true</EnableAssessmentUploadToAzureMigrate>
</AssessmentConfiguration>
```



## <a name="xml-elements"></a>Элементы XML 

XML-элементы, передаваемые в ДМАКМД, определяются в следующей таблице: 


|**XML-элемент** |**Определение**  |
|---------|---------|
|`AssessmentName`|Имя оценки|
|`AssessmentSourcePlatform`|Исходная платформа SQL Server. Значение по умолчанию — `SqlOnPrem`.|
|`AssessmentTargetPlatform`|Целевая платформа SQL Server.  </br> `AzureSqlDatabase` предназначен для целевого объекта базы данных SQL Azure. </br> `ManagedSqlServer` предназначен для целевого объекта Управляемый экземпляр Azure SQL. </br></br>Пример **оценки азуресклми** оценки целевого объекта SQL управляемый экземпляр.|
|`AssessmentDatabases`|Если необходимо оценить все базы данных в экземпляре, укажите только имя экземпляра, в каждой из которых указаны конкретные базы данных. </br></br>Пример **оценки азуресклми** оценивает все базы данных в экземпляре `Servername\SQL2017` и две определенные базы данных в экземпляре `Servername\SQL2016` .  |
|`AssessmentResultDma` </br> `AssessmentResultJson` </br> `AssessmentResultCsv` | Задает формат файла результатов. `.DMA`, `.JSON` и `.CSV` соответственно. Дважды щелкните, `.DMA` чтобы открыть в пользовательском интерфейсе DMA. <br> `AssessmentResultDma` требуется для отправки результатов оценки в центр миграции Azure.  |
|`AssessmentOverwriteResult`| Указывает, следует ли перезаписывать существующий файл результатов оценки с тем же путем, что и `AssessmentResultJson` , `AssessmentResultDma` или `AssessmentResultCsv` .|
|`AssessmentEvaluateCompatibilityIssues` </br> `AssessmentEvaluateFeatureParity` |Выполните оценку, чтобы оценить проблемы совместимости и нарушения четности компонентов соответственно.|
|`AzureCloudEnvironment`|Облачная среда Azure для подключения. значение по умолчанию — общедоступное облако Azure. </br></br> Поддерживаемые значения: </br>`Azure (default)`, `AzureChina`, `AzureGermany`, `AzureUSGovernment`.|
|`SubscriptionId`|Идентификатор подписки Azure.|
|`AzureMigrateProjectName`|Имя проекта службы "миграция Azure" для отправки результатов оценки.|
|`ResourceGroupName`|Имя группы ресурсов для миграции Azure.|
|`AzureAuthenticationInteractiveAuthentication`|Задайте значение `true` , чтобы открыть окно проверки подлинности.|
|`AzureAuthenticationTenantId`|Идентификатор клиента Azure Active Directory. </br></br>Получите это в колонке " **Обзор** " Azure Active Directory в [портал Azure](https://portal.azure.com). |
|`EnableAssessmentUploadToAzureMigrate`| Задайте значение `true` для отправки и публикации результатов оценки в центре миграции Azure.|
|   |   |


## <a name="results"></a>Результаты 

ДМАКМД выводит состояние после успешного завершения. 


Ниже приведен пример выходных данных результатов. 

```console
Assessment finished for project: Scale-Assessment-for-AzureSQLManagedInstance
DATABASES:
Succeeded             : 4
Failed                : 0
SERVER INSTANCES:
Succeeded             : 2
Failed                : 0
CSV result file       : C:\Demo\ScaleAssessment\Scale-Assessment-for-AzureSQLManagedInstance.csv
JSON result file      : C:\Demo\ScaleAssessment\Scale-Assessment-for-AzureSQLManagedInstance.json
--------------------------------------------------------------------------------
```

Просмотрите отправленные результаты в [службе "миграция Azure](dma-assess-sql-data-estate-to-sqldb.md#view-target-readiness-assessment-results) ", чтобы получить централизованное представление о всей области данных. . 

## <a name="best-practices"></a>Советы и рекомендации 

При использовании ДМАКМД учитывайте следующие рекомендации: 

- Логически группируются в соответствии с целевыми SQL Server экземплярами и базами данных, основанными на приложении, вместо того, чтобы оценивать все экземпляры SQL Server во всей области данных. 
- Создайте отдельный проект службы "миграция Azure" для каждой цели SQL Azure, чтобы избежать перезаписи результатов. 
- Время выполнения оценки зависит от количества объектов базы данных. По возможности избегайте выполнения оценок в рабочей системе и разгрузки на виртуальную машину или на промежуточный сервер, особенно для баз данных с большим количеством объектов. 


## <a name="see-also"></a>См. также

* [Помощник по миграции данных (DMA)](../dma/dma-overview.md)
* [Помощник по миграции данных: параметры конфигурации](../dma/dma-configurationsettings.md)
* [Помощник по миграции данных: рекомендации](../dma/dma-bestpractices.md)

