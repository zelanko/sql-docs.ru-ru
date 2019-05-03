---
title: Настройка SQL Server в установке Server Core | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- IsHadrEnabled server property
- Server Core Installation [SQL Server]
ms.assetid: ed6e5e94-4b8d-422a-a17e-61b05a4df903
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e8134b7a69df7254ce3609ddce24a15293c47efd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779737"
---
# <a name="configure-sql-server-on-a-server-core-installation"></a>Настройка SQL Server на установке Server Core
  Этот раздел содержит сведения о настройке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на установке Server Core из [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] с пакетом обновления 1 (SP1). 
  
##  <a name="configure-and-manage-server-core-on-windows-server"></a>Настройка и управление Server Core в Windows Server  
 Раздел содержит ссылки на разделы, в которых приведены сведения о настройке установки Server Core и управлении ей.  
  
 Не все компоненты [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] поддерживаются в режиме Server Core.  Некоторые из этих компонентов могут быть установлены на клиентском компьютере или другом сервере, на котором нет Server Core, и подключены к службам компонента ядра СУБД, установленным в Server Core.  
  
 Дополнительные сведения о дистанционной настройке и управлении установкой Server Core см. в следующих разделах:  
  
-   [Windows Server 2008 R2: Рекомендации по развертыванию ядра сервера](https://go.microsoft.com/fwlink/?LinkID=245957) (https://go.microsoft.com/fwlink/?LinkID=245957)  
  
-   [Настройка установки Server Core: Общие сведения о](https://go.microsoft.com/fwlink/?LinkId=245958) (https://go.microsoft.com/fwlink/?LinkId=245958)  
  
-   [Настройка установки Server Core Windows Server 2008 R2 с помощью Sconfig.cmd](https://go.microsoft.com/fwlink/?LinkId=245959) (https://go.microsoft.com/fwlink/?LinkId=245959)  
  
-   [Установка роли сервера на сервере под управлением установки Server Core Windows Server 2008 R2: Общие сведения о](https://go.microsoft.com/fwlink/?LinkId=245960) (https://go.microsoft.com/fwlink/?LinkId=245960)  
  
-   [Установка компонентов Windows на сервере под управлением установки Server Core Windows Server 2008 R2: Общие сведения о](https://go.microsoft.com/fwlink/?LinkId=245961) (https://go.microsoft.com/fwlink/?LinkId=245961)  
  
-   [Управление установкой Server Core. Общие сведения о](https://go.microsoft.com/fwlink/?LinkId=245962) (https://go.microsoft.com/fwlink/?LinkId=245962)  
  
-   [Администрирование установки Server Core](https://go.microsoft.com/fwlink/?LinkId=245963) (https://go.microsoft.com/fwlink/?LinkId=245963)  
  
##  <a name="install-updates"></a>Установка обновлений  
 Этот раздел содержит сведения об установке обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на компьютере под управлением Windows Server Core. Пользователям рекомендуется своевременно оценивать и устанавливать последние обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы обеспечить наличие последних обновлений безопасности для систем. Дополнительные сведения об установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на компьютере под управлением Windows Server Core см. в разделе [Установка SQL Server 2014 на Server Core](install-sql-server-on-server-core.md).  
  
 Ниже приведены два сценария для установки обновлений продукта.  
  
-   [Установка обновлений для SQL Server 2014 во время новой установки](#installing-updates-during-a-new-installation) 
  
-   [Установка обновлений для SQL Server 2014, после установки](#installing-updates-after-installation) 
  
### <a name="installing-updates-during-a-new-installation"></a>Установка обновлений во время новой установки  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает только установку из командной строки в операционной системе Server Core. Дополнительные сведения см. в статье [Установка SQL Server 2014 из командной строки](install-sql-server-from-the-command-prompt.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объединяет последние обновления продукта с установкой основного продукта, чтобы он и применимые обновления устанавливались одновременно.  
  
 Когда программа установки обнаруживает последние версии соответствующих обновлений, эти обновления загружаются и интегрируются в текущую процедуру установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Функция обновления продукта может включить в установку пакет обновления, накопительное обновление или и то и другое.  
  
 Укажите параметры UpdateEnabled и UpdateSource, чтобы ввести последние обновления продукта в установку основного продукта. В следующем примере показано, как выполнить обновления продукта в процессе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```sql  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /UpdateEnabled=True /UpdateSource="<SourcePath>" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
### <a name="installing-updates-after-installation"></a>Установка обновлений после установки 
 В установленном экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]рекомендуется установить последние обновления безопасности и критические обновления, в том числе выпуски для общего распространения (GDR) и пакеты обновления (SP). Отдельные накопительные обновления и обновления безопасности следует устанавливать в каждом отдельном случае по мере необходимости. Оцените необходимость обновления и установите его, если это требуется.  
  
 Применение обновления из командной строки. Замените <package_name> именем конкретного пакета обновления.  
  
-   Обновление одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и всех общих компонентов. Можно указать экземпляр с помощью параметра InstanceName или параметра InstanceID.  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance  
    ```  
  
-   Обновление только общих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch  
    ```  
  
-   Обновление всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере и всех общих компонентов.  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances  
    ```  
  
##  <a name="startstop-sql-server-service"></a>Службы SQL Server для запуска и остановки  
 [Приложение sqlservr](../../tools/sqlservr-application.md) позволяет запускать, останавливать, приостанавливать и возобновлять работу экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из командной строки.  
  
 Для запуска и остановки служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно также использовать службы Net.  
  
## <a name="enable-alwayson-availability-groups"></a>Включение групп доступности AlwaysOn  
 Включение групп доступности AlwaysOn является предварительным требованием для экземпляра сервера, чтобы использовать группы доступности в качестве решения высокого уровня доступности и аварийного восстановления. Дополнительные сведения об управлении группами доступности AlwaysOn см. в разделе [Включение и отключение групп доступности AlwaysOn (SQL Server)](../availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).  
  
### <a name="using-sql-server-configuration-manager-remotely"></a>Удаленное использование диспетчера конфигурации SQL Server  
 Эти действия предназначены для выполнения на компьютере под управлением клиентской редакции [!INCLUDE[win7](../../includes/win7-md.md)] или более поздней версии или на другом сервере, где установлена графическая оболочка сервера (т. е. полной установки [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] или Windows 8 с включенным компонентом графической оболочки сервера).  
  
1.  Откройте оснастку «Управление компьютером». Чтобы открыть оснастку «Управление компьютером», выполните одно из следующих действий.  
  
    1.  В [!INCLUDE[win7](../../includes/win7-md.md)], Windows Server 2008 и [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]:  
  
        1.  Нажмите кнопку «Пуск», выберите «Все программы», «Администрирование» и выберите пункт «Управление компьютером».  
  
        2.  Нажмите кнопку «Пуск», выберите команду «Выполнить», введите COMPMGMT.MSC и нажмите кнопку «ОК».  
  
    2.  В Windows 8 с включенной графической оболочкой сервера:  
  
        1.  Переместите курсор мыши в нижний левый угол экрана и щелкните правой кнопкой мыши при появлении дополнительного значка «Пуск».  
  
        2.  Выберите пункт «Управление компьютером» в контекстном меню.  
  
2.  В дереве консоли щелкните правой кнопкой мыши «Управление компьютером», а затем выберите «Подключение к другому компьютеру».  
  
3.  В диалоговом окне «Выбор компьютера» введите имя компьютера Server Core, которым необходимо управлять, или нажмите кнопку «Обзор», чтобы найти его, а затем нажмите кнопку «ОК».  
  
4.  В дереве консоли в разделе «Управление компьютером» компьютера Server Core выберите «Службы и приложения».  
  
5.  Дважды щелкните диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
6.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager последовательно щелкните [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы, щелкните правой кнопкой мыши [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (\<имя экземпляра >), где \<имя экземпляра > — имя локального экземпляра сервера для которого вы хотите включить AlwaysOn Группы доступности и выберите пункт Свойства.  
  
7.  Перейдите на вкладку Высокий уровень доступности AlwaysOn.  
  
8.  Убедитесь, что поле Имя отказоустойчивого кластера Windows содержит имя локального узла отказоустойчивого кластера. Если это поле не заполнено, значит в настоящее время этот экземпляр сервера не поддерживает группы доступности AlwaysOn. Либо локальный компьютер не является узлом кластера, кластер WSFC завершил работу, либо этот выпуск [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживает группы доступности AlwaysOn.  
  
9. Установите флажок «Включить группы доступности AlwaysOn» и нажмите кнопку «ОК».  
  
10. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сохранит внесенные изменения. После этого необходимо вручную перезапустить службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Это позволит выбрать время перезапуска, которое лучше всего подходит под требования вашего предприятия. После перезапуска службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция AlwaysOn будет включена, а свойство IsHadrEnabled будет установлено в значение 1.  
  
> [!NOTE]
>  -   Чтобы подключиться к этому компьютеру, необходимо иметь соответствующие разрешения пользователя или получить полномочия на целевом компьютере от соответствующего источника.  
> -   Имя управляемого компьютера отображается в скобках рядом с элементом «Управление компьютером» в дереве консоли.  
  
### <a name="using-powershell-cmdlets-to-enable-alwayson-availability-groups"></a>Использование командлетов PowerShell для активации групп доступности AlwaysOn  
 Командлет PowerShell, Enable-SqlAlwaysOn, используется для активации групп доступности AlwaysOn на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если группы доступности AlwaysOn включаются во время работы службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то для вступления изменения в силу необходимо перезапустить службу компонента ядра СУБД. Если не указан параметр -Force, командлет запрашивает, следует ли перезапустить службу. В случае отказа никаких действий не предпринимается.  
  
 Для выполнения этого командлета необходимо иметь разрешения администратора.  
  
 Для активации групп доступности AlwaysOn в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно использовать один из следующих вариантов синтаксиса.  
  
```  
Enable-SqlAlwaysOn [-Path <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn -InputObject <Server> [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn [-ServerInstance <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
 Следующая команда PowerShell активирует группы доступности AlwaysOn на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (компьютер или экземпляр).  
  
```  
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Machine\Instance  
```  
  
## <a name="configuring-remote-access-of-sql-server-running-on-server-core"></a>Настройка удаленного доступа к SQL Server на Server Core  
 Чтобы настроить удаленный доступ к экземпляру [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , который запускается в [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core с пакетом обновления 1 (SP1), выполните действия, описанные ниже.  
  
### <a name="enable-remote-connections-on-an-instance-of-sql-server"></a>Включение удаленных подключений на экземпляре SQL Server 
 Чтобы разрешить удаленные соединения, выполните следующие инструкции для экземпляра Server Core в локальной программе SQLCMD.exe.  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-sql-server-browser-service"></a>Включить и запустить службу обозревателя SQL Server  
 По умолчанию эта служба отключена.  Если она отключена на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , работающем на Server Core, то для ее включения выполните следующую команду из командной строки:  
  
 `sc config SQLBROWSER start= auto`  
  
 После включения службы выполните следующую команду из командной строки, чтобы запустить службу:  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a>Создание исключений в брандмауэре Windows  
 Чтобы создать исключения в брандмауэре Windows для доступа к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выполните действия, описанные в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
### <a name="enable-tcpip-on-an-instance-of-sql-server"></a>Включите поддержку TCP/IP в экземпляре SQL Server
 Протокол TCP/IP для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Server Core можно включить через Windows PowerShell. Выполните следующие действия.  
  
1.  На компьютере, где запущена ОС Windows Server 2008 R2 Server Core с пакетом обновления 1 (SP1), запустите диспетчер задач.  
  
2.  На вкладке **Приложения** нажмите **Создать задачу**.  
  
3.  В диалоговом окне **Создание новой задачи** введите **sqlps.exe** в поле **Открыть** и нажмите кнопку **ОК**. Это приведет к открытию окна **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell**.  
  
4.  В окне **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** выполните следующий скрипт, чтобы включить протокол TCP/IP:  
  
```  
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = new-object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
##  <a name="sql-server-profiler"></a>Приложение SQL Server Profiler  
 На удаленном компьютере запустите приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] и выберите в меню «Файл» пункт «Создать трассировку», приложение откроет диалоговое окно «Соединение с сервером», где можно указать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , размещенный на компьютере Server Core, к которому необходимо подключиться. Дополнительные сведения см. в разделе [Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md).  
  
 Сведения о разрешениях, необходимых для выполнения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], см. в разделе [Разрешения, необходимые для запуска приложения SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).  
  
 Дополнительные сведения о приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]см. в разделе [Приложение SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md).  
  
##  <a name="sql-server-auditing"></a>Подсистема аудита SQL Server  
 Для определения аудита можно дистанционно использовать среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)] . После создания и включения аудита он начнет вести записи в целевое назначение. Дополнительные сведения о создании аудитов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и управлении ими см. в разделе [Подсистема аудита SQL Server (компонент Database Engine)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
##  <a name="sql-servevr-command-prompt-utilities"></a>Программы командной строки Servevr команды SQL  
 Можно использовать следующие средства командной строки, которые позволяют объединить в скрипт операции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютере Server Core. В следующей таблице содержится список программ командной строки, поставляемых вместе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для Server Core.  
  
|**Служебная программа**|**Описание**|**Установлена в**|  
|-----------------|---------------------|----------------------|  
|[Программа bcp](../../tools/bcp-utility.md)|Используется для копирования данных между экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и файлом данных в указанном пользователем формате.|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа dtexec](../../integration-services/packages/dtexec-utility.md)|Используется для настройки и выполнения пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Программа dtutil](../../integration-services/dtutil-utility.md)|Используется для управления пакетами служб SSIS.|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Программа osql](../../tools/osql-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqlagent90](../../tools/sqlagent90-application.md)|Используется для запуска агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из командной строки.|\<диск>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*имя_экземпляра*>\MSSQL\Binn|  
|[Служебная программа sqlcmd](../../tools/sqlcmd-utility.md)|Позволяет вводить инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , системные процедуры и файлы скрипта в командной строке.|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа SQLdiag](../../tools/sqldiag-utility.md)|Используется для сбора диагностических сведений для службы поддержки пользователей [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Программа sqlmaint](../../tools/sqlmaint-utility.md)|Служит для выполнения планов обслуживания баз данных, созданных в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn|  
|[Программа sqlps](../../tools/sqlps-utility.md)|Используется для выполнения команд и скриптов PowerShell. Загружает и регистрирует командлеты и поставщика PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Приложение sqlservr](../../tools/sqlservr-application.md)|Служит для запуска и остановки экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] из командной строки при устранении неполадок.|\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn|  
  
##  <a name="use-troubleshooting-tools"></a>Использование средств устранения неполадок  
 Для определения аудита можно дистанционно использовать среду [SQLdiag Utility](../../tools/sqldiag-utility.md) позволяет выполнять сбор файлов журналов и данных с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и других типов серверов, а также мониторинг серверов и устранение определенных неполадок на серверах. SQLdiag предназначена для исследования и упрощения сбора диагностической информации для Microsoft Customer Support Services.  
  
 Вы можете запустить программу в командной строке администратора в Server Core, используя синтаксис, описанный в разделе: [Программа SQLdiag](../../tools/sqldiag-utility.md).  
  
## <a name="see-also"></a>См. также  
 [Установка SQL Server 2014 на Server Core](install-sql-server-on-server-core.md)   
 [Инструкции по установке](../../sql-server/install/installation-how-to-topics.md)  
  
  
