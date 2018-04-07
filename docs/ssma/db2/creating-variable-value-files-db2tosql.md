---
title: Создание файлов значение переменной (DB2ToSQL) | Документы Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 122f3fbe-46a0-40df-ac3b-d43bf33d96ba
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 41ddf64fdad160c1467903c41e40c5968bea2399
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="creating-variable-value-files-db2tosql"></a>Создание файлов значение переменной (DB2ToSQL)
Файл значение переменной является XML-файл, состоящий из значений параметра команд как имя сервера источника или назначения, которые часто изменяются в зависимости от одного сервера миграции. При возникновении большое количество миграции базы данных, несколько файлов переменной для хранения значения каждого исходного сервера создается, на которые ссылается файл сценария master **– v** переключения командной строки. Это помогает при ведении статических значений в несколько файлов скриптов, если значения переменных в нескольких файлах переменной.  
  
> [!NOTE]  
> 1.  Имена переменных префиксом и суффиксом символом $ (доллара). Если переменные не будут назначены значения в файле значение переменной, возникает ошибка при синтаксическом разборе файла скрипта, возникающие в процесс выполнения консоли остановился.  
> 2.  The escape character for **$** is **$$**. Если значение переменной или статической значение параметра содержит **$** символ (доллара), затем **$$** должен быть указан следует считать символ вместо переменной.  
> 3.  В целях удобства переменные могут быть объявлены внутри `‘variable-group’` элементы для логического разделения пользователя определены переменные.  Использование этого элемента не является обязательным.  
  
**Примеры:**  
  
**Пример 1.**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<project-folder>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**Пример 2.**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в работе консоли — [Создание файлов подключения сервера &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
## <a name="see-also"></a>См. также  
[Создание файлов подключения к серверу](http://msdn.microsoft.com/en-us/002f129e-0868-48ad-a4b4-c68b5007e12e)  
  
