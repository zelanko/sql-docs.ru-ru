---
title: Создание файлов переменных значений (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 122f3fbe-46a0-40df-ac3b-d43bf33d96ba
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: cf62d09de1180687598d817ff9199d7098008829
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63299135"
---
# <a name="creating-variable-value-files-db2tosql"></a>Создание файлов переменных значений (DB2ToSQL)
Файл переменных значение является XML-файл, состоящий из значений параметра команды, имя сервера источника или назначения, которые часто изменяются в зависимости от одного сервера миграции. При возникновении большое количество миграцию баз данных, несколько файлов переменной для хранения значения каждого исходного сервера создается, на которые ссылается файл скрипта базы данных master с **- v** переключиться в командной строке. Это помогает в поддержании статических значений в нескольких файлах скриптов, если значения переменных в нескольких файлах переменной.  
  
> [!NOTE]  
> 1.  Имена переменных префиксом и суффиксом символом $ (доллара). Если переменные не присваивается значение в файле значение переменной, возникает ошибка при синтаксическом анализе файла скрипта, приводит к разблокированию процесс выполнения консоли.  
> 2.  Escape-символа для **$** — **$$**. Если значение переменной или статической значение параметра содержит **$** символа (доллара), затем **$$** должен быть указан следует считать символ вместо переменной.  
> 3.  В целях удобства поддержки переменные можно объявлять внутри `'variable-group'` элементы для логического разделения пользователя определены переменные.  Использование этого элемента не является обязательным.  
  
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
Следующий шаг в работе консоли — [Создание файлов подключения к серверу &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
## <a name="see-also"></a>См. также  
[Создание файлов подключения к серверу](../oracle/creating-the-server-connection-files-oracletosql.md)  
  
