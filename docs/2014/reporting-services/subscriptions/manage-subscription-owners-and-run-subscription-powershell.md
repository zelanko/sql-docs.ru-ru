---
title: Использование PowerShell для изменения и перечисления Reporting Services владельцев подписок и запуска подписки | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0fa6cb36-68fc-4fb8-b1dc-ae4f12bf6ff0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ebb20180e96302ba2ee90e9ab90cb79be19b7e1b
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72796376"
---
# <a name="use-powershell-to-change-and-list-reporting-services-subscription-owners-and-run-a-subscription"></a>Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription
  Приступая к работе с [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] , вы можете программно передать владение подпиской [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] от одного пользователя другому. В этом разделе содержится несколько скриптов Windows PowerShell, которые можно использовать для смены владельца подписки или простого перечисления владельцев. В каждом примере содержится образец синтаксиса для собственного режима и режима SharePoint. После смены владельца подписки подписка будет выполняться в контексте безопасности нового владельца, а в отчете в поле «User!UserID» будет отображаться значение нового владельца. Дополнительные сведения об объектной модели вызовов образцов см. в разделе <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>  
  
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell")  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]Основной режим &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Режим интеграции|  
  
 **В этом разделе:**  
  
-   [Использование скриптов](#bkmk_how_to)  
  
-   [Скрипт: вывод списка владельцев всех подписок](#bkmk_list_ownership_all)  
  
-   [Скрипт: вывод списка подписок, принадлежащих конкретному пользователю](#bkmk_list_all_one_user)  
  
-   [Скрипт: смена владельца всех подписок, принадлежащих конкретному пользователю](#bkmk_change_all)  
  
-   [Скрипт: вывод списка всех подписок, связанных с конкретным отчетом](#bkmk_list_for_1_report)  
  
-   [Скрипт: смена владельца конкретной подписки](#bkmk_change_all_1_subscription)  
  
-   [Скрипт: запуск (вызов) одной подписки](#bkmk_run_1_subscription)  
  
##  <a name="bkmk_how_to"></a> Использование скриптов  
  
### <a name="permissions"></a>Permissions  
 В этом разделе приводится сводка по уровням разрешений, необходимым для использования каждого метода в собственном режиме и режиме SharePoint [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. В скриптах, рассматриваемых в этом разделе, используются следующие методы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .  
  
-   [Метод ReportingService2010.ListSubscriptions](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listsubscriptions.aspx)  
  
-   [Метод ReportingService2010.ChangeSubscriptionOwner](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.changesubscriptionowner.aspx)  
  
-   [ReportingService2010.ListChildren](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listchildren.aspx)  
  
-   Метод [ReportingService2010.FireEvent](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.fireevent.aspx) используется только в последнем скрипте для запуска конкретной подписки. Если использовать этот скрипт не планируется, можно проигнорировать требования к методу FireEvent.  
  
 **Собственный режим.**  
  
-   Список подписок: (HYPERLINK "https://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx" ReadSubscription в отчете, а пользователь является владельцем подписки) или ReadAnySubscription  
  
-   Изменение подписок: пользователь должен состоять в группе BUILTIN\Administrators  
  
-   Список дочерних элементов: ReadProperties для элемента  
  
-   Вызов события: GenerateEvents (System)  
  
 **Режим интеграции с SharePoint:**  
  
-   Список подписок: ManageAlerts или (HYPERLINK "https://technet.microsoft.com/library/microsoft.sharepoint.spbasepermissions.aspx" CreateAlerts в отчете, и пользователь является владельцем подписки, а подписка является подпиской по времени).  
  
-   Изменение подписок: ManageWeb  
  
-   Список дочерних элементов: ViewListItems  
  
-   Вызов события: ManageWeb  
  
 Дополнительные сведения см. в разделе [Сравнение ролей и задач служб Reporting Services с группами и разрешениями SharePoint](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).  
  
### <a name="script-usage"></a>Использование скрипта  
 **Создание файлов скрипта (PS1)**  
  
1.  Создайте папку с именем **c:\scripts**. Если выбирается другая папка, измените имя папки, используемое в конструкциях синтаксиса командной строки в примере.  
  
2.  Для каждого скрипта создайте текстовый файл и сохраните файлы в папку c:\scripts. При создании файлов PS1 используйте имена из каждого синтаксиса командной строки в примере.  
  
3.  Откройте командную строку с разрешениями администратора.  
  
4.  С помощью приведенного в каждом примере синтаксиса командной строки выполните каждый скрипт.  
  
 **Тестовые среды**  
  
 Скрипты, приведенные в данном разделе, были протестированы в PowerShell версии 3 и со следующими версиями [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]:  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]  
  
##  <a name="bkmk_list_ownership_all"></a> Скрипт: вывод списка владельцев всех подписок  
 Этот скрипт выводит список всех подписок на одной сайте. С помощью этого скрипта можно проверить подключение или проверить путь к отчету и ИД подписки для использования в других скриптах. Этот скрипт упрощает аудит существующих подписок и их владельцев.  
  
### <a name="native-mode-syntax"></a>Синтаксис в собственном режиме
  
```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/reportserver" "/"  
```  
  
### <a name="sharepoint-mode-syntax"></a>Синтаксис режима интеграции с SharePoint
  
```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/_vti_bin/reportserver" "http://[server]"  
```  
  
### <a name="script"></a>Скрипт
  
```powershell
# Parameters  
#    server   - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
  
Param(  
    [string]$server,  
    [string]$site  
   )  
  
$rs2010 += New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$subscriptions += $rs2010.ListSubscriptions($site); # use "/" for default native mode site  
  
Write-Host " "  
Write-Host "----- $server's Subscriptions: "  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted, Status  
```  
  
> [!TIP]  
>  Чтобы проверить URL-адреса сайтов в режиме SharePoint, воспользуйтесь командлетом SharePoint **Get-SPSite**. Дополнительные сведения см. в статье [Get-SPSite](https://technet.microsoft.com/library/ff607950\(v=office.15\).aspx).  
  
##  <a name="bkmk_list_all_one_user"></a> Скрипт: вывод списка подписок, принадлежащих конкретному пользователю  
 Этот скрипт перечисляет все подписки, принадлежащие конкретному пользователю. С помощью этого скрипта можно проверить подключение или проверить путь к отчету и ИД подписки для использования в других скриптах. Этот скрипт полезен в случае, если какой-либо сотрудник увольняется из организации и необходимо проверить принадлежащие ему подписки, чтобы в дальнейшем сменить владельца или удалить подписку.  
  
### <a name="native-mode-syntax"></a>Синтаксис в собственном режиме
  
```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]" "[server]/reportserver" "/"  
```  
  
### <a name="sharepoint-mode-syntax"></a>Синтаксис режима интеграции с SharePoint
  
```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]"  "[server]/_vti_bin/reportserver" "http://[server]"  
```  
  
### <a name="script"></a>Скрипт  
  
```powershell
# Parameters:  
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change  
#    server        - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    site        - use "/" for default native mode site  
Param(  
    [string]$currentOwner,  
    [string]$server,  
    [string]$site  
)  
  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$subscriptions += $rs2010.ListSubscriptions($site);  
  
Write-Host " "  
Write-Host " "  
Write-Host "----- $currentOwner's Subscriptions: "  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.owner -eq $currentOwner}  
```  
  
##  <a name="bkmk_change_all"></a> Скрипт: смена владельца всех подписок, принадлежащих конкретному пользователю  
 Этот скрипт меняет владельца подписок, принадлежащих конкретному пользователю параметр нового владельца.  
  
### <a name="native-mode-syntax"></a>Синтаксис в собственном режиме
  
```cmd
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\current owner]" "[Domain]\[new owner]" "[server]/reportserver"  
```  
  
### <a name="sharepoint-mode-syntax"></a>Синтаксис режима интеграции с SharePoint
  
```cmd
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\{current owner]" "[Domain]\[new owner]" "[server]/_vti_bin/reportserver"  
```  
  
### <a name="script"></a>Скрипт
  
```powershell
# Parameters:  
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change  
#    newOwner      - DOMAIN\USER that will own the subscriptions you wish to change  
#    server        - server and instance name (e.g. myserver/reportserver, myserver/reportserver_db2, myserver/_vti_bin/reportserver)  
  
Param(  
    [string]$currentOwner,  
    [string]$newOwner,  
    [string]$server  
)  
  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$items = $rs2010.ListChildren("/", $true);  
  
$subscriptions = @();  
  
ForEach ($item in $items)  
{  
    if ($item.TypeName -eq "Report")  
    {  
        $curRepSubs = $rs2010.ListSubscriptions($item.Path);  
        ForEach ($curRepSub in $curRepSubs)  
        {  
            if ($curRepSub.Owner -eq $currentOwner)  
            {  
                $subscriptions += $curRepSub;  
            }  
        }  
    }  
}  
  
Write-Host " "  
Write-Host " "  
Write-Host -foregroundcolor "green" "-----  $currentOwner's Subscriptions changing ownership to $newOwner : "  
$subscriptions | select SubscriptionID, Owner, Path, Description,  Status  | format-table -AutoSize  
  
ForEach ($sub in $subscriptions)  
{  
    $rs2010.ChangeSubscriptionOwner($sub.SubscriptionID, $newOwner);  
}  
  
$subs2 = @();  
  
ForEach ($item in $items)  
{  
    if ($item.TypeName -eq "Report")  
    {  
        $subs2 += $rs2010.ListSubscriptions($item.Path);  
    }  
}  
```  
  
##  <a name="bkmk_list_for_1_report"></a> Скрипт: вывод списка всех подписок, связанных с конкретным отчетом  
 Этот скрипт перечисляет все подписки, связанные с конкретным отчетом. В синтаксисе пути к отчету требуется использовать полный URL-адрес. В примерах синтаксиса в имени отчета указывается только название, содержащее пробел. Поэтому имя отчета следует заключить в одинарные кавычки.  
  
### <a name="native-mode-syntax"></a>Синтаксис в собственном режиме
  
```cmd
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/reportserver" "'/reports/title only'" "/"  
```  
  
### <a name="sharepoint-mode-syntax"></a>Синтаксис режима интеграции с SharePoint
  
```cmd
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/_vti_bin/reportserver"  "'http://[server]/shared documents/title only.rdl'" "http://[server]"  
```  
  
### <a name="script"></a>Скрипт
  
```powershell
# Parameters:  
#    server      - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    reportpath  - path to report in the report server, including report name e.g. /reports/test report >> pass in  "'/reports/title only'"  
#    site        - use "/" for default native mode site  
Param  
(  
      [string]$server,  
      [string]$reportpath,  
      [string]$site  
)  
  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$subscriptions += $rs2010.ListSubscriptions($site);  
  
Write-Host " "  
Write-Host " "  
Write-Host "----- $reportpath 's Subscriptions: "  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.path -eq $reportpath}  
```  
  
##  <a name="bkmk_change_all_1_subscription"></a> Скрипт: смена владельца конкретной подписки  
 Этот сценарий меняет владельца конкретной подписки. Подписка идентифицируется по SubscriptionID, указанному в скрипте. Чтобы определить правильный SubscriptionID, можно воспользоваться одним из скриптов вывода списка подписок.  
  
### <a name="native-mode-syntax"></a>Синтаксис в собственном режиме
  
```cmd
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/reportserver" "/" "ac5637a1-9982-4d89-9d69-a72a9c3b3150"  
```  
  
### <a name="sharepoint-mode-syntax"></a>Синтаксис режима интеграции с SharePoint
  
```cmd
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/_vti_bin/reportserver" "http://[server]" "9660674b-f020-453f-b1e3-d9ba37624519"  
```  
  
### <a name="script"></a>Скрипт
  
```powershell
# Parameters:  
#    newOwner       - DOMAIN\USER that will own the subscriptions you wish to change  
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    site        - use "/" for default native mode site  
#    subscriptionID - guid for the single subscription to change  
  
Param(  
    [string]$newOwner,  
    [string]$server,  
    [string]$site,  
    [string]$subscriptionid  
   )  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
  
$subscription += $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid};  
  
Write-Host " "  
Write-Host "----- $subscriptionid's Subscription properties: "  
$subscription | select Path, report, Description, SubscriptionID, Owner, Status  
  
$rs2010.ChangeSubscriptionOwner($subscription.SubscriptionID, $newOwner)  
  
#refresh the list  
$subscription = $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid}; # use "/" for default native mode site  
Write-Host "----- $subscriptionid's Subscription properties: "  
$subscription | select Path, report, Description, SubscriptionID, Owner, Status  
```  
  
##  <a name="bkmk_run_1_subscription"></a> Скрипт: запуск (вызов) одной подписки  
 Этот скрипт запускает определенную подписку с помощью метода FireEvent. Независимо от настроенного для подписки расписания скрипт запустит подписку немедленно. EventType сопоставляется с известным набором событий, которые определены в файле конфигурации сервера отчетов **rsreportserver.config** . Скрипт использует следующий тип событий для стандартных подписок:  
  
 `<Event>`  
  
 `<Type>TimedSubscription</Type>`  
  
 `</Event>`  
  
 Дополнительные сведения о файле конфигурации см. в разделе [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).  
  
 Скрипт содержит логику задержки "`Start-Sleep -s 6`", поэтому после запуска события есть небольшой период времени для ввода обновленного состояния в метод ListSubscription.  
  
### <a name="native-mode-syntax"></a>Синтаксис в собственном режиме
  
```cmd
powershell c:\scripts\FireSubscription.ps1 "[server]/reportserver" $null "70366e82-2d3c-4edd-a216-b97e51e26de9"  
```  
  
### <a name="sharepoint-mode-syntax"></a>Синтаксис режима интеграции с SharePoint
  
```cmd
powershell c:\scripts\FireSubscription.ps1 "[server]/_vti_bin/reportserver" "http://[server]" "c3425c72-580d-423e-805a-41cf9799fd25"  
```  
  
### <a name="script"></a>Скрипт
  
```powershell
# Parameters  
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    site           - use $null for a native mode server  
#    subscriptionid - subscription guid  
  
Param(  
  [string]$server,  
  [string]$site,  
  [string]$subscriptionid  
  )  
  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
#event type is case sensative to what is in the rsreportserver.config  
$rs2010.FireEvent("TimedSubscription",$subscriptionid,$site)  
  
Write-Host " "  
Write-Host "----- Subscription ($subscriptionid) status: "  
#get list of subscriptions and filter to the specific ID to see the Status and LastExecuted  
Start-Sleep -s 6 # slight delay in processing so ListSubscription returns the updated Status and LastExecuted  
$subscriptions = $rs2010.ListSubscriptions($site);   
$subscriptions | select Status, Path, report, Description, Owner, SubscriptionID, EventType, lastexecuted | where {$_.SubscriptionID -eq $subscriptionid}
```  
  
## <a name="see-also"></a>См. также статью  
 <xref:ReportService2010.ReportingService2010.ListSubscriptions%2A>   
 <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>   
 <xref:ReportService2010.ReportingService2010.ListChildren%2A>   
 <xref:ReportService2010.ReportingService2010.FireEvent%2A>  
