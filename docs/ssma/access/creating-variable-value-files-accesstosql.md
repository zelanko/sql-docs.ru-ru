---
title: Создание файлов значение переменной (AccessToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 808595c3-8ef1-40bd-a93e-5cf237950e08
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 44c317d773df9027f5c485f417941544ff17c6d0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="creating-variable-value-files-accesstosql"></a>Создание файлов значение переменной (AccessToSQL)
Файл значение переменной является XML-файл, состоящий из значений параметра команд (например, имя сервера источника или назначения), которые часто изменяются в разных миграция сервера. При возникновении большое количество миграции базы данных, несколько файлов переменной для хранения значения каждого исходного сервера создаются и на которые ссылается файл сценария master **– v** переключения командной строки. Это помогает в поддержании статических значений в несколько файлов скриптов, если значения переменных в нескольких файлах переменной.  
  
> [!NOTE]  
> -  Имена переменных префиксом и суффиксом символом $ (доллара). Если переменная не назначено значение в файле значение переменной, при синтаксическом разборе файла скрипта произойдет ошибка, полученный в процесс выполнения консоли остановился.  
> -  The escape character for **$** is **$$**. Если значение переменной или статической значение параметра содержит **$** символ (доллара), затем **$$** должен быть указан следует считать символ вместо переменной.  
> -  В целях удобства переменные могут быть объявлены внутри `‘variable-group’` элементы для логического разделения определяемых пользователем переменных.  Использование этого элемента не является обязательным.  
  
**Примеры:**  
  
**Пример 1.**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$type$" value="MyProject"/>  
  
    <variable name="$project_folder$" value=".\$project_name$"/>  
  
    <variable name="$project_name$" value="$type$ConsoleProject"/>  
  
    <variable name="$project_overwrite$" value="true"/>  
  
    <variable name="$project_type$" value="sql-server-2008"/>  
  
  </variable-group>  
  
</variables>  
```  
**Пример 2.**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="xxx"/>  
  
      <variable name="$TargetDB$" value="xxx"/>  
  
      <variable name="$TargetUserName$" value="xxx"/>  
  
      <variable name="$TargetPassword$" value="xxx"/>  
  
      <variable name="$TargetIsTrusted$" value="xxx"/>  
  
      <variable name="$TrustedConnection$" value="xxx"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="TestTable1"/>  
  
      <variable name="$ObjectName2$" value="TestProc1"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="variable-value-file-validation"></a>Проверка файла значения переменной  
Пользователь может легко проверить свой файл значение переменной, соответствие файлу определения схемы **ConsoleScriptVariablesSchema.xsd** доступны в папке «Схемы».  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в работе консоли — [Создание файлов подключения сервера &#40;AccessToSQL&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
## <a name="see-also"></a>См. также:  
[Создание файлов подключения сервера (Access)](http://msdn.microsoft.com/829153be-aa8e-4162-87e8-69882feecf19)  
  
