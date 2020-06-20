---
title: Справочник по PowerShell для ядра СУБД | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5412b8a96f79f0c33206c794090916732ef016a8
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934475"
---
# <a name="database-engine-powershell-reference"></a>Справочник по PowerShell для ядра СУБД
  В состав [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] включен набор командлетов Windows PowerShell 2.0 для выполнения обычных действий в компоненте [!INCLUDE[ssDE](../includes/ssde-md.md)]. Кроме того, выражения запросов и универсальные имена ресурса (URN) можно преобразовать в пути SQL Server PowerShell либо использовать для указания одного или нескольких объектов в компоненте [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
## <a name="database-engine-cmdlets"></a>Командлеты Database Engine  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] включает в себя сравнительно мало командлетов для компонента [!INCLUDE[ssDE](../includes/ssde-md.md)]. Большинство скриптов Windows PowerShell, работающих с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)] , используют поставщика SQL Server PowerShell и объектные модели управляемости SQL Server. Дополнительные сведения см. в статье [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md).  
  
 Описание получения справки о командлетах SQL Server в среде Windows PowerShell см. в разделе [Get Help SQL Server PowerShell](../powershell/sql-server-powershell.md).  
  
### <a name="in-this-section"></a>В этом разделе  
 В данном разделе содержатся сведения об этих командлетах.  
  
|Описание|Командлет|  
|-----------------|------------|  
|Выполняет скрипты Transact-SQL и XQuery, например скрипты, которые можно выполнить с помощью программы `sqlcmd`.|[Invoke-Sqlcmd, командлет](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|Определяет, соответствует ли объект компонента Database Engine политике управления на основе политик.|[Invoke-PolicyEvaluation, командлет](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
  
### <a name="information-about-other-cmdlets"></a>Сведения о других командлетах  
 Командлеты `Encode-Sqlname` и `Decode-Sqlname` помогают указать идентификаторы SQL Server, содержащие символы, не поддерживаемые в путях Windows PowerShell. Дополнительные сведения см. в статье [SQL Server Identifiers in PowerShell](../powershell/sql-server-identifiers-in-powershell.md).  
  
 Используйте командлет `Convert-UrnToPath`, чтобы преобразовать уникальное имя ресурса для объекта компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] в путь для поставщика SQL Server PowerShell. Дополнительные сведения см. в статье [Convert URNs to SQL Server Provider Paths](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md).  
  
## <a name="query-expressions-and-unique-resource-names"></a>Выражения запросов и уникальные имена ресурсов  
 Выражения запроса — это строки, которые используют синтаксис, напоминающий XPath для указания набора условий, перечисляющих один или несколько объектов в иерархии объектной модели. Уникальное имя ресурса (URN) — это определенный тип строки выражения запроса, который уникально определяет один объект. Дополнительные сведения см. в статье [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).  
  
## <a name="see-also"></a>См. также:  
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  
  
  
