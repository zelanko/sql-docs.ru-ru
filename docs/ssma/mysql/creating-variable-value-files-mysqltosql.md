---
title: Создание файлов переменных значений (MySQLToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Creating variable value files
- variable value file validation
ms.assetid: 1dc56a7b-8e3a-4576-ad4f-47050bf7e28a
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: b3b44a99893c2dbc3dbd3a0597e6600020211702
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935713"
---
# <a name="creating-variable-value-files-mysqltosql"></a>Создание файлов переменных значений (MySQLToSQL)
Файл значения переменной — это XML-файл, состоящий из значений параметров таких команд, как, имя исходного или целевого сервера, которое часто меняются при миграции с одного сервера на другой. При выполнении большого количества миграций базы данных создается несколько переменных файлов для хранения значений каждого исходного сервера и на них указывают ссылки в файле главного сценария с помощью параметра **-v** в командной строке. Это помогает поддерживать статические значения в нескольких файлах скриптов с переменными значениями в нескольких файлах переменных.  
  
> [!NOTE]  
> 1.  Имена переменных добавляются с префиксом в символ $ (доллар). Если переменным не присвоено значение в файле значения переменной, то во время синтаксического анализа файла скрипта будет возникать ошибка, что привело к остановке процесса выполнения консоли.  
> 2.  Escape-символ для **$** имеет значение **$$** . Если значение переменной или статического значения параметра содержит **$** символ (доллар), то **$$** необходимо указать, что он будет обрабатываться как символ, а не как переменная.  
> 3.  Для целей обслуживания переменные могут быть объявлены внутри `'variable-group'` элементов для логического разделения определяемых пользователем переменных.  Использование этого элемента не является обязательным.  
  
**Примеры:**  
  
**Пример 1**.  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<folder-name>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**Пример 2.**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetUserName$ value="<user-name>"/>  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
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
  
## <a name="variable-value-file-validation"></a>Проверка файла значения переменной  
Пользователь может легко проверить свой файл значений переменных по отношению к файлу определения схемы **"консолескриптвариаблессчема. xsd"** , доступному в папке "Schemas".  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в работе консоли — [Создание файлов подключения к серверу &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
## <a name="see-also"></a>См. также:  
[Создание файлов подключения к серверу (MySQL)](https://msdn.microsoft.com/df0e970c-da0b-4118-b359-c9dcbbad16d6)  
  
