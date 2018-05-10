---
title: PowerShell для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql
ms.prod_service: powershell
ms.component: powershell
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 89b70725-bbe7-4ffe-a27d-2a40005a97e7
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c8736ee258f072685bd7919b98c15a5704873fbb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-powershell"></a>SQL Server PowerShell
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

**[Установка компонентов SQL Server PowerShell](download-sql-server-ps-module.md)**

> [!NOTE]
> Существует два модуля SQL Server PowerShell — **SqlServer** и **SQLPS**. Модуль **SQLPS** входит в состав установки SQL Server (для обеспечения обратной совместимости), но больше не обновляется. Самым актуальным модулем PowerShell является модуль **SqlServer**. Модуль **SqlServer** содержит обновленные версии командлетов в **SQLPS**, а также новые командлеты для поддержки последних функций SQL.  
> Предыдущие версии модуля **SqlServer** *входили* в состав среды SQL Server Management Studio (SSMS), но только с SSMS версий 16.x. Для работы PowerShell с SSMS 17.0 и более поздних версий необходимо установить модуль **SqlServer** из коллекции PowerShell.
> Сведения об установке модуля **SqlServer** см. в статье [Установка компонентов SQL Server PowerShell](download-sql-server-ps-module.md).

**Почему модуль SQLPS изменился на SqlServer?**

Для поставки обновлений SQL PowerShell было необходимо изменить удостоверение модуля SQL PowerShell, а также программу-оболочку, известную как *SQLPS.exe*. В связи с эти изменением теперь существует два модуля SQL PowerShell — модуль **SqlServer** и модуль **SQLPS**.  

**Обновите скрипты PowerShell, если они импортируют модуль SQLPS.**

Если у вас есть скрипты PowerShell, которые выполняют команду `Import-Module -Name SQLPS`, и вы хотите использовать преимущества новых функциональных возможностей поставщика и новых командлетов, необходимо изменить их на `Import-Module -Name SqlServer`. Новый модуль устанавливается в папку `%ProgramFiles%\WindowsPowerShell\Modules\SqlServer`. Поэтому не нужно обновлять переменную $env:PSModulePath. При наличии скриптов, использующих версии модуля **SqlServer** сторонних производителей или сообщества следует использовать параметр Prefix, чтобы избежать конфликтов имен. Модуль, используемый агентом SQL Server, не изменился. 

  
## <a name="sql-server-powershell-components"></a>Компоненты SQL Server PowerShell  
Модуль **SqlServer** загружает две оснастки Windows PowerShell.  
  
-   Поставщик [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , который предоставляет простой механизм навигации, аналогичный путям в файловой системе. Можно построить пути, аналогичные путям файловой системы, где диску соответствует управляющая объектная модель [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , а узлы основаны на классах объектной модели. Затем можно использовать привычные команды, такие как **cd** и **dir** , чтобы перемещаться по путям, аналогично переходу по структуре папок в окне командной строки. Для выполнения действий на узлах пути можно использовать другие команды, например **ren** или **del**.  
  
-   Набор командлетов, которые поддерживают такие действия, как запуск скрипта **sqlcmd**, содержащего инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] или XQuery.  
  
  
## <a name="sql-server-versions"></a>SQL Server, версии  
Командлеты SQL PowerShell можно использовать для управления экземплярами базы данных SQL Azure, хранилища данных SQL Azure и во всех [поддерживаемых продуктов SQL Server](https://support.microsoft.com/lifecycle/search/1044).  


## <a name="sql-server-identifiers-that-contain-characters-not-supported-in-powershell-paths"></a>Идентификаторы SQL Server, содержащие символы, не поддерживаемые в путях Windows PowerShell  
 
Командлеты **Encode-Sqlname** и **Decode-Sqlname** помогают указать идентификаторы SQL Server, содержащие символы, не поддерживаемые в путях Windows PowerShell. Дополнительные сведения см. в статье [SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md).  
  
Используйте командлет **Convert-UrnToPath** , чтобы преобразовать уникальное имя ресурса для объекта компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] в путь для поставщика SQL Server PowerShell. Дополнительные сведения см. в статье [Convert URNs to SQL Server Provider Paths](https://docs.microsoft.com/powershell/module/sqlserver/Convert-UrnToPath).  
  
## <a name="query-expressions-and-unique-resource-names"></a>Выражения запросов и уникальные имена ресурсов  

Выражения запроса — это строки, которые используют синтаксис, напоминающий XPath для указания набора условий, перечисляющих один или несколько объектов в иерархии объектной модели. Уникальное имя ресурса (URN) — это определенный тип строки выражения запроса, который уникально определяет один объект. Дополнительные сведения см. в статье [Query Expressions and Uniform Resource Names](query-expressions-and-uniform-resource-names.md).       


## <a name="cmdlet-reference"></a>Справочник по командлетам
* [Командлеты SqlServer](https://docs.microsoft.com/powershell/module/sqlserver)
* [Командлеты SQLPS](https://docs.microsoft.com/powershell/module/sqlps)
