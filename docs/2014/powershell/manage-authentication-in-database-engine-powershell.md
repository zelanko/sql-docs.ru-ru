---
title: Управление аутентификацией в PowerShell (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a04e581758748d55b9defcab3beaa6a86f0eecf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "72797796"
---
# <a name="manage-authentication-in-database-engine-powershell"></a>Управление проверкой подлинности в компонент Database Engine PowerShell
  По умолчанию компоненты [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell используют при установлении соединения с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)]проверку подлинности Windows. Для использования проверки подлинности SQL Server необходимо либо определить виртуальный диск PowerShell, либо указать параметры `-Username` и `-Password` для `Invoke-Sqlcmd`.  
  
1.  **Перед началом работы выполните следующие действия.**  [Разрешения](#Permissions)  
  
2.  **To set authentication, using:**  [A Virtual Drive](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)  
  
##  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Все действия, которые могут быть выполнены на экземпляре компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , определяются разрешениями, предоставляемыми учетным данным, которые использовались при подключении к экземпляру. По умолчанию для подключения к компоненту [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с проверкой подлинности Windows поставщик [!INCLUDE[ssDE](../includes/ssde-md.md)]и командлеты используют учетную запись Windows, под которой они работают.  
  
 Для подключения с проверкой подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] необходимо указать идентификатор имени входа и пароль проверки подлинности SQL Server. При использовании [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поставщика необходимо связать учетные данные [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] входа с виртуальным диском, а затем использовать команду Change Directory (`cd`) для подключения к этому диску. В Windows PowerShell учетные данные безопасности можно связывать только с виртуальными дисками.  
  
##  <a name="sql-server-authentication-using-a-virtual-drive"></a><a name="SQLAuthVirtDrv"></a> Проверка подлинности SQL Server с помощью виртуального диска  
 **Создание виртуального диска с именем входа для проверки подлинности SQL Server**  
  
1.  Создайте функцию, которая:  
  
    1.  Имеет параметры для имени, назначаемого виртуальному диску, идентификатора имени входа и пути поставщика, который будет связан с виртуальным диском.  
  
    2.  Использует `read-host` для запроса ввода пароля.  
  
    3.  Использует `new-object` для создания объекта учетных данных.  
  
    4.  Использует `new-psdrive` для создания виртуального диска с указанными учетными данными.  
  
2.  Вызовите функцию, чтобы создать виртуальный диск с указанными учетными данными.  
  
### <a name="example-virtual-drive"></a>Пример (виртуальный диск)  
 В этом примере показано создание функции **sqldrive** для создания виртуального диска, который затем будет связан с указанным именем входа для проверки подлинности и экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Функция **sqldrive** запрашивает ввод пароля для имени входа, скрывая символы пароля при их вводе. Затем, когда вы используете команду Change Directory (`cd`) для подключения к пути с помощью имени виртуального диска, все операции выполняются с использованием учетных данных входа для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] проверки подлинности, которые были указаны при создании диска.  
  
```powershell
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = Read-Host -AsSecureString -Prompt "Password"  
    $cred = New-Object System.Management.Automation.PSCredential -argumentlist $login, $pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="sql-server-authentication-using-invoke-sqlcmd"></a><a name="SQLAuthInvSqlCmd"></a> Проверка подлинности SQL Server с использованием Invoke-Sqlcmd  
 **Использование Invoke-Sqlcmd для проверки подлинности SQL Server**  
  
1.  Укажите идентификатор имени входа с помощью параметра `-Username`, а связанный с ним пароль — с помощью параметра `-Password`.  
  
### <a name="example-invoke-sqlcmd"></a>Пример (Invoke-Sqlcmd)  
 В этом примере командлет read-host используется для запроса ввода пароля с последующим подключением с проверкой подлинности SQL Server.  
  
```powershell
## Prompt the user for their password.  
$pwd = Read-Host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" -Username "MyLogin" -Password $pwd  
```  
  
## <a name="see-also"></a>См. также:  
 [SQL Server PowerShell](sql-server-powershell.md)   
 [Поставщик SQL Server PowerShell](sql-server-powershell-provider.md)   
 [Invoke-Sqlcmd, командлет](../database-engine/invoke-sqlcmd-cmdlet.md)  
