---
title: Идентификаторы SQL Server в PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- PowerShell [SQL Server], identifiers
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- identifiers [SQL Server], PowerShell
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 651099b0-33b4-453a-a864-b067f21eb8b9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3823b6d55439aad860d9176933c348e44acc1ba5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922853"
---
# <a name="sql-server-identifiers-in-powershell"></a>Идентификаторы SQL Server в PowerShell
  Поставщик [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для Windows PowerShell использует идентификаторы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в путях Windows PowerShell. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] могут содержать символы, которые не поддерживаются в путях Windows PowerShell. Такие символы при использовании в идентификаторах в составе путей Windows PowerShell следует экранировать или применять для них специальную кодировку.  
  
## <a name="sql-server-identifiers-in-windows-powershell-paths"></a>Идентификаторы SQL Server в путях Windows PowerShell  
 Поставщики Windows PowerShell предоставляют доступ к иерархиям данных с помощью структуры путей, аналогичной используемой в файловой системе Windows. В поставщике [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] реализуются пути к объектам [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Для компонента [!INCLUDE[ssDE](../includes/ssde-md.md)]жесткий диск задается как SQLSERVER, а первая папка — как \SQL. Объекты базы данных указываются как контейнеры и элементы. Ниже приведен путь к таблице Vendor в схеме Purchasing базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] на экземпляре компонента [!INCLUDE[ssDE](../includes/ssde-md.md)]по умолчанию:  
  
```  
SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Purchasing.Vendor  
```  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] представляют собой имена объектов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , такие как имена таблиц или столбцов. Существуют два типа идентификаторов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Обычные идентификаторы ограничены набором символов, которые также поддерживаются в путях Windows PowerShell. Такие имена можно использовать в путях Windows PowerShell без изменения.  
  
-   В идентификаторах с разделителями можно использовать символы, неподдерживаемые в именах путей Windows PowerShell. Идентификаторами с разделителями называют идентификаторы, заключенные в квадратные скобки (например: [ИмяИдентификатора]) и заключенные в кавычки (например: "ИмяИдентификатора"). Если в идентификаторе с разделителями используются символы, неподдерживаемые в путях Windows PowerShell, эти символы нужно кодировать или экранировать перед использованием идентификатора в качестве имени элемента или контейнера. Кодировка применяется для всех символов. С другой стороны, экранирование некоторых символов, таких как символ двоеточия (:), невозможно.  
  
## <a name="sql-server-identifiers-in-cmdlets"></a>Идентификаторы SQL Server в командлетах  
 Некоторые командлеты [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] имеют параметры, в которые в качестве входных данных передается идентификатор. Значения таких параметров обычно задаются в виде строковых констант, заключенных в кавычки, или строковых переменных. Если идентификаторы задаются в виде строковых констант или в переменных, то конфликты с набором символов, поддерживаемых Windows PowerShell, не возникают.  
  
## <a name="sql-server-identifier-tasks"></a>Работа с идентификаторами SQL Server  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описывает, как указывать имя экземпляра, включая имя компьютера, на котором эксплуатируется экземпляр.|[Указание экземпляров в поставщике SQL Server PowerShell](sql-server-powershell-provider.md)|  
|Описывает, как указывать шестнадцатеричную кодировку для символов в идентификаторах с разделителями, которые не поддерживаются Windows PowerShell. Кроме того, описывает, как декодировать шестнадцатеричные символы.|[Шифрование и расшифровка идентификаторов SQL Server](encode-and-decode-sql-server-identifiers.md)|  
|Описывает, как использовать escape-символ Windows PowerShell для символов, не поддерживаемых в путях PowerShell.|[Применение escape-символов к идентификаторам SQL Server](escape-sql-server-identifiers.md)|  
  
## <a name="see-also"></a>См. также  
 [SQL Server PowerShell, поставщик](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)   
 [Идентификаторы баз данных](../relational-databases/databases/database-identifiers.md)  
  
  
