---
title: Командлеты PowerShell для режима SharePoint службы Reporting Services | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
caps.latest.revision: 30
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 3a9ced7cb304b5cec0e329adc43f6572b45ebf19
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189480"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a>PowerShell cmdlets для режима SharePoint службы Reporting Services
  При установке служб [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint инсталлируются командлеты PowerShell для поддержки серверов отчетов в режиме интеграции с SharePoint. Командлеты охватывают три категории функциональных возможностей.  
  
-   Установка [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] общей службы и прокси-сервера SharePoint.  
  
-   Подготовка и управление [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] службы приложений и связанные учетные записи-посредники.  
  
-   Управление функциями служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , например расширениями и ключами шифрования.  
  
||  
|-|  
|Службы [!INCLUDE[applies](../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint|  
  
 **В этом разделе обсуждается следующее.**  
  
-   [Обзор командлетов](#bkmk_cmdlet_sum)  
  
-   [Командлеты общей службы и прокси-серверов](#bkmk_sharedservice_cmdlets)  
  
-   [Командлеты приложения службы и прокси-серверов](#bkmk_serviceapp_cmdlets)  
  
-   [Командлеты пользовательской функциональности служб Reporting Services](#bkmk_ssrsfeatures_cmdlets)  
  
-   [Простые примеры](#bkmk_basic_samples)  
  
-   [Подробные примеры](#bkmk_detailedsamples)  
  
    -   [Создание приложения службы Reporting Services и прокси-сервера](#bkmk_example_create_service_application)  
  
    -   [Проверка и обновление модуля доставки служб Reporting Services](#bkmk_example_delivery_extension)  
  
    -   [Получение и задание свойств базы данных приложения службы Reporting Services, например время ожидания базы данных](#bkmk_example_db_properties)  
  
    -   [Список reporting services модули обработки данных — режим SharePoint](#bkmk_example_list_data_extensions)  
  
    -   [Изменение и вывод списка владельцев подписки](#bkmk_change_subscription_owner)  
  
##  <a name="bkmk_cmdlet_sum"></a> Обзор командлетов  
 Для выполнения командлетов необходимо открыть консоль управления SharePoint. Можно также использовать редактор графического пользовательского интерфейса, который включен в Microsoft Windows, **интегрированная среда скриптов Windows PowerShell (ISE)**. Дополнительные сведения см. в разделе [запуск Windows PowerShell в Windows Server](http://technet.microsoft.com/library/hh847814.aspx) (http://technet.microsoft.com/library/hh847814.aspx). В следующих сводках о командлетах ссылки на «базы данных» служебного приложения указывают на все базы данных, созданные и используемые приложением службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Это включает базы данных конфигурации, предупреждений и временные базы данных.  
  
 Если при вводе примеров PowerShell отображается сообщение об ошибке следующего вида:  
  
-   термин "Install-SPRSService" не опознан как  
    имя командлета, функции, файла скрипта или действующей программы. Проверьте правильность написания имени, а если включен путь, то проверьте правильность пути и повторите попытку.  
  
 Возникает одна из следующих проблем.  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Режим SharePoint не установлен и, следовательно, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не установлены командлеты.  
  
-   Команда PowerShell была выполнена в Windows PowerShell или Windows PowerShell ISE, а не в оболочке управления SharePoint. Используйте оболочку управления SharePoint или добавьте оснастку SharePoint к окну Windows PowerShell с помощью следующей команды:  
  
    ```  
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 Дополнительные сведения см. [с помощью Windows PowerShell для администрирования SharePoint 2013](http://technet.microsoft.com/library/ee806878.aspx) (http://technet.microsoft.com/library/ee806878.aspx).  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a>Открытие оболочки управления SharePoint и выполнение командлетов  
  
1.  Нажмите кнопку **Пуск** .  
  
2.  Щелкните группу **Продукты Microsoft SharePoint** .  
  
3.  Щелкните **Консоль управления SharePoint**.  
  
 Чтобы просмотреть справку командной строки для командлета, используйте команду Get-Help среды PowerShell в командной строке PowerShell. Например:  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="bkmk_sharedservice_cmdlets"></a> Командлеты общей службы и прокси-серверов  
 В следующей таблице содержатся командлеты PowerShell для общей службы SharePoint [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
|Командлет|Описание|  
|------------|-----------------|  
|Install-SPRSService|Устанавливает и регистрирует, либо удаляет общую службу [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Это можно сделать только на компьютере, где имеется установка служб SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. При установке выполняются две операции.<br /><br /> (1) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] установлена служба в ферме.<br /><br /> (2) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] на текущем компьютере установлен экземпляр службы.<br /><br /> При удалении выполняются две операции.<br />(1) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] службы удаляются с текущего компьютера.<br />(2) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] службы удаляются из фермы.<br /><br /> <br /><br /> Примечание: Если присутствуют другие компьютеры в ферме, имеющих [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] служба, или если все еще [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] служебных приложений, работающих в ферме, отображается предупреждающее сообщение.|  
|Install-SPRSServiceProxy|Устанавливает и регистрирует или удаляет прокси-сервер службы Reporting Services на ферме SharePoint.|  
|Get-SPRSProxyUrl|Возвращает URL-адреса для доступа к [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] службы.|  
|Get-SPRSServiceApplicationServers|Возвращает все серверы в локальной ферме SharePoint, на которых имеется установка общей службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Этот командлет полезен при обновлении служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , чтобы определить, на каких серверах выполняется общая служба, в связи с чем требуется обновление.|  
  
###  <a name="bkmk_serviceapp_cmdlets"></a> Командлеты приложения службы и прокси-серверов  
 В следующей таблице содержатся командлеты PowerShell для приложений служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и связанные с ними прокси-серверы.  
  
|Командлет|Описание|  
|------------|-----------------|  
|Get-SPRSServiceApplication|Возвращает один или больше объектов служебного приложения [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|New-SPRSServiceApplication|Создание нового приложения службы Reporting Services и связанных баз данных.<br /><br /> Параметр LogonType указывает, использует ли сервер отчетов учетную запись пула приложений служб SSRS или имя входа SQL Server для доступа к базе данных сервера отчетов. Может принимать одно из следующих значений:<br /><br /> 0 Проверка подлинности Windows<br /><br /> 1 SQL Server<br /><br /> 2 Учетная запись пула приложений (по умолчанию)|  
|Remove-SPRSServiceApplication|Удаляет указанное приложение службы Reporting Services. Также будут удалены связанные базы данных.|  
|Set-SPRSServiceApplication|Изменяет свойства существующего приложения службы Reporting Services.|  
|New-SPRSServiceApplicationProxy|Создание прокси-сервера приложения службы Reporting Services.|  
|Get-SPRSServiceApplicationProxy|Получает один или несколько [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] прокси-серверов приложения службы.|  
|Dismount-SPRSDatabase|Выполняет размонтирование баз данных приложения службы для приложения службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].|  
|Remove-SPRSDatabase|Удаление баз данных приложения службы для [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] приложения службы.|  
|Set-SPRSDatabase|Задает свойства баз данных, связанных с приложением службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].|  
|Mount-SPRSDatabase|Присоединяет базы данных для [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] приложения службы.|  
|New-SPRSDatabase|Создать новые базы данных приложения службы для указанного [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] приложения службы.|  
|Get-SPRSDatabaseCreationScript|Выводит на экран скрипт создания базы данных для приложения службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Затем скрипт можно запустить в среде SQL Server Management Studio.|  
|Get-SPRSDatabase|Получает одну или несколько баз данных приложения службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Используйте команду для получения идентификатора базы данных служебного приложения, чтобы вы могли использовать Set-SPRSDatabase comdlet для изменения параметров, например `querytimeout`. Смотрите примеры в данной теме, [Получение и задание свойств базы данных приложения Reporting Services, например времени ожидания базы данных](#bkmk_example_db_properties).|  
|Get-SPRSDatabaseRightsScript|Выводит на экран скрипт определения прав базы данных [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] приложения службы. Запрашивает необходимые сведения о пользователе и базе данных, а затем возвращает код Transact-SQL, который можно выполнить для изменения разрешений. Затем этот скрипт можно запустить в среде SQL Server Management Studio.|  
|Get-SPRSDatabaseUpgradeScript|Выводит скрипт обновления базы данных на экран. Скрипт произведет обновление баз данных приложения службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] до версии баз данных текущей установки служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
  
###  <a name="bkmk_ssrsfeatures_cmdlets"></a> Командлеты пользовательской функциональности служб Reporting Services  
  
|Командлет|Описание|  
|------------|-----------------|  
|Update-SPRSEncryptionKey|Обновляет ключ шифрования для указанного приложения службы Reporting Services и повторно шифрует его данные.|  
|Restore-SPRSEncryptionKey|Восстанавливает созданную ранее резервную копию ключа шифрования для приложения службы Reporting Services.|  
|Remove-SPRSEncryptedData|Удаляет зашифрованные данные для указанного приложения службы Reporting Services.|  
|Backup-SPRSEncryptionKey|Создает резервную копию ключа шифрования для указанного приложения службы Reporting Services.|  
|New-SPRSExtension|Регистрирует новый модуль для работы с приложением службы Reporting Services.|  
|Set-SPRSExtension|Задает свойства существующего модуля служб Reporting Services.|  
|Remove-SPRSExtension|Удаляет модуль из приложения службы Reporting Services.|  
|Get-SPRSExtension|Получает один или несколько [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] расширения для [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] приложения службы.<br /><br /> Допустимые значения:<br /><br /> **Доставка**<br /><br /> **Deliveryui**<br /><br /> **Render**<br /><br /> **Data**<br /><br /> **безопасность**<br /><br /> **Проверка подлинности**<br /><br /> **EventProcessing**<br /><br /> **ReportItems**<br /><br /> **Designer**<br /><br /> **ReportItemDesigner**<br /><br /> **ReportItemConverter**<br /><br /> **ReportDefinitionCustomization**|  
|Get-SPRSSite|Возвращает сайты SharePoint с учетом того, включена ли на них функция «ReportingService». По умолчанию возвращаются сайты, на которых включена функция «ReportingService».|  
  
##  <a name="bkmk_basic_samples"></a> Простые примеры  
 Возвращает список командлетов, содержащих в названии строку «SPRS». Это будет полный список [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] командлетов.  
  
```  
Get-command –noun *SPRS*  
```  
  
 Или (немного более подробно) перенаправлены в текстовый файл с именем commandlist.txt  
  
```  
Get-command -noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 Установка службы SharePoint [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и прокси-сервера службы.  
  
```  
Install-SPRSService  
```  
  
```  
Install-SPRSServiceProxy  
```  
  
 Запуск [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] службы  
  
```  
get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 Введите следующую команду в консоли управления SharePoint, чтобы получить из файла журнала отфильтрованный список строк. Команда отфильтрует строки, содержащие подстроку «ssrscustomactionerror». В этом примере рассматривается файл журнала, созданный при установке rssharepoint.msi.  
  
```  
Get-content -path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | select-string "ssrscustomactionerror"  
```  
  
##  <a name="bkmk_detailedsamples"></a> Подробные примеры  
 В дополнение к следующим примерам, обратитесь к разделу “Сценарий Windows PowerShell” в данной теме [Windows PowerShell script for Steps 1–4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).  
  
###  <a name="bkmk_example_create_service_application"></a> Создание приложения службы Reporting Services и прокси-сервера  
 Этот пример скрипта выполняет следующие задачи:  
  
1.  Создайте приложение службы Reporting Services и прокси-сервер. В скрипте предполагается, что пул приложений «My App Pool» уже существует.  
  
2.  Добавьте прокси-сервер в группу прокси-серверов по умолчанию  
  
3.  Предоставьте приложению службы доступ к порту 80 базы данных содержимого веб-приложения. В скрипте предполагается сайта "http://sitename" уже существует.  
  
```  
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool “My App Pool”  
$serviceApp = New-SPRSServiceApplication “My RS Service App” –ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy –Name “My RS Service App Proxy” –ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup –default | Add-SPServiceApplicationProxyGroupMember –Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application’s content database.  
$webApp = Get-SPWebApplication “http://sitename”  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)  
  
```  
  
###  <a name="bkmk_example_delivery_extension"></a> Проверка и обновление модуля доставки служб Reporting Services  
 Следующий пример скрипта PowerShell показывает обновление конфигурации модуля доставки электронной почты сервера отчетов для приложения службы с именем `My RS Service App`. Измените значения для SMTP-сервера (`<email server name>`) и псевдонима FROM электронной почты (`<your FROM email address>`).  
  
```  
$app=get-sprsserviceapplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
$emailXml = [xml]$emailCfg   
$emailXml.SelectSingleNode("//SMTPServer").InnerText = “<email server name>”  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 В приведенном выше примере, если точное имя приложения службы не известно, можно было изменить первую инструкцию таким образом, чтобы имя приложения службы возвращалось на основе поиска фрагмента имени. Например:  
  
```  
$app=get-sprsserviceapplication | where {$_.name -like " ssrs_testapp *"}  
```  
  
 Следующий сценарий вернет текущие значения настройки модулю доставки электронной почты сервера отчетов для служебного приложения под именем "Приложения служб Reporting Services". В ходе первого шага производится задание для переменной $app значения, равного объекту приложения службы с именем «Мое приложение служб RS».  
  
 Во второй инструкции запрашивается значение модуля доставки «электронная почта сервера отчетов» для объекта приложения службы в переменной $app и выбрано configurationXML (XML-файлы конфигурации).  
  
```  
$app=get-sprsserviceapplication –Name "Reporting Services Application"  
Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
 Вы также можете переписать указанные выше два выражения в одно:  
  
```  
get-sprsserviceapplication –Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="bkmk_example_db_properties"></a> Получение и задание свойств базы данных приложения службы Reporting Services, например время ожидания базы данных  
 Следующий пример сначала возвращает список баз данных и параметров, чтобы вы могли определить guid базы данных (идентификатор), который вы затем предоставите для настройки команды. Полный список параметров смотрите в `Get-SPRSDatabase | format-list`.  
  
```  
get-SPRSDatabase | select id, querytimeout,connectiontimeout, status, server, ServiceInstance   
```  
  
 Следующий пример является примеров вывода. Определите идентификатор для базы данных, которую вы хотите изменить и используйте идентификатор в SET cmdlet.  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```  
Set-SPRSDatabase –identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 Чтобы убедиться в том, что значение установлено, снова запустите GET cmdlet.  
  
```  
Get-SPRSDatabase –identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="bkmk_example_list_data_extensions"></a> Список reporting services модули обработки данных — режим SharePoint  
 В примере ниже циклически опрашивается каждое приложение службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , выводится список текущих данных модулей обработки для каждого приложения.  
  
```  
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)   
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType “Data” | select name,extensiontype | Format-Table -AutoSize  
}  
```  
  
 **Пример результата:**  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="bkmk_change_subscription_owner"></a> Изменение и вывод списка владельцев подписки  
 См. раздел [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
## <a name="see-also"></a>См. также  
 [Использование PowerShell для смены и перечисления владельцев подписок служб Reporting Services и запуска подписки](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)   
 [Контрольный список: Использование PowerShell для проверки PowerPivot для SharePoint](../analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md)   
 [Скрипты PowerShell для управления SharePoint CodePlex](http://sharepointpsscripts.codeplex.com/)   
 [Администрирование служб SSRS с помощью PowerShell](https://curatedviews.cloudapp.net/13107/how-to-administer-ssrs-using-powershell)  
  
  