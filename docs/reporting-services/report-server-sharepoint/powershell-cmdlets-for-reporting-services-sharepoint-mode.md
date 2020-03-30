---
title: Командлеты PowerShell для режима интеграции служб Reporting Services с SharePoint | Документы Майкрософт
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
monikerRange: '>=sql-server-2016 <=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 3e415fee08a9723419c7d8a4258fc88670c5e262
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "68892406"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a>Командлеты PowerShell для режима интеграции служб Reporting Services с SharePoint

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

При установке служб SQL Server 2016 Reporting Services в режиме интеграции с SharePoint устанавливаются командлеты PowerShell для поддержки серверов отчетов в режиме интеграции с SharePoint. Командлеты охватывают три категории функциональных возможностей.  
  
-   Установка общей службы и прокси-сервера Reporting Services для SharePoint.  
  
-   Подготовка приложений служб Reporting Services и связанных с ними прокси-серверов и управление ими.  
  
-   Управление компонентами служб Reporting Services, например расширениями и ключами шифрования.  

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступна после выхода SQL Server 2016.

## <a name="cmdlet-summary"></a>Обзор командлетов

 Для выполнения командлетов необходимо открыть консоль управления SharePoint. Можно также использовать редактор графического пользовательского интерфейса, который включен в Microsoft Windows, **интегрированная среда скриптов Windows PowerShell (ISE)** . Дополнительные сведения см. в разделе [Запуск Windows PowerShell на Windows Server](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell). В следующих сводках по командлетам упоминания "баз данных" приложения службы относятся ко всем базам данных, созданным и используемым приложением службы Reporting Services. Это включает базы данных конфигурации, предупреждений и временные базы данных.  
  
 Если при вводе примеров PowerShell отображается сообщение об ошибке следующего вида:  
  
-   термин "Install-SPRSService" не опознан как  
    имя командлета, функции, файла скрипта или действующей программы. Проверьте правильность написания имени, а если включен путь, то проверьте правильность пути и повторите попытку.  
  
 Возникает одна из следующих проблем.  
  
-   Режим интеграции служб Reporting Services с SharePoint не установлен, поэтому не установлены командлеты Reporting Services.  
  
