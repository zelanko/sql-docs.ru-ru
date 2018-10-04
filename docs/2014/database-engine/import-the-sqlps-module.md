---
title: Импорт модуля SQLPS | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e687fd8c7fcd7c21f8aac9b546492a8f9bd4a644
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077244"
---
# <a name="import-the-sqlps-module"></a>Импорт модуля SQLPS
  Для управления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из PowerShell рекомендуется импортировать модуль `sqlps` в среду Windows PowerShell 2.0. Модуль загружает и регистрирует оснастки [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и сборки управляемости.  
  
1.  **Перед началом работы:** [Безопасность](#Security)  
  
2.  **Чтобы загрузить модуль:**  [Загрузка модуля sqlps](#LoadSqlps)  
  
## <a name="before-you-begin"></a>Перед началом  
 После импорта модуля `sqlps` в среду Windows PowerShell можно:  
  
-   Вводить команды Windows PowerShell в интерактивном режиме.  
  
-   Запускать файлы скриптов Windows PowerShell.  
  
-   Запускать командлеты служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Использовать пути поставщика служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для передвижения по иерархии объектов среды служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Для управления объектами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] используйте объектные модели управляемости [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (такие как Microsoft.SqlServer.Management.Smo).  
  
> [!NOTE]  
>  Команды, используемые в именах двух командлетов SQL Server (`Encode-Sqlname` и `Decode-Sqlname`), не соответствуют утвержденным командам для Windows PowerShell 2.0. Это не влияет на их работу, но Windows PowerShell выдает предупреждение при `sqlps` модуль импортируется в сеанс.  
  
###  <a name="Security"></a> безопасность  
 По умолчанию в Windows PowerShell политика выполнения скриптов работает в **ограниченном**режиме, блокируя все скрипты Windows PowerShell. Для загрузки модуля `sqlps` можно использовать командлет `Set-ExecutionPolicy`, чтобы включить запуск как подписанных, так и любых других скриптов. Следует выполнять только скрипты, полученные из доверенных источников, а также защищать все входные и выходные файлы, установив необходимые разрешения NTFS. Дополнительные сведения о включении скриптов Windows PowerShell см. в разделе [Выполнение скриптов Windows PowerShell](http://www.microsoft.com/technet/scriptcenter/topics/winpsh/manual/run.mspx).  
  
##  <a name="LoadSqlps"></a> Загрузка модуля sqlps  
 **Загрузка модуля sqlps в среду Windows PowerShell**  
  
1.  Используйте `Set-ExecutionPolicy` командлет, чтобы задать соответствующую политику выполнения скриптов.  
  
2.  Используйте `Import-Module` командлет, чтобы импортировать модуль sqlps. Укажите `DisableNameChecking` параметр, если вы хотите отключить предупреждение о `Encode-Sqlname` и `Decode-Sqlname`.  
  
### <a name="example-powershell"></a>Пример (PowerShell)  
 В этом примере показана загрузка модуля `sqlps` с отключенной проверкой имен.  
  
```  
## Import the SQL Server Module.  
  
Import-Module “sqlps” -DisableNameChecking  
  
```  
  

  
## <a name="see-also"></a>См. также  
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)   
 [SQL Server PowerShell, поставщик](../powershell/sql-server-powershell-provider.md)   
 [Использование командлетов компонента Database Engine](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
  
  
