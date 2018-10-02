---
title: Отключение или приостановка обработки отчетов и подписок | Документы Майкрософт
ms.date: 09/29/2015
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- subscriptions [Reporting Services], pausing
- report processing [Reporting Services], pausing
- shared data sources [Reporting Services]
- pausing subscription processing
- pausing report processing
- temporarily stopping report processing
- disabling shared data sources
- roles [Reporting Services], modifying
- shared schedules [Reporting Services], pausing
ms.assetid: 3cf9a240-24cc-46d4-bec6-976f82d8f830
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 419e1a3e6bf886625edd260f48afea9bcb4bc109
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47614852"
---
# <a name="disable-or-pause-report-and-subscription-processing"></a>Отключение или приостановка обработки отчетов и подписок
  Существует несколько подходов, которые позволяют отключить или приостановить обработку отчетов и подписок [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . В этой статье описаны различные подходы — от отключения подписки до прерывания подключения к источнику данных. Не все эти подходы можно применять при обоих режимах работы сервера [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . В таблице ниже приведена сводка методов и поддерживаемых режимов сервера [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
##  <a name="bkmk_top"></a> В этом разделе  
  
||Поддерживаемый режим сервера|  
|-|---------------------------|  
|[Включение и отключение подписок](#bkmk_disable_subscription)|Основной режим|  
|[Приостановка общего расписания](#bkmk_pause_schedule)|Основной режим и режим SharePoint|  
|[Отключение общего источника данных](#bkmk_disable_shared_datasource)|Основной режим и режим SharePoint|  
|[Изменение назначений ролей для предотвращения доступа к отчету (основной режим)](#bkmk_modify_role_assignment)|Основной режим|  
|[Удаление разрешений на управление подписками из роли (основной режим)](#bkmk_remove_manage_subscriptions_permission)|Основной режим|  
|[Отключение модулей доставки](#bkmk_disable_extensions)|Основной режим и режим SharePoint|  
  
##  <a name="bkmk_disable_subscription"></a> Включение и отключение подписок  
  
> [!TIP]  
>  Новые возможности [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. **Включение и отключение подписок**. Новые параметры пользовательского интерфейса позволяют быстро отключать и включать подписки. Отключенные подписки сохраняют другие свойства конфигурации, такие как расписание, и их можно легко включить. Кроме того, можно программным путем включать и отключать подписки, а также проверять, какие именно подписки отключены.  
  
 ![лента подписки на службы Reporting Services](../../reporting-services/subscriptions/media/ssrs-subscription-ribbon.png "лента подписки на службы Reporting Services")  
  
 В диспетчере отчетов основного режима перейдите к подписке либо со страницы **Мои подписки** , либо со страницы **Управление** отдельной подписки. Выберите одну или несколько подписок, а затем нажмите на ленте кнопку отключения ![отключение подписки на службы Reporting Services](../../reporting-services/subscriptions/media/ssrs-disable-subscription.png "отключение подписки на службы Reporting Services") или включения ![включение подписки на службы Reporting Services](../../reporting-services/subscriptions/media/ssrs-enable-subscription.png "включение подписки на службы Reporting Services"). Отключенные подписки помечаются значком предупреждения ![предупреждение о состоянии подписки на службы Reporting Services](../../reporting-services/subscriptions/media/ssrs-subscription-warning.png "предупреждение о состоянии подписки на службы Reporting Services"), и для них указывается состояние **Отключено**.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] записывают строку в журнал [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] при отключении подписки и еще одну строку — при ее включении. Например, в файле журнала сервера отчетов:  
  
 `C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles\ReportServerService__10_16_2014_00_02_18.log`  
  
 можно увидеть строки, аналогичные приведенным ниже.  
  
 `library!ReportServer_0-1!b08!10/16/2014-16:21:14:: i INFO: Call to DisableSubscriptionAction(SubscriptionID=e843bc2b-023e-45a3-ba23-22f9dc9a0934)`  
  
 `library!ReportServer_0-1!2eec!10/16/2014-16:44:18:: i INFO: Call to EnableSubscriptionAction(SubscriptionID=e843bc2b-023e-45a3-ba23-22f9dc9a0934).`  
  
 ![Содержимое, связанное с PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") **Отключение отдельной подписки с помощью Windows PowerShell**. Для отключения определенной подписки используйте приведенный ниже скрипт PowerShell. Обновите имя сервера и идентификатор подписки.  
  
```  
#disable specific subscription  
$rs2010 = New-WebServiceProxy -Uri "http://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptionID = "subscription guid”;  
$rs2010.DisableSubscription($subscriptionID);  
  
```  
  
 С помощью следующего сценария можно вывести список всех подписок с их идентификаторами. Обновите имя сервера.  
  
```  
#list all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "http://SERVERNAME /ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/");  
$subscriptions | select subscriptionid, report, status, path  
  
```  
  
 ![Содержимое, связанное с PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") **Создание списка всех отключенных подписок с помощью Windows PowerShell**. Для получения списка всех отключенных подписок на текущем сервере отчетов в собственном режиме используйте приведенный ниже скрипт PowerShell. Обновите имя сервера.  
  
```  
#list all disabled subscriptions  
$rs2010 = New-WebServiceProxy -Uri "http://uetestb03/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/");  
Write-Host "--- Disabled Subscriptions ---";  
Write-Host "----------------------------------- ";  
$subscriptions | Where-Object {$_.Active.DisabledByUserSpecified -and $_.Active.DisabledByUser } | select subscriptionid, report, status, lastexecuted,path | format-table -auto  
```  
  
 ![Содержимое, связанное с PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") **Включение всех отключенных подписок с помощью Windows PowerShell**. Для включения всех подписок, которые в настоящее время отключены, используйте приведенный ниже скрипт PowerShell. Обновите имя сервера.  
  
```  
#enable all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "http://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/") | Where-Object {$_.status -eq "disabled" } ;  
ForEach ($subscription in $subscriptions)  
{  
    $rs2010.EnableSubscription($subscription.SubscriptionID);  
    $subscription | select subscriptionid, report, path  
}  
  
```  
  
 ![Содержимое, связанное с PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") **ОТКЛЮЧЕНИЕ всех подписок с помощью Windows PowerShell**. Для отключения **ВСЕХ** подписок используйте приведенный ниже скрипт PowerShell.  
  
```  
#DISABLE all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "http://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/") ;  
ForEach ($subscription in $subscriptions)  
{  
    $rs2010.DisableSubscription($subscription.SubscriptionID);  
    $subscription | select subscriptionid, report, path  
}  
```  
  
##  <a name="bkmk_pause_schedule"></a> Приостановка общего расписания  
 Если отчет или подписка выполняется по общему расписанию, можно приостановить расписание для предотвращения процесса обработки. Обработка всех отчетов и подписок, управляемая данным расписанием, откладывается до возобновления выполнения расписания.  
  
-   **Режим интеграции с SharePoint**. ![Параметры SharePoint](../../analysis-services/media/as-sharepoint2013-settings-gear.gif "Параметры SharePoint") В разделе **Параметры сайта** выберите **Управление общими расписаниями**. Выберите расписание, а затем щелкните **Приостановка выбранных расписаний**.  
  
-   **Основной режим.** В диспетчере отчетов щелкните **Параметры сайта**. Выберите расписание и щелкните **Приостановить**.  
  
##  <a name="bkmk_disable_shared_datasource"></a> Отключение общего источника данных  
 Одним из преимуществ использования общих источников данных является возможность отключения их, что позволяет избежать формирования отчета или запуска управляемой данными подписки. При отключении общих источников данных происходит разрыв соединения между отчетом и его внешним источником. После отключения источник данных становится недоступным для всех отчетов и подписок, которые его использовали.  
  
 Обратите внимание на то, что отчет продолжает загружаться, даже если источник данных недоступен. В отчете не содержится данных, но пользователи, обладающие соответствующими разрешениями, имеют доступ к страницам свойств отчета, настройкам безопасности, журналу отчета и информации о подписке, связанной с данным отчетом.  
  
-   **Режим SharePoint.** Чтобы отключить общий источник данных на сервере отчетов в режиме SharePoint, перейдите в библиотеку документов, которая содержит этот источник данных. ![Значок общего источника данных](../../reporting-services/report-data/media/hlp-16datasource.png "Значок общего источника данных") Щелкните источник данных, а затем снимите флажок **Включить этот источник данных**.  
  
-   **Основной режим.** Чтобы отключить общий источник данных на сервере отчетов в основном режиме, откройте этот источник данных в диспетчере отчетов и снимите флажок **Включить этот источник данных** .  
  
##  <a name="bkmk_modify_role_assignment"></a> Изменение назначений ролей для предотвращения доступа к отчету (основной режим)  
 Один из способов сделать отчет недоступным — временно удалить назначение роли, которое предоставляет доступ к отчету. Этот подход можно использовать для всех отчетов независимо от того, было ли создано соединение с источником данных. Этот подход затрагивает только конкретный отчет, не влияя на работу остальных отчетов или других элементов.  
  
 Для удаления назначения ролей откройте страницу «Свойства безопасности» для отчета в диспетчере отчетов. Если отчет наследует свойства безопасности от родительского объекта, то можно выбрать пункт **Изменить параметры безопасности элемента** , чтобы создать ограничивающую политику безопасности, исключающую назначения роли, которые обеспечивают доступ большому количеству пользователей (например, можно удалить назначения роли, которые предоставляют доступ всем пользователям, и оставить назначения роли, которые предоставляют доступ небольшой группе пользователей, например администраторам).  
  
##  <a name="bkmk_remove_manage_subscriptions_permission"></a> Удаление разрешений на управление подписками из роли (основной режим)  
 Чтобы запретить пользователям создавать подписки, удалите задачу **Управление отдельными подписками** из роли. После этого страницы «Подписка» станут недоступны. В диспетчере отчетов папка «Мои подписки» отображается пустой (ее удалить нельзя), даже если она до этого содержала подписки. Удаление связанных с подписками задач запрещает пользователям создавать и изменять подписки, но не удаляет существующие подписки, Существующие подписки продолжают действовать до тех пор, пока они не будут удалены. Чтобы удалить разрешение:  
  
1.  Откройте [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
2.  Подключитесь к серверу отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
3.  Разверните узел **Безопасность** .  
  
4.  Выберите роль и удалите задачу **Управление отдельными подписками** .  
  
##  <a name="bkmk_disable_extensions"></a> Отключение модулей доставки  
 Все модули доставки, установленные на сервере отчетов, доступны любому пользователю, который имеет разрешение на создание подписки на данный отчет. Следующие модули доставки доступны и настраиваются автоматически:  
  
-   Общая папка Windows  
  
-   Библиотека SharePoint (доступна только с сайта SharePoint, который интегрирован с сервером отчетов, работающим в режиме интеграции с SharePoint).  
  
 Доставку по электронной почте перед использованием необходимо настроить. Если настройка не выполнена, эта функция недоступна. См. дополнительные сведения о [настройке сервера отчетов для доставки электронной почты (SSRS Configuration Manager)](http://msdn.microsoft.com/b838f970-d11a-4239-b164-8d11f4581d83).  
  
 Если требуется отключить конкретные модули, можно удалить записи, относящиеся к этим модулям, из файла **RSReportServer.config** . Дополнительные сведения см. в руководствах по [файлам конфигурации Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md) и [настройке сервера отчетов для доставки электронной почты (SSRS Configuration Manager)](http://msdn.microsoft.com/b838f970-d11a-4239-b164-8d11f4581d83).  
  
 После удаления модуля доставки он становится недоступным в диспетчере отчетов или на сайте SharePoint. При удалении модуля доставок могут появляться неактивные подписки. Обязательно удаляйте подписки или настраивайте их на использование другого модуля доставки, прежде чем удалить какой-либо модуль.  
  
## <a name="see-also"></a>См. также:  
 [Подписки и доставка (службы Reporting Services)](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Файлы конфигурации служб Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Настройка диспетчера отчетов (собственный режим)](../../reporting-services/report-server/configure-report-manager-native-mode.md)   
 [Сервер отчетов служб Reporting Services (основной режим)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Диспетчер отчетов (службы Reporting Services в основном режиме)](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [Страница "Свойства безопасности", элементы (диспетчер отчетов)](http://msdn.microsoft.com/library/351b8503-354f-4b1b-a7ac-f1245d978da0)  
  
  
