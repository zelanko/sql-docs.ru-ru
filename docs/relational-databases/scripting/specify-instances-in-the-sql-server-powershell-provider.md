---
title: "Указание экземпляров в поставщике PowerShell (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: ssms
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9373de68-fd43-45f2-b9a6-149c96610aeb
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 409654f138f1ac9628822d824c431cea504d2c0f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="specify-instances-in-the-sql-server-powershell-provider"></a>Указание экземпляров в поставщике SQL Server PowerShell
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Пути, указанные для поставщика SQL Server для PowerShell, должны идентифицировать экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и компьютер, на котором он запущен. Синтаксическая конструкция для указания компьютера и экземпляра должна соответствовать правилам для идентификаторов SQL Server и путям Windows PowerShell.  
  
1.  **Перед началом работы выполните следующие действия.**  [Ограничения](#LimitationsRestrictions)  
  
2.  **Указание экземпляра:**  [Примеры](#Examples)  
  
## <a name="before-you-begin"></a>Перед началом  
 Первый узел, следующий за SQLSERVER:\SQL в пути поставщика SQL Server, является именем компьютера, на котором выполняется экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], например:  
  
```  
SQLSERVER:\SQL\MyComputer  
```  
  
 Если среда Windows PowerShell установлена на одном компьютере с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], то вместо имени компьютера можно использовать localhost или (local). Скрипты, в которых указано localhost или (local), можно выполнять на любом компьютере, при этом изменять их путем внесения имен разных компьютеров не требуется.  
  
 На одном и том же компьютере можно запустить несколько экземпляров исполняемой программы компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Узел после имени компьютера в пути поставщика SQL Server определяет экземпляр, например:  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance  
```  
  
 На каждом компьютере может быть только один экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]по умолчанию. При установке экземпляра по умолчанию указывать для него имя не нужно. При указании в строке соединения только имени компьютера происходит подключение к экземпляру по умолчанию на этом компьютере. Все прочие экземпляры на компьютере должны быть именованными. Имя экземпляра указывается во время установки, а в строке подключения необходимо указывать и имя компьютера, и имя экземпляра.  
  
###  <a name="LimitationsRestrictions"></a> Ограничения  
 Для указания локального компьютера в скриптах PowerShell нельзя использовать точку (.). Точка не поддерживается, так как PowerShell интерпретирует точку как команду.  
  
 Windows PowerShell обычно обрабатывает символы скобок в (local) как команды. Необходимо либо закодировать, либо экранировать их при использовании в пути, или заключить путь в двойные кавычки. Дополнительные сведения см. в разделе «Шифрование и расшифровка идентификаторов SQL Server».  
  
 Для поставщика [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда необходимо указывать имя экземпляра. Для экземпляров по умолчанию необходимо указывать имя DEFAULT.  
  
##  <a name="Examples"></a> Примеры; имена компьютеров и экземпляров  
 В этом примере серверный объект устанавливается на экземпляр по умолчанию на локальном компьютере:  
  
```  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT   
```  
  
 Windows PowerShell обычно обрабатывает символы скобок в (local) как команды. Необходимо:  
  
-   заключить строку пути в кавычки;  
  
    ```  
    Set-Location "SQLSERVER:\SQL\(local)\DEFAULT"  
    ```  
  
-   экранировать скобки при помощи символа обратной кавычки (`);  
  
    ```  
    Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
    ```  
  
-   зашифровать скобки с помощью шестнадцатеричного представления:  
  
    ```  
    Set-Location SQLSERVER:\SQL\%28local%29\DEFAULT  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Идентификаторы SQL Server в PowerShell](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell, поставщик](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  
