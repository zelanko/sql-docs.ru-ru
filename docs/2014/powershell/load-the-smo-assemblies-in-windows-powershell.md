---
title: Загрузка сборки объектов SMO в Windows PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8ca42b69-da5a-47f4-9085-34e443f0e389
author: stevestein
ms.author: sstein
ms.openlocfilehash: dc5d5f1a11603dac8e3d4aa075ccceb784d8ae15
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84960424"
---
# <a name="load-the-smo-assemblies-in-windows-powershell"></a>Загрузка сборки объектов SMO в Windows PowerShell
  В данном разделе описана загрузка сборок управляющих объектов SQL Server (SMO) в скриптах Windows PowerShell, не использующих поставщик SQL Server для PowerShell.  
  
## <a name="before-you-begin"></a>Перед началом  
 Рекомендуемым механизмом загрузки сборок объектов SMO является загрузка модуля `sqlps`. Поставщик [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , включенный в этот модуль, автоматически загружает сборки объектов SMO, а также реализует функции, расширяющие степень полезности объектов в скриптах PowerShell.  
  
 В двух следующих случаях, возможно, понадобится загрузить сборки объектов SMO напрямую.  
  
-   Если скрипт ссылается на объект SMO перед первой командой, ссылающейся на поставщика, или командлетами из оснасток [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Код объектов SMO переносится из другого языка, такого как C# или Visual Basic, который не использует этот поставщик или командлеты.  
  
## <a name="example-loading-the-sql-server-management-objects"></a>Пример. Загрузка управляющих объектов SQL Server  
 Следующий код загружает сборки объектов SMO:  
  
```powershell
# Loads the SQL Server Management Objects (SMO)  
  
$ErrorActionPreference = "Stop"  
  
$sqlpsreg = "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.SqlServer.Management.PowerShell.sqlps"  
  
if (Get-ChildItem $sqlpsreg -ErrorAction "SilentlyContinue")  
{  
    throw "SQL Server Provider for Windows PowerShell is not installed."  
}  
else  
{  
    $item = Get-ItemProperty $sqlpsreg  
    $sqlpsPath = [System.IO.Path]::GetDirectoryName($item.Path)  
}  
  
$assemblylist =   
"Microsoft.SqlServer.Management.Common",  
"Microsoft.SqlServer.Smo",  
"Microsoft.SqlServer.Dmf ",  
"Microsoft.SqlServer.Instapi ",  
"Microsoft.SqlServer.SqlWmiManagement ",  
"Microsoft.SqlServer.ConnectionInfo ",  
"Microsoft.SqlServer.SmoExtended ",  
"Microsoft.SqlServer.SqlTDiagM ",  
"Microsoft.SqlServer.SString ",  
"Microsoft.SqlServer.Management.RegisteredServers ",  
"Microsoft.SqlServer.Management.Sdk.Sfc ",  
"Microsoft.SqlServer.SqlEnum ",  
"Microsoft.SqlServer.RegSvrEnum ",  
"Microsoft.SqlServer.WmiEnum ",  
"Microsoft.SqlServer.ServiceBrokerEnum ",  
"Microsoft.SqlServer.ConnectionInfoExtended ",  
"Microsoft.SqlServer.Management.Collector ",  
"Microsoft.SqlServer.Management.CollectorEnum",  
"Microsoft.SqlServer.Management.Dac",  
"Microsoft.SqlServer.Management.DacEnum",  
"Microsoft.SqlServer.Management.Utility"  
  
foreach ($asm in $assemblylist)  
{  
    $asm = [Reflection.Assembly]::LoadWithPartialName($asm)  
}  
  
Push-Location  
cd $sqlpsPath  
Update-FormatData -PrependPath SQLProvider.Format.ps1xml
Pop-Location  
```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server PowerShell](sql-server-powershell.md)  
