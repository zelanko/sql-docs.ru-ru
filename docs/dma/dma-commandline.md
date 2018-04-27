---
title: Запустите из командной строки (SQL Server данных помощник по миграции) | Документы Microsoft
ms.custom: ''
ms.date: 09/01/2017
ms.prod: sql
ms.prod_service: dma
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-dma
ms.tgt_pltfrm: ''
ms.topic: article
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0bf0437354f90a03f1d1cf68be074df3f4234676
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Запустите помощник по миграции данных из командной строки
С версии 2.1 и выше, когда вы можете установить помощник по миграции данных, она также устанавливает dmacmd.exe в *% ProgramFiles %\\Microsoft данных помощник по миграции\\*. Используйте dmacmd.exe для оценки баз данных в автоматическом режиме и вывода результатов в формате JSON или CSV-файл. Это особенно полезно при оценке несколько баз данных или большой базы данных. 

> [!NOTE]
> Dmacmd.exe поддерживает выполнение только для оценки. В настоящее время не поддерживается миграция.


## <a name="command-line-arguments"></a>Аргументы командной строки

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentTargetPlatform="TargetPlatform"\]
/AssessmentEvaluateRecommendations|/AssessmentEvaluateCompatibilityIssues
\[/AssessmentOverwriteResult\]
/AssessmentResultJson="file"|/AssessmentResultCsv="file"
```


|Аргумент  |Описание  | Обязательный (Y/N)
|---------|---------|---------------|
| `/help or /?`     | Как использовать dmacmd.exe текст справки        | Нет
|`/AssessmentName`     |   Имя проекта оценки   | Да
|`/AssessmentDatabases`     | Пробелами список строк подключения. Имя базы данных (Initial Catalog) учитывается регистр символов. | Да
|`/AssessmentTargetPlatform`     | Целевая платформа для оценки, поддерживаемые значения: SqlServer2012, SqlServer2014, SqlServer2016 и AzureSqlDatabaseV12. Значение по умолчанию — SqlServer2016   | Нет
|`/AssessmentEvaluateFeatureParity`  | Запустите четности правила компонентов  | Нет
|`/AssessmentEvaluateCompatibilityIssues`     | Выполнение правил совместимости  | Да <br> (AssessmentEvaluateCompatibilityIssues или AssessmentEvaluateRecommendations не требуется.)
|`/AssessmentEvaluateRecommendations`     | Запустите функцию рекомендации        | Да <br> (AssessmentEvaluateCompatibilityIssues или AssessmentEvaluateRecommendationsis требуется)
|`/AssessmentOverwriteResult`     | Перезаписать файл результатов    | Нет
|`/AssessmentResultJson`     | Полный путь к файлу результатов JSON     | Да <br> (AssessmentResultJson или AssessmentResultCsv не требуется)
|`/AssessmentResultCsv`    | Полный путь к файлу результатов CSV   | Да <br>(AssessmentResultJson или AssessmentResultCsv не требуется)




## <a name="examples"></a>Примеры

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Оценки одного-базы данных, с помощью правила совместимости проверки подлинности и выполнения Windows**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***Integrated Security=true*"**
***/AssessmentEvaluateCompatibilityIssues*** /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```



**Оценки одного-базы данных, используя рекомендации функции проверки подлинности и выполнения SQL Server**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***User Id=myUsername;Password=myPassword;***"
***/AssessmentEvaluateRecommendations*** /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```


**Оценки одного-базы данных для целевой платформы SQL Server 2012 и сохранить результаты в файл .json и CSV**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
***/AssessmentTargetPlatform="SqlServer2012"***
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
***/AssessmentResultJson***="C:\\temp\\Results\\AssessmentReport.json"
***/AssessmentResultCsv***="C:\\temp\\Results\\AssessmentReport.csv"
```


**Оценки одного-базы данных для целевой платформы базы данных SQL Azure сохранить результаты в файл .json и CSV**

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


**Оценка несколькими базами данных**

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



## <a name="see-also"></a>См. также:

[Загрузка помощник по миграции данных](https://www.microsoft.com/download/details.aspx?id=53595)
