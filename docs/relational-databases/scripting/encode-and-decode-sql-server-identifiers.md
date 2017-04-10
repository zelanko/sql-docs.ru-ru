---
title: "Шифрование и расшифровка идентификаторов SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# Шифрование и расшифровка идентификаторов SQL Server
  Идентификаторы SQL Server с разделителями иногда содержат символы, не поддерживаемые в путях Windows PowerShell. Эти символы можно задавать путем кодирования их шестнадцатеричных значений.  
  
1.  **Перед началом работы выполните следующие действия.**  [Ограничения](#LimitationsRestrictions)  
  
2.  **Обработка специальных символов:**  [кодирование идентификатора](#EncodeIdent), [декодирование идентификатора](#DecodeIdent)  
  
## Перед началом  
 Символы, неподдерживаемые в именах путей Windows PowerShell, могут быть представлены или закодированы в виде символа «%», за которым следует шестнадцатеричное значение для битового шаблона, представляющего символ, например «**%**xx». Для обработки символов, неподдерживаемых в обозначениях путей Windows PowerShell, всегда можно использовать кодировку.  
  
 Командлет **Encode-SqlName** принимает в качестве входных данных идентификатор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Он возвращает строку, в которой все символы, не поддерживаемые языком Windows PowerShell, закодированы в виде «%xx». Командлет **Decode-SqlName** принимает в качестве входных данных закодированный идентификатор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и возвращает исходный идентификатор.  
  
###  <a name="LimitationsRestrictions"></a> Ограничения  
 Командлеты **Encode-Sqlname** и **Decode-Sqlname** обеспечивают только кодирование или декодирование символов, допустимых в идентификаторах SQL Server с разделителями, но не поддерживаемых в путях PowerShell. Символы, кодируемые командлетом **Encode-SqlName** и декодируемые командлетом **Decode-SqlName**, перечислены ниже.  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|**Символ**|\|/|.|%|\<|>|*|?|[|]|&#124;|  
|**Шестнадцатеричная кодировка**|%5C|%2F|%3A|%25|%3C|%3E|%2A|%3F|%5B|%5D|%7C|  
  
##  <a name="EncodeIdent"></a> Кодирование идентификатора  
 **Кодирование идентификатора SQL Server в пути PowerShell**  
  
-   Используйте один из двух методов для кодирования идентификатора SQL Server:  
  
    -   Укажите шестнадцатеричный код для неподдерживаемого символа, используя синтаксис %XX, где XX — шестнадцатеричный код.  
  
    -   Передайте идентификатор в виде строки, заключенной в кавычки, в командлет **Encode-Sqlname**.  
  
### Примеры (кодирование)  
 В этом примере указана закодированная версия символа «:» (%3A):  
  
```  
Set-Location Table%3ATest  
```  
  
 Можно также использовать **Encode-SqlName** для формирования имени, поддерживаемого Windows PowerShell:  
  
```  
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="DecodeIdent"></a> Декодирование идентификатора  
 **Декодирование идентификатора SQL Server из пути PowerShell**  
  
 Используйте командлет **Decode-Sqlname** для замены шестнадцатеричных кодов символами, представленными этими кодами.  
  
### Примеры (декодирование)  
 В этом примере происходит возврат строки «Table:Test»:  
  
```  
Decode-SqlName "Table%3ATest"  
```  
  
## См. также:  
 [Идентификаторы SQL Server в PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell, поставщик](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  