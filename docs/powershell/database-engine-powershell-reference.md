---
title: "Справочник по PowerShell для ядра СУБД | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dc3df1d697b05201ac48520c1e344c28648cdfaf
ms.lasthandoff: 04/11/2017

---
# <a name="database-engine-powershell-reference"></a>Справочник по PowerShell для ядра СУБД
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] включен набор командлетов Windows PowerShell для выполнения обычных действий в компоненте [!INCLUDE[ssDE](../includes/ssde-md.md)]. Кроме того, выражения запросов и универсальные имена ресурса (URN) можно преобразовать в пути SQL Server PowerShell либо использовать для указания одного или нескольких объектов в компоненте [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
## <a name="database-engine-cmdlets"></a>Командлеты ядра СУБД  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] включает в себя сравнительно мало командлетов для компонента [!INCLUDE[ssDE](../includes/ssde-md.md)]. Большинство скриптов Windows PowerShell, работающих с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)] , используют поставщика SQL Server PowerShell и объектные модели управляемости SQL Server. Дополнительные сведения см. в статье [SQL Server PowerShell Provider](../relational-databases/scripting/sql-server-powershell-provider.md).  
  
 Описание получения справки о командлетах SQL Server в среде Windows PowerShell см. в разделе [Get Help SQL Server PowerShell](../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
### <a name="in-this-section"></a>В этом разделе  
 В данном разделе содержатся сведения об этих командлетах.  
  
|Описание|Командлет|  
|-----------------|------------|  
|Выполняет скрипты Transact-SQL и XQuery, например скрипты, которые можно выполнить с помощью программы **sqlcmd** .|[Invoke-Sqlcmd, командлет](../powershell/invoke-sqlcmd-cmdlet.md)|  
|Определяет, соответствует ли объект ядра СУБД политике управления на основе политик.|[Invoke-PolicyEvaluation, командлет](../powershell/invoke-policyevaluation-cmdlet.md)|  
  
### <a name="information-about-other-cmdlets"></a>Сведения о других командлетах  
 Командлеты **Encode-Sqlname** и **Decode-Sqlname** помогают указать идентификаторы SQL Server, содержащие символы, не поддерживаемые в путях Windows PowerShell. Дополнительные сведения см. в статье [SQL Server Identifiers in PowerShell](../relational-databases/scripting/sql-server-identifiers-in-powershell.md).  
  
 Используйте командлет **Convert-UrnToPath** , чтобы преобразовать уникальное имя ресурса для объекта компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] в путь для поставщика SQL Server PowerShell. Дополнительные сведения см. в статье [Convert URNs to SQL Server Provider Paths](../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md).  
  
## <a name="query-expressions-and-unique-resource-names"></a>Выражения запросов и уникальные имена ресурсов  
 Выражения запроса — это строки, которые используют синтаксис, напоминающий XPath для указания набора условий, перечисляющих один или несколько объектов в иерархии объектной модели. Уникальное имя ресурса (URN) — это определенный тип строки выражения запроса, который уникально определяет один объект. Дополнительные сведения см. в статье [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).  
  
## <a name="see-also"></a>См. также:  
 [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)  
  
  
