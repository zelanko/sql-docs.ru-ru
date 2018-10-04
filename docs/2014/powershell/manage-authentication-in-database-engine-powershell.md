---
title: Управление аутентификацией в PowerShell (ядро СУБД) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 61dbea86eabc0395b2f314f170aa97c5067880fd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163566"
---
# <a name="manage-authentication-in-database-engine-powershell"></a>Управление проверкой подлинности в компонент Database Engine PowerShell
  По умолчанию компоненты [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell используют при установлении соединения с компонентом [!INCLUDE[ssDE](../includes/ssde-md.md)]проверку подлинности Windows. Можно использовать проверку подлинности SQL Server, необходимо либо определить виртуальный диск PowerShell, либо указав `–Username` и `–Password` параметры `Invoke-Sqlcmd`.  
  
1.  **Перед началом работы выполните следующие действия.**  [Разрешения](#Permissions)  
  
2.  **To set authentication, using:**  [A Virtual Drive](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)  
  
##  <a name="Permissions"></a> Permissions  
 Все действия, которые могут быть выполнены на экземпляре компонента [!INCLUDE[ssDE](../includes/ssde-md.md)] , определяются разрешениями, предоставляемыми учетным данным, которые использовались при подключении к экземпляру. По умолчанию для подключения к компоненту [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с проверкой подлинности Windows поставщик [!INCLUDE[ssDE](../includes/ssde-md.md)]и командлеты используют учетную запись Windows, под которой они работают.  
  
 Для подключения с проверкой подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] необходимо указать идентификатор имени входа и пароль проверки подлинности SQL Server. При использовании [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поставщика, необходимо связать [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] учетные данные для входа с виртуальным диском, а затем используйте команду смены каталога (`cd`) для подключения к этому диску. В Windows PowerShell учетные данные безопасности можно связывать только с виртуальными дисками.  
  
##  <a name="SQLAuthVirtDrv"></a> Проверка подлинности SQL Server с помощью виртуального диска  
 **Создание виртуального диска с именем входа для проверки подлинности SQL Server**  
  
1.  Создайте функцию, которая:  
  
    1.  Имеет параметры для имени, назначаемого виртуальному диску, идентификатора имени входа и пути поставщика, который будет связан с виртуальным диском.  
  
    2.  Использует `read-host` для запроса ввода пароля.  
  
    3.  Использует `new-object` для создания объекта учетных данных.  
  
    4.  Использует `new-psdrive` для создания виртуального диска с указанными учетными данными.  
  
2.  Вызовите функцию, чтобы создать виртуальный диск с указанными учетными данными.  
  
### <a name="example-virtual-drive"></a>Пример (виртуальный диск)  
 В этом примере показано создание функции **sqldrive** для создания виртуального диска, который затем будет связан с указанным именем входа для проверки подлинности и экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Функция **sqldrive** запрашивает ввод пароля для имени входа, скрывая символы пароля при их вводе. При каждом использовании команды перехода в каталог (`cd`) для подключения к пути с помощью имени виртуального диска, все операции выполняются с помощью [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] учетные данные для входа проверки подлинности, которые были указаны при создании этого диска.  
  
```  
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = read-host -AsSecureString -Prompt "Password"  
    $cred = new-object System.Management.Automation.PSCredential -argumentlist $login,$pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="SQLAuthInvSqlCmd"></a> Проверка подлинности SQL Server с использованием Invoke-Sqlcmd  
 **Использование Invoke-Sqlcmd для проверки подлинности SQL Server**  
  
1.  Используйте `–Username` параметр для указания идентификатора входа и `–Password` параметр, чтобы указать соответствующий пароль.  
  
### <a name="example-invoke-sqlcmd"></a>Пример (Invoke-Sqlcmd)  
 В этом примере командлет read-host используется для запроса ввода пароля с последующим подключением с проверкой подлинности SQL Server.  
  
```  
## Prompt the user for their password.  
$pwd = read-host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" –Username “MyLogin” –Password $pwd  
```  
  
## <a name="see-also"></a>См. также  
 [SQL Server PowerShell](sql-server-powershell.md)   
 [SQL Server PowerShell, поставщик](sql-server-powershell-provider.md)   
 [Командлет Invoke-Sqlcmd](../database-engine/invoke-sqlcmd-cmdlet.md)  
  
  
