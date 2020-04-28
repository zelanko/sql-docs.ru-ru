---
title: Шифрование и расшифровка идентификаторов SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 373b2b9d90512293e1776d06ab5797faaf47a210
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72797769"
---
# <a name="encode-and-decode-sql-server-identifiers"></a>Шифрование и расшифровка идентификаторов SQL Server
  Идентификаторы SQL Server с разделителями иногда содержат символы, не поддерживаемые в путях Windows PowerShell. Эти символы можно задавать путем кодирования их шестнадцатеричных значений.  
  
1.  **Перед началом работы выполните следующие действия.**  [Ограничения](#LimitationsRestrictions)  
  
2.  **Обработка специальных символов:**  [кодирование идентификатора](#EncodeIdent), [декодирование идентификатора](#DecodeIdent)  
  
## <a name="before-you-begin"></a>Перед началом  
 Символы, которые не поддерживаются в именах путей Windows PowerShell, могут быть представлены или закодированы как символ "%", за которым следует шестнадцатеричное значение для битового шаблона, представляющего символ, как**%** в "XX". Для обработки символов, неподдерживаемых в обозначениях путей Windows PowerShell, всегда можно использовать кодировку.  
  
 Командлет **Encode-SqlName** принимает в качестве входных данных идентификатор [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Он возвращает строку, в которой все символы, не поддерживаемые языком Windows PowerShell, закодированы в виде «%xx». Командлет **Decode-SqlName** принимает в качестве входных данных закодированный идентификатор [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и возвращает исходный идентификатор.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Ограничения  
 Командлеты `Encode-Sqlname` и `Decode-Sqlname` обеспечивают только кодирование или декодирование символов, допустимых в идентификаторах SQL Server с разделителями, но не поддерживаемых в путях PowerShell. Символы, кодируемые командлетом **Encode-SqlName** и декодируемые командлетом **Decode-SqlName**, перечислены ниже.  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|**Символ**|\ |/|:|%|\<|>|*|?|[|]|&#124;|  
|**Шестнадцатеричная кодировка**|%5C|%2F|%3A|%25|%3C|%3E|%2A|%3F|%5B|%5D|%7C|  
  
##  <a name="encoding-an-identifier"></a><a name="EncodeIdent"></a>Кодирование идентификатора  
 **Кодирование идентификатора SQL Server в пути PowerShell**  
  
-   Используйте один из двух методов для кодирования идентификатора SQL Server:  
  
    -   Укажите шестнадцатеричный код для неподдерживаемого символа, используя синтаксис %XX, где XX — шестнадцатеричный код.  
  
    -   Передайте идентификатор в виде строки, заключенной в кавычки, в командлет `Encode-Sqlname`  
  
### <a name="examples-encoding"></a>Примеры (кодирование)  
 В этом примере указана закодированная версия символа «:» (%3A):  
  
```  
Set-Location Table%3ATest  
```  
  
 Можно также использовать **Encode-SqlName** для формирования имени, поддерживаемого Windows PowerShell:  
  
```powershell
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="decoding-an-identifier"></a><a name="DecodeIdent"></a> декодирование идентификатора  
 **Декодирование идентификатора SQL Server из пути PowerShell**  
  
 Используйте командлет `Decode-Sqlname` для замены шестнадцатеричных кодов символами, представленными этими кодами.  
  
### <a name="examples-decoding"></a>Примеры (декодирование)  
 В этом примере происходит возврат строки Table:Test:  
  
```powershell
Decode-SqlName "Table%3ATest"  
```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server идентификаторов в PowerShell](sql-server-identifiers-in-powershell.md)   
 [Поставщик SQL Server PowerShell](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
