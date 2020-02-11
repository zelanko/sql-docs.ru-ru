---
title: Создание файлов переменных значений (Акцесстоскл) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 808595c3-8ef1-40bd-a93e-5cf237950e08
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 051ded7d675f81998718b858c71488ba968ec680
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68006597"
---
# <a name="creating-variable-value-files-accesstosql"></a>Создание файлов переменных значений (Акцесстоскл)
Файл значений переменных — это XML-файл, состоящий из значений параметров команд (таких как имя исходного или целевого сервера), которые часто меняются при миграции сервера. При выполнении большого количества миграций баз данных создаются несколько переменных файлов для хранения значений каждого исходного сервера и на них указывают ссылки в файле главного сценария с помощью параметра **-v** в командной строке. Это поведение помогает поддерживать статические значения в нескольких файлах скриптов с переменными значениями в нескольких файлах переменных.  
  
> [!NOTE]  
> -  Имена переменных добавляются с префиксом в символ $ (доллар). Если переменной не присвоено значение в файле значения переменной, произойдет ошибка во время синтаксического анализа файла скрипта, что приведет к остановке процесса выполнения консоли.  
> -  Escape-символ для **$** имеет **$$** значение. Если значение переменной или статического значения параметра содержит символ **$** (доллар), то **$$** необходимо указать, что он будет обрабатываться как символ, а не как переменная.  
> -  Для целей обслуживания переменные могут быть объявлены внутри `'variable-group'` элементов для логического разделения определяемых пользователем переменных.  Использование этого элемента не является обязательным.  
  
**Примеры:**  
  
**Пример 1:**  
  
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
Пользователь может легко проверить свой файл значения переменной в файле определения схемы **консолескриптвариаблессчема. xsd** , доступном в папке Schemas.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в работе консоли — [Создание файлов подключения к серверу &#40;акцесстоскл&#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
## <a name="see-also"></a>См. также раздел  
[Создание файлов подключения к серверу (доступ)](https://msdn.microsoft.com/829153be-aa8e-4162-87e8-69882feecf19)  
  
