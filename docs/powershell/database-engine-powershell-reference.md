---
title: "Справочник по компоненту Database Engine PowerShell | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Справочник по компоненту Database Engine PowerShell
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] включен набор командлетов Windows PowerShell для выполнения обычных действий в компоненте [!INCLUDE[ssDE](../includes/ssde-md.md)]. Кроме того, выражения запросов и универсальные имена ресурса (URN) можно преобразовать в пути SQL Server PowerShell либо использовать для указания одного или нескольких объектов в компоненте [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
## Командлеты Database Engine  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] включает в себя сравнительно мало командлетов для компонента [!INCLUDE[ssDE](../includes/ssde-md.md)]. Большинство скриптов Windows PowerShell, работающих с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)] , используют поставщика SQL Server PowerShell и объектные модели управляемости SQL Server. Дополнительные сведения см. в статье [SQL Server PowerShell Provider](../relational-databases/scripting/sql-server-powershell-provider.md).  
  
 Описание получения справки о командлетах SQL Server в среде Windows PowerShell см. в разделе [Get Help SQL Server PowerShell](../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
### В этом разделе  
 В данном разделе содержатся сведения об этих командлетах.  
  
|Описание|Командлет|  
|-----------------|------------|  
|Выполняет скрипты Transact-SQL и XQuery, например скрипты, которые можно выполнить с помощью программы **sqlcmd**.|[Invoke-Sqlcmd, командлет](../powershell/invoke-sqlcmd-cmdlet.md)|  
|Определяет, соответствует ли объект компонента Database Engine политике управления на основе политик.|[Invoke-PolicyEvaluation, командлет](../powershell/invoke-policyevaluation-cmdlet.md)|  
  
### Сведения о других командлетах  
 Командлеты **Encode-Sqlname** и **Decode-Sqlname** помогают указать идентификаторы SQL Server, содержащие символы, не поддерживаемые в путях Windows PowerShell. Дополнительные сведения см. в статье [SQL Server Identifiers in PowerShell](../relational-databases/scripting/sql-server-identifiers-in-powershell.md).  
  
 Используйте командлет **Convert-UrnToPath**, чтобы преобразовать уникальное имя ресурса для объекта компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] в путь для поставщика SQL Server PowerShell. Дополнительные сведения см. в статье [Convert URNs to SQL Server Provider Paths](../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md).  
  
## Выражения запросов и уникальные имена ресурсов  
 Выражения запроса — это строки, которые используют синтаксис, напоминающий XPath для указания набора условий, перечисляющих один или несколько объектов в иерархии объектной модели. Уникальное имя ресурса (URN) — это определенный тип строки выражения запроса, который уникально определяет один объект. Дополнительные сведения см. в статье [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).  
  
## См. также:  
 [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)  
  
  