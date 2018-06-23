---
title: Импорт модуля SQLPS | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
caps.latest.revision: 9
author: mgblythe
ms.author: mblythe
manager: jhubbard
ms.openlocfilehash: 8c20daf51270931609fb876b9a7035da343d19f7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101807"
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
>  Команды, используемые в именах двух командлетов SQL Server (`Encode-Sqlname` и `Decode-Sqlname`), не соответствуют утвержденным командам для Windows PowerShell 2.0. Это не влияет на их работу, однако Windows PowerShell выдает предупреждение при `sqlps` модуль импортируется в сеанс.  
  
###  <a name="Security"></a> безопасность  
 По умолчанию в Windows PowerShell политика выполнения скриптов работает в **ограниченном**режиме, блокируя все скрипты Windows PowerShell. Для загрузки модуля `sqlps` можно использовать командлет `Set-ExecutionPolicy`, чтобы включить запуск как подписанных, так и любых других скриптов. Следует выполнять только скрипты, полученные из доверенных источников, а также защищать все входные и выходные файлы, установив необходимые разрешения NTFS. Дополнительные сведения о включении скриптов Windows PowerShell см. в разделе [Выполнение скриптов Windows PowerShell](http://www.microsoft.com/technet/scriptcenter/topics/winpsh/manual/run.mspx).  
  
##  <a name="LoadSqlps"></a> Загрузка модуля sqlps  
 **Загрузка модуля sqlps в среду Windows PowerShell**  
  
1.  Используйте `Set-ExecutionPolicy` командлету задать соответствующую политику выполнения скриптов.  
  
2.  Используйте `Import-Module` для импорта модуля sqlps. Укажите `DisableNameChecking` параметра, если требуется отключить предупреждение о `Encode-Sqlname` и `Decode-Sqlname`.  
  
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
  
  