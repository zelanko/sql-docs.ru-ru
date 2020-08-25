---
title: Сборка проекта из командной строки
description: Создание проектов базы данных SQL Server из командной строки
ms.custom: seodec18
ms.date: 08/07/2020
ms.reviewer: drskwier, maghan, sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: ec3c9224e0cf93ae24ba1a4858b0299f7b303076
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180723"
---
# <a name="build-a-database-project-from-command-line"></a>Создание проекта базы данных из командной строки

В то время как расширение "Проект Базы данных SQL" для Azure Data Studio предоставляет графический пользовательский интерфейс для [сборки проекта базы данных](sql-database-project-extension-build.md), встроенный интерфейс командной строки также доступен для сред Windows, macOS и Linux. В этой статье содержатся сведения о предварительных требованиях и синтаксисе, необходимых для создания проекта SQL для DACPAC из командной строки.

## <a name="prerequisites"></a>Предварительные требования
1. Установите и настройте [расширение проектов баз данных SQL для Azure Data Studio](sql-database-project-extension.md).

2. Для построения проекта базы данных SQL из командной строки на всех платформах, которые поддерживаются расширением Azure Data Studio, для проектов базы данных SQL необходимы следующие DLL-библиотеки .NET Core и целевой файл `Microsoft.Data.Tools.Schema.SqlTasts.targets`. Эти файлы создаются расширением во время первой сборки, выполненной в интерфейсе Azure Data Studio и помещенной в папку расширения в разделе `BuildDirectory`.  Например, на Linux эти файлы помещаются в `~\.azuredatastudio\extensions\microsoft.sql-database-projects-x.x.x\BuildDirectory\`.  Скопируйте эти 10 файлов в новую и доступную папку или запишите их расположение.  Это расположение будет обозначаться в документе как `DotNet Core build folder`.
- Microsoft.Data.Tools.Schema.Sql.dll

- Microsoft.Data.Tools.Schema.Tasks.Sql.dll

- Microsoft.Data.Tools.Utilities.dll 

- Microsoft.SqlServer.Dac.dll 

- Microsoft.SqlServer.Dac.Extensions.dll 

- Microsoft.SqlServer.TransactSql.ScriptDom.dll 

- Microsoft.SqlServer.Types.dll 

- Microsoft.Data.Tools.Schema.SqlTasks.targets 

- System.ComponentModel.Composition.dll 

- Microsoft.Data.SqlClient.dll 


3. Если проект создан в Azure Data Studio, перейдите к разделу [Сборка проекта из командной строки](#build-the-project-from-the-command-line). Если проект создан в SQL Server Data Tools (SSDT), откройте его в расширении проекта Базы данных SQL для Azure Data Studio.  При открытии проекта в Azure Data Studio файл `sqlproj` автоматически обновляется с тремя правками, приведенными ниже для сведений.
    1. Условия импорта 
    ```
    <Import Condition="'$(NetCoreBuild)' == 'true'" Project="$(NETCoreTargetsPath)\Microsoft.Data.Tools.Schema.SqlTasks.targets"/> 
    <Import Condition="'$(NetCoreBuild)' != 'true' AND '$(SQLDBExtensionsRefPath)' != ''" Project="$(SQLDBExtensionsRefPath)\Microsoft.Data.Tools.Schema.SqlTasks.targets"/> 
    <Import Condition="'$(NetCoreBuild)' != 'true' AND '$(SQLDBExtensionsRefPath)' == ''" Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.SqlTasks.targets"/> 
    ```
    2. Справочник по пакетам
    ```
    <ItemGroup> 
        <PackageReference Condition="'$(NetCoreBuild)' == 'true'" Include="Microsoft.NETFramework.ReferenceAssemblies" Version="1.0.0" PrivateAssets="All"/> 
    </ItemGroup> 
    ```
    3. Очистите целевой объект, необходимый для поддержки двойного редактирования в SQL Server Data Tools (SSDT) и Azure Data Studio
    ```
    <Target Name="AfterClean"> 
        <Delete Files="$(BaseIntermediateOutputPath)\project.assets.json"/> 
    </Target> 
    ```

## <a name="build-the-project-from-the-command-line"></a>Сборка проекта из командной строки
В полной версии папки .NET используйте следующую команду:
```
dotnet build "<sqlproj file path>" /p:NetCoreBuild=true /p:NETCoreTargetsPath="<DotNet Core build folder>"
```
Например, из `/usr/share/dotnet` в Linux
```
dotnet build "/home/myuser/Documents/DatabaseProject1/DatabaseProject1.sqlproj" /p:NetCoreBuild=true /p:NETCoreTargetsPath="/home/myuser/.azuredatastudio-insiders/extensions/microsoft.sql-database-projects-0.1.2/BuildDirectory"  
```
## <a name="next-steps"></a>Дальнейшие действия

- [Расширение проектов баз данных SQL для Azure Data Studio](sql-database-project-extension.md)
- [Публикация проектов базы данных SQL](sql-database-project-extension-build.md#publish-a-database-project)