-   Команда PowerShell была выполнена в Windows PowerShell или Windows PowerShell ISE, а не в оболочке управления SharePoint. Используйте оболочку управления SharePoint или добавьте оснастку SharePoint к окну Windows PowerShell с помощью следующей команды:  
  
    ```  
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 Дополнительные сведения см. в разделе [Использование Windows PowerShell для управления SharePoint 2013](https://technet.microsoft.com/library/ee806878.aspx).  
  
### <a name="open-the-sharepoint-management-shell-and-run-cmdlets"></a>Открытие командной консоли SharePoint и выполнение командлетов
  
1.  Нажмите кнопку **Пуск** .  
  
2.  Щелкните группу **Продукты Microsoft SharePoint** .  
  
3.  Щелкните **Консоль управления SharePoint**.  
  
 Чтобы просмотреть справку командной строки для командлета, используйте команду Get-Help среды PowerShell в командной строке PowerShell. Пример:  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
##  <a name="shared-service-and-proxy-cmdlets"></a>Командлеты общей службы и прокси-серверов

 В приведенной ниже таблице содержатся командлеты PowerShell для общих служб Reporting Services, интегрированных с SharePoint.  
  
|Командлет|Description|  
|------------|-----------------|  
|Install-SPRSService|Устанавливает и регистрирует либо удаляет общие службы Reporting Services. Это можно сделать только на компьютере, где установлены службы SQL Server Reporting Services в режиме интеграции с SharePoint. При установке выполняются две операции.<br /><br /> — Службы Reporting Services устанавливаются в ферме.<br /><br /> — Экземпляр служб Reporting Services устанавливается на текущем компьютере.<br /><br /> При удалении выполняются две операции.<br /><br /> — Службы Reporting Services удаляются с текущего компьютера.<br /><br /> — Службы Reporting Services удаляются из фермы.<br /><br /> <br /><br /> Если в ферме имеются другие компьютеры, на которых установлены службы Reporting Services, или если в ферме все еще выполняются приложения служб Reporting Services, будет выведено предупреждающее сообщение.|  
|Install-SPRSServiceProxy|Устанавливает и регистрирует или удаляет прокси-сервер службы Reporting Services на ферме SharePoint.|  
|Get-SPRSProxyUrl|Возвращает URL-адреса для доступа к службе Reporting Services.|  
|Get-SPRSServiceApplicationServers|Возвращает все серверы в локальной ферме SharePoint, на которых имеется общая установка службы Reporting Services. Этот командлет полезен при обновлении служб Reporting Services для определения того, на каких серверах выполняется общая служба, в связи с чем требуется обновление.|  
  
## <a name="service-application-and-proxy-cmdlets"></a>Командлеты приложения службы и прокси-серверов

 В приведенной ниже таблице содержатся командлеты PowerShell для приложений служб Reporting Services и связанных с ними прокси-серверов.  
  
|командлет|Description|  
|------------|-----------------|  
|Get-SPRSServiceApplication|Возвращает один или несколько объектов приложений служб Reporting Services.|  
|New-SPRSServiceApplication|Создание нового приложения службы Reporting Services и связанных баз данных.<br /><br /> Параметр LogonType указывает, использует ли сервер отчетов учетную запись пула приложений служб SSRS или имя входа SQL Server для доступа к базе данных сервера отчетов. Допустимые значения:<br /><br /> 0 Проверка подлинности Windows<br /><br /> 1 SQL Server<br /><br /> 2 Учетная запись пула приложений (по умолчанию)|  
|Remove-SPRSServiceApplication|Удаляет указанное приложение службы Reporting Services. Также будут удалены связанные базы данных.|  
|Set-SPRSServiceApplication|Изменяет свойства существующего приложения службы Reporting Services.|  
|New-SPRSServiceApplicationProxy|Создание прокси-сервера приложения службы Reporting Services.|  
|Get-SPRSServiceApplicationProxy|Возвращает одно или несколько существующих приложений службы Reporting Services.|  
|Dismount-SPRSDatabase|Отключает базы данных для приложения служб Reporting Services.|  
|Remove-SPRSDatabase|Удаляет базы данных для приложения служб Reporting Services.|  
|Set-SPRSDatabase|Задает свойства баз данных, связанных с приложением служб Reporting Services.|  
|Mount-SPRSDatabase|Подключает базы данных для приложения служб Reporting Services.|  
|New-SPRSDatabase|Создает базы данных приложения службы для указанного приложения служб Reporting Services.|  
|Get-SPRSDatabaseCreationScript|Выводит на экран скрипт создания базы данных для приложения служб Reporting Services. Затем скрипт можно запустить в среде SQL Server Management Studio.|  
|Get-SPRSDatabase|Возвращает одну или несколько баз данных приложения службы Reporting Services. Используйте команду для получения идентификатора базы данных служебного приложения, чтобы вы могли использовать Set-SPRSDatabase comdlet для изменения параметров, например `querytimeout`. Смотрите примеры в разделе [Получение и задание свойств базы данных приложения служб Reporting Services](#get-and-set-properties-of-the-reporting-service-application-database).|  
|Get-SPRSDatabaseRightsScript|Выводит на экран скрипт определения прав базы данных для приложения служб Reporting Services. Запрашивает необходимые сведения о пользователе и базе данных, а затем возвращает код Transact-SQL, который можно выполнить для изменения разрешений. Затем этот скрипт можно запустить в среде SQL Server Management Studio.|  
|Get-SPRSDatabaseUpgradeScript|Выводит скрипт обновления базы данных на экран. Скрипт обновит базы данных приложения служб Reporting Services до версии текущей установки служб Reporting Services.|  
  
## <a name="reporting-services-custom-functionality-cmdlets"></a>Командлеты пользовательской функциональности служб Reporting Services
  
|Командлет|Description|  
|------------|-----------------|  
|Update-SPRSEncryptionKey|Обновляет ключ шифрования для указанного приложения службы Reporting Services и повторно шифрует его данные.|  
|Restore-SPRSEncryptionKey|Восстанавливает созданную ранее резервную копию ключа шифрования для приложения службы Reporting Services.|  
|Remove-SPRSEncryptedData|Удаляет зашифрованные данные для указанного приложения службы Reporting Services.|  
|Backup-SPRSEncryptionKey|Создает резервную копию ключа шифрования для указанного приложения службы Reporting Services.|  
|New-SPRSExtension|Регистрирует новый модуль для работы с приложением службы Reporting Services.|  
|Set-SPRSExtension|Задает свойства существующего модуля служб Reporting Services.|  
|Remove-SPRSExtension|Удаляет модуль из приложения службы Reporting Services.|  
|Get-SPRSExtension|Возвращает один или несколько модулей Reporting Services для приложения службы Reporting Services.<br /><br /> Допустимые значения:<br /><br /> <br /><br /> Доставка<br /><br /> DeliveryUI<br /><br /> Render<br /><br /> Данные<br /><br /> безопасность<br /><br /> Аутентификация<br /><br /> EventProcessing<br /><br /> ReportItems<br /><br /> Конструктор<br /><br /> ReportItemDesigner<br /><br /> ReportItemConverter<br /><br /> ReportDefinitionCustomization|  
|Get-SPRSSite|Возвращает сайты SharePoint с учетом того, включена ли на них функция «ReportingService». По умолчанию возвращаются сайты, на которых включена функция «ReportingService».|  
  
## <a name="basic-samples"></a>Простые примеры

 Возвращает список командлетов, содержащих в названии строку "SPRS". Это будет полный список командлетов для служб Reporting Services.  
  
```  
Get-command -noun *SPRS*  
```  
  
 Или (немного более подробно) перенаправлены в текстовый файл с именем commandlist.txt  
  
```  
Get-command -noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 Установка служб Reporting Services для SharePoint и прокси-сервера службы.  
  
```  
Install-SPRSService  
```  
  
```  
Install-SPRSServiceProxy  
```  
  
 Запуск служб Reporting Services  
  
```  
get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 Введите следующую команду в консоли управления SharePoint, чтобы получить из файла журнала отфильтрованный список строк. Команда отфильтрует строки, содержащие подстроку "ssrscustomactionerror". В этом примере рассматривается файл журнала, созданный при установке rssharepoint.msi.  
  
```  
Get-content -path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | select-string "ssrscustomactionerror"  
```  
  
## <a name="detailed-samples"></a>Подробные примеры

 В дополнение к следующим примерам обратитесь к разделу "Сценарий Windows PowerShell" в статье [Сценарий Windows PowerShell для шагов 1–4](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md#bkmk_full_script).  
  
### <a name="create-a-reporting-services-service-application-and-proxy"></a>Создание приложения службы Reporting Services и прокси-сервера

 Этот пример скрипта выполняет следующие задачи:  
  
1.  Создайте приложение службы Reporting Services и прокси-сервер. В скрипте предполагается, что пул приложений "My App Pool" уже существует.  
  
2.  Добавьте прокси-сервер в группу прокси-серверов по умолчанию  
  
3.  Предоставьте приложению службы доступ к порту 80 базы данных содержимого веб-приложения. В скрипте предполагается, что сайт `https://sitename` уже существует.  
  
```  
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool "My App Pool"  
$serviceApp = New-SPRSServiceApplication "My RS Service App" -ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy -Name "My RS Service App Proxy" -ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application's content database.  
$webApp = Get-SPWebApplication "https://sitename"  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)  
  
```  
  
### <a name="review-and-update-a-reporting-services-delivery-extension"></a>Проверка и обновление модуля доставки служб Reporting Services

 Следующий пример скрипта PowerShell показывает обновление конфигурации модуля доставки электронной почты сервера отчетов для приложения службы с именем `My RS Service App`. Измените значения для SMTP-сервера (`<email server name>`) и псевдонима FROM электронной почты (`<your FROM email address>`).  
  
```  
$app=get-sprsserviceapplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
$emailXml = [xml]$emailCfg   
$emailXml.SelectSingleNode("//SMTPServer").InnerText = "<email server name>"  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 В приведенном выше примере, если точное имя приложения службы не известно, можно было изменить первую инструкцию таким образом, чтобы имя приложения службы возвращалось на основе поиска фрагмента имени. Пример:  
  
```  
$app=get-sprsserviceapplication | where {$_.name -like " ssrs_testapp *"}  
```  
  
 Следующий сценарий вернет текущие значения настройки модулю доставки электронной почты сервера отчетов для служебного приложения под именем "Приложения служб Reporting Services". В ходе первого шага производится задание для переменной $app значения, равного объекту приложения службы с именем «Мое приложение служб RS».  
  
 Во второй инструкции запрашивается значение модуля доставки "электронная почта сервера отчетов" для объекта приложения службы в переменной $app и выбрано configurationXML (XML-файлы конфигурации).  
  
```  
$app=get-sprsserviceapplication -Name "Reporting Services Application"  
Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
 Вы также можете переписать указанные выше два выражения в одно:  
  
```  
get-sprsserviceapplication -Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
### <a name="get-and-set-properties-of-the-reporting-service-application-database"></a>Получение и задание свойств для базы данных приложения Reporting Services

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
Set-SPRSDatabase -identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 Чтобы убедиться в том, что значение установлено, снова запустите GET cmdlet.  
  
```  
Get-SPRSDatabase -identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
### <a name="list-reporting-services-data-extensions"></a>Список модулей обработки данных Reporting Services

 В примере ниже циклически опрашивается каждое приложение служб Reporting Services и выводится список текущих модулей обработки данных для каждого приложения.  
  
```  
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)   
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType "Data" | select name,extensiontype | Format-Table -AutoSize  
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
  
### <a name="change-and-list-reporting-services-subscription-owners"></a>Изменение и перечисление владельцев подписок Reporting Services

 См. раздел [Использование PowerShell для смены и перечисления владельцев подписок служб Reporting Services и запуска подписки](../../reporting-services/subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
## <a name="next-steps"></a>Дальнейшие действия

[Использование PowerShell для смены и перечисления владельцев подписок служб Reporting Services и запуска подписки](../../reporting-services/subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)  
[Контрольный список. Использование PowerShell для проверки Power Pivot для SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint)   
[Получение справки по SQL Server PowerShell](../../relational-databases/scripting/get-help-sql-server-powershell.md)   

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
