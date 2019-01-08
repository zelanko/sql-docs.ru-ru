---
title: Создание файлов переменных значений (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 808595c3-8ef1-40bd-a93e-5cf237950e08
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 00144c51e60b72fe043443d2a9c8d1d51a6cb8da
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52542063"
---
# <a name="creating-variable-value-files-accesstosql"></a>Создание файлов переменных значений (AccessToSQL)
Файл значение переменной является XML-файл, состоящий из значений параметра команд (например, имя сервера источника или назначения), которые часто изменяются в разных миграция сервера. При возникновении большое количество миграцию баз данных, несколько файлов переменной для хранения значения каждого исходного сервера создаются и на которые ссылается файл скрипта базы данных master с **- v** переключиться в командной строке. Это помогает в поддержании статических значений в нескольких файлах скриптов, если значения переменных в нескольких файлах переменной.  
  
> [!NOTE]  
> -  Имена переменных префиксом и суффиксом символом $ (доллара). Если переменная не назначено значение в файле значение переменной, при синтаксическом анализе файла скрипта, произойдет ошибка, полученный в замедляется работа процесса выполнения консоли.  
> -  Escape-символа для **$** — **$$**. Если значение переменной или статической значение параметра содержит **$** символа (доллара), затем **$$** должен быть указан следует считать символ вместо переменной.  
> -  В целях удобства поддержки переменные можно объявлять внутри `'variable-group'` элементы для логического разделения определяемых пользователем переменных.  Использование этого элемента не является обязательным.  
  
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
  
## <a name="variable-value-file-validation"></a>Проверка файла значение переменной  
Пользователь легко можно проверить его/ее файл значение переменной, соответствие файлу определения схемы **ConsoleScriptVariablesSchema.xsd** доступны в папке «Схемы».  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в работе консоли — [Создание файлов подключения к серверу &#40;AccessToSQL&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
## <a name="see-also"></a>См. также  
[Создание файлов подключения к серверу (доступ)](https://msdn.microsoft.com/829153be-aa8e-4162-87e8-69882feecf19)  
  
