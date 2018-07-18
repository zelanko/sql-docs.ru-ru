---
title: Запустите помощник по миграции данных из командной строки (SQL Server) | Документация Майкрософт
description: Узнайте, как запустить помощник по миграции данных из командной строки для оценки базы данных SQL Server для миграции
ms.custom: ''
ms.date: 09/01/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 6b364dc03d48cbc1c0487362712e10f7ab0b782e
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785465"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Запустите помощник по миграции данных из командной строки
В версии 2.1 и выше, когда установки помощника по миграции данных, также устанавливается dmacmd.exe в *% ProgramFiles %\\Microsoft Data Migration Assistant\\*. Используйте dmacmd.exe для оценки баз данных в автоматическом режиме и вывода результата JSON или CSV-файл. Этот метод особенно полезен при оценке в нескольких базах данных или огромных баз данных. 

> [!NOTE]
> Dmacmd.exe поддерживает только оценки. В настоящее время не поддерживается миграция.


## <a name="command-line-arguments"></a>Аргументы командной строки

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




## <a name="examples"></a>Примеры

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



## <a name="see-also"></a>См. также

[Скачать помощник по миграции данных](https://www.microsoft.com/download/details.aspx?id=53595)
