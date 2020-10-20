---
title: Применение escape-символов к идентификаторам SQL Server
description: Некоторые символы, отображаемые в идентификаторах SQL Server с разделителями, не поддерживаются в путях Windows PowerShell. Узнайте, как можно экранировать некоторые из них с помощью символа обратной кавычки.
ms.prod: sql
ms.technology: sql-server-powershell
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: markingmyname
ms.author: maghan
ms.reviewer: matteot, drskwier
ms.custom: ''
ms.date: 10/14/2020
ms.openlocfilehash: 4ad4bdc7720d0c405e3982b6b4533b55c2756490
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "92005499"
---
# <a name="escape-sql-server-identifiers"></a>Применение escape-символов к идентификаторам SQL Server

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Часто можно использовать экранирующий символ обратной кавычки (`) для escape-символов, применение которых допускается в идентификаторах с разделителями [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], но не в именах путей Windows PowerShell. Тем не менее экранирование некоторых символов невозможно. Например, в среде Windows PowerShell нельзя экранировать символ двоеточия (:). Идентификаторы с этим символом должны быть закодированы. Кодировка более надежна, чем экранирование, поскольку действует для всех символов.  

[!INCLUDE [sql-server-powershell-version](../includes/sql-server-powershell-version.md)]

Символ обратной кавычки (`) обычно расположен на клавише в верхнем левом углу клавиатуры, под клавишей ESC.  

## <a name="examples"></a>Примеры

Ниже приведен пример экранирования символа #:  

```powershell
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```

Это пример экранирования скобок при указании (local) в качестве имени компьютера:  

```powershell
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```

## <a name="see-also"></a>См. также:

- [Идентификаторы SQL Server в PowerShell](sql-server-identifiers-in-powershell.md)
- [Поставщик SQL Server PowerShell](sql-server-powershell-provider.md)
- [SQL Server PowerShell](sql-server-powershell.md)