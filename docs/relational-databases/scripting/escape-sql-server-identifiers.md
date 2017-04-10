---
title: "Применение escape-символов к идентификаторам SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Применение escape-символов к идентификаторам SQL Server
  Часто можно использовать escape-символ обратной кавычки Windows PowerShell (`) для экранирования символов, применение которых допускается в идентификаторах с разделителями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но не в именах путей Windows PowerShell. Тем не менее экранирование некоторых символов невозможно. Например, в среде Windows PowerShell нельзя экранировать символ двоеточия (:). Идентификаторы с этим символом должны быть закодированы. Кодировка более надежна, чем экранирование, поскольку действует для всех символов.  
  
## Перед началом  
 Символ обратной кавычки (`) обычно расположен на клавише в верхнем левом углу клавиатуры, под клавишей ESC.  
  
## Примеры  
 Ниже приведен пример экранирования символа #:  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 Это пример экранирования скобок при указании (local) в качестве имени компьютера:  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## См. также:  
 [Идентификаторы SQL Server в PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell, поставщик](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  