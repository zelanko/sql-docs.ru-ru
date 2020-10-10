---
title: Сборка проекта из командной строки
description: Создание проектов базы данных SQL Server из командной строки
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.reviewer: maghan, sstein
ms.custom: ''
ms.date: 08/07/2020
ms.openlocfilehash: a6849f13f8182285749c7a95801ee111e7ba0130
ms.sourcegitcommit: c4d6804bde7eaf72d9233d6d43f77d77d1b17c4e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2020
ms.locfileid: "91624681"
---
# <a name="build-a-database-project-from-command-line"></a>Создание проекта базы данных из командной строки

В то время как расширение "Проект Базы данных SQL" для Azure Data Studio предоставляет графический пользовательский интерфейс для [сборки проекта базы данных](sql-database-project-extension-build.md), встроенный интерфейс командной строки также доступен для сред Windows, macOS и Linux. В этой статье содержатся сведения о предварительных требованиях и синтаксисе, необходимых для создания проекта SQL для DACPAC из командной строки.

## <a name="prerequisites"></a>Предварительные требования

1. Установите и настройте [расширение проектов баз данных SQL для Azure Data Studio](sql-database-project-extension.md).

2. Для построения проекта базы данных SQL из командной строки на всех платформах, которые поддерживаются расширением Azure Data Studio, для проектов базы данных SQL необходимы следующие DLL-библиотеки .NET Core и целевой файл `Microsoft.Data.Tools.Schema.SqlTasts.targets`. Эти файлы создаются расширением во время первой сборки, выполненной в интерфейсе Azure Data Studio и помещенной в папку расширения в разделе `BuildDirectory`.  Например, на Linux эти файлы помещаются в `~\.azuredatastudio\extensions\microsoft.sql-database-projects-x.x.x\BuildDirectory\`.  Скопируйте эти 10 файлов в новую и доступную папку или запишите их расположение.  Это расположение будет обозначаться в документе как `DotNet Core build folder`.

    - Microsoft.Data.Tools.Schema.Sql.dll
    - Microsoft.Data.Tools.Schema.Tasks.Sql.dll
    - Microsoft.Data.Tools.Utilities.dll
    - System.Io.Packaging.dll
    - Microsoft.SqlServer.Dac.dll
    - Microsoft.SqlServer.Dac.Extensions.dll
    - Microsoft.SqlServer.TransactSql.ScriptDom.dll
    - Microsoft.SqlServer.Types.dll
    - Microsoft.Data.Tools.Schema.SqlTasks.targets
    - System.ComponentModel.Composition.dll
    - Microsoft.Data.SqlClient.dll

3. Если проект создан в Azure Data Studio, перейдите к разделу [Сборка проекта из командной строки](#build-the-project-from-the-command-line). Если проект создан в SQL Server Data Tools (SSDT), откройте его в расширении проекта Базы данных SQL для Azure Data Studio.  При открытии проекта в Azure Data Studio файл `sqlproj` автоматически обновляется с тремя правками, приведенными ниже для сведений.

    1. Условия импорта

    ```console
    <Import Condition="'$(NetCoreBuild)' == 'true'" Project="$(NETCoreTargetsPath)\Microsoft.Data.Tools.Schema.SqlTasks.targets"/> 
    <Import Condition="'$(NetCoreBuild)' != 'true' AND '$(SQLDBExtensionsRefPath)' != ''" Project="$(SQLDBExtensionsRefPath)\Microsoft.Data.Tools.Schema.SqlTasks.targets"/>
    <Import Condition="'$(NetCoreBuild)' != 'true' AND '$(SQLDBExtensionsRefPath)' == ''" Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.SqlTasks.targets"/>
    ```

    2. Справочник по пакетам

    ```console
    <ItemGroup>
        <PackageReference Condition="'$(NetCoreBuild)' == 'true'" Include="Microsoft.NETFramework.ReferenceAssemblies" Version="1.0.0" PrivateAssets="All"/>
    </ItemGroup>
    ```

    3. Очистите целевой объект, необходимый для поддержки двойного редактирования в SQL Server Data Tools (SSDT) и Azure Data Studio

        ```console
        <Target Name="AfterClean">
            <Delete Files="$(BaseIntermediateOutputPath)\project.assets.json"/>
        </Target>
        ```

## <a name="build-the-project-from-the-command-line"></a>Сборка проекта из командной строки

В полной версии папки .NET используйте следующую команду:

```console
dotnet build "<sqlproj file path>" /p:NetCoreBuild=true /p:NETCoreTargetsPath="<DotNet Core build folder>"
```

Например, из `/usr/share/dotnet` в Linux

```console
dotnet build "/home/myuser/Documents/DatabaseProject1/DatabaseProject1.sqlproj" /p:NetCoreBuild=true /p:NETCoreTargetsPath="/home/myuser/.azuredatastudio-insiders/extensions/microsoft.sql-database-projects-0.1.2/BuildDirectory"  
```

## <a name="next-steps"></a>Дальнейшие действия

- [Расширение проектов баз данных SQL для Azure Data Studio](sql-database-project-extension.md)
- [Публикация проектов базы данных SQL](sql-database-project-extension-build.md#publish-a-database-project)
