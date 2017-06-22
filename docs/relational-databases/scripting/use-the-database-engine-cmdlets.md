---
title: "Использование командлетов ядра СУБД | Документация Майкрософт"
ms.custom: 
ms.date: 08/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Convert-UrnToPath cmdlet
- PowerShell [SQL Server], cmdlets
- Cmdlets [SQL Server]
- PowerShell [SQL Server], Convert-UrnToPath
- Cmdlets [SQL Server], Convert-UrnToPath
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 720aa982-09ae-41a3-b603-a91004cfbe3e
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 457781b7e16a5722f4d232cff14b8f20c7651972
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="use-the-database-engine-cmdlets"></a>Использование командлетов компонента Database Engine
  Командлеты Windows PowerShell представляют собой команды из одной функции, в именах которых, как правило, используется соглашение об именовании "глагол-существительное", например **Get-Help** или **Set-MachineName**. Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для Windows PowerShell предоставляет командлеты, относящиеся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="database-engine-cmdlets"></a>Командлеты Database Engine  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реализовано небольшое количество командлетов для компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Эти командлеты в основном используются для запуска существующих скриптов Transact-SQL из новых скриптов PowerShell, оценки политик управления на основе политик и помощи в задании идентификаторов SQL Server в путях поставщика SQL Server.  
  
 Большинство скриптов Windows PowerShell работают с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] , используя поставщик SQL Server PowerShell и объектные модели управляемости SQL Server. Дополнительные сведения см. в статье [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md).  
  
### <a name="get-cmdlet-help"></a>Получение справки по командлету  
 В среде Windows PowerShell справочные сведения о каждом командлете можно получить с помощью командлета **Get-Help** . Командлет**Get-Help** возвращает такую информацию, как синтаксис, определения параметров, типы входных и выходных данных, а также описание действий, выполняемых командлетом. Дополнительные сведения см. в разделе [Get Help SQL Server PowerShell](../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
### <a name="partial-parameter-names"></a>Частичные имена параметров  
 Полное имя параметра командлета указывать не обязательно. Необходимо только указать достаточную часть имени, чтобы уникально отделить его от других параметров, поддерживаемых данным командлетом. В следующих примерах показано три способа задания параметра **Invoke-Sqlcmd -QueryTimeout** :  
  
```  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTimeout 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTime 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryT 3  
```  
  
## <a name="database-engine-cmdlet-tasks"></a>Задачи командлета Database Engine  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описывает использование командлета **Invoke-Sqlcmd** для выполнения скриптов **sqlcmd** или команд, содержащих инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] или XQuery. Он может принимать входные данные **sqlcmd** в виде символьного строкового входного параметра или имени открываемого файла скрипта.|[Invoke-Sqlcmd, командлет](../../powershell/invoke-sqlcmd-cmdlet.md)|  
|Описывает использование командлета **Invoke-PolicyEvaluation** для сообщения о том, соответствует ли целевой набор объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] условиям, определенным в схемах управления на основе политик. Кроме того, этот командлет можно использовать для повторного задания любых настраиваемых параметров в целевых объектах, которые не соответствуют условиям политики.|[Invoke-PolicyEvaluation, командлет](../../powershell/invoke-policyevaluation-cmdlet.md)|  
|Описывает использование командлетов **Encode-Sqlname** и **Decode-Sqlname** для обработки идентификаторов SQL Server, содержащих символы, не поддерживаемые в путях Windows PowerShell.|[Шифрование и расшифровка идентификаторов SQL Server](../../relational-databases/scripting/encode-and-decode-sql-server-identifiers.md)|  
|Описывает использование командлета **Convert-UrnToPath** для преобразования универсального имени ресурса (URN) объекта управляемости SQL Server в эквивалентный путь поставщика SQL Server.|[Преобразование универсальных имен ресурса в пути поставщика SQL Server](../../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md)|  
  
## <a name="see-also"></a>См. также:  
 [SQL Server PowerShell, поставщик](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
[Обзор командлетов PowerShell для групп доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)
  
  

