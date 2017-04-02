---
title: "Преобразование универсальных имен ресурса в пути поставщика SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Преобразование универсальных имен ресурса в пути поставщика SQL Server
  Модель объектов управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает унифицированные имена ресурсов (URN) для своих объектов. Каждое универсальное имя ресурса (URN) однозначно определяет объект SMO и может быть преобразовано в путь поставщика SQL Server PowerShell с помощью командлета **Convert-UrnToPath**.  
  
## Преобразование имен URN в пути  
 Каждое имя URN содержит ту же информацию, что и путь к объекту, но представленную в другой форме. Например, ниже показан путь к таблице:  
  
 SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address  
  
 А ниже приведено имя URN, указывающее на тот же объект:  
  
 Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']  
  
 Если объект SMO создан в скрипте PowerShell, можно узнать URN объекта из свойства **Urn**, а затем использовать командлет **Convert-UrnToPath** для преобразования строки универсального имени ресурса объекта SMO в путь Windows PowerShell. Затем можно использовать поставщик для перехода в различные точки на пути.  
  
 Если имена узлов содержат символы национального алфавита, которые не поддерживаются в именах путей Windows PowerShell, командлет **Convert-UrnToPath** преобразует их в шестнадцатеричное представление. Например, строка «My:Table» возвращается как «My%3ATable».  
  
 Чтобы ознакомиться с примерами использования этого командлета, выполните в среде Windows PowerShell:  
  
```  
Get-Help Convert-UrnToPath -Examples  
```  
  
## См. также:  
 [Выражения запросов и универсальные имена ресурсов](../../powershell/query-expressions-and-uniform-resource-names.md)   
 [SQL Server PowerShell, поставщик](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  