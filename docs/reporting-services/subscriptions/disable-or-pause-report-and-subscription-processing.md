---
title: Отключение или приостановка обработки отчетов и подписок | Документы Майкрософт
ms.date: 06/19/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
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
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 228cb40e1c0f40d9525ca83129878d30b722b910
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893423"
---
# <a name="disable-or-pause-report-and-subscription-processing"></a>Отключение или приостановка обработки отчетов и подписок  
Существует несколько подходов, которые позволяют отключить или приостановить обработку отчетов и подписок [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . В этой статье описаны различные подходы — от отключения подписки до прерывания подключения к источнику данных. В обоих [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] режимах сервера возможны не все подходы. В следующих таблицах приведены сводные данные о методах и поддерживаемых [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] режимах сервера.  
  
##  <a name="bkmk_top"></a> В этой статье описано следующее:  
  
||Поддерживаемый режим сервера|  
|-|---------------------------|  
|[Включение и отключение подписок](#bkmk_disable_subscription)|Основной режим|  
|[Приостановка общего расписания](#bkmk_pause_schedule)|Основной режим и режим SharePoint|  
|[Отключение общего источника данных](#bkmk_disable_shared_datasource)|Основной режим и режим SharePoint|  
|[Изменение назначений ролей для предотвращения доступа к отчету (основной режим)](#bkmk_modify_role_assignment)|Основной режим|  
|[Удаление разрешений на управление подписками из роли (основной режим)](#bkmk_remove_manage_subscriptions_permission)|Основной режим|  
|[Отключение модулей доставки](#bkmk_disable_extensions)|Основной режим и режим SharePoint|  
  
##  <a name="bkmk_disable_subscription"></a>Включение и отключение подписок  
  
>[!TIP]  
>Новые возможности в SQL 2016 Reporting Services, *Включение и отключение подписок*. Новые параметры пользовательского интерфейса позволяют быстро включать и отключать подписки. В отключенных подписках сохраняются другие свойства конфигурации, например расписание. Такие подписки можно легко включить снова. Кроме того, можно программным путем включать и отключать подписки, а также проверять, какие именно подписки отключены.  
  
  ![Кнопки включения и отключения на странице "подписки" ](../../reporting-services/subscriptions/media/disable-or-pause-report-and-subscription-processing/subscription-enable-and-disable-buttons.png)  
  
На веб-портале перейдите к подписке на странице **«Мои подписки** » или на странице « **подписки** » отдельной подписки. Выберите одну или несколько подписок, а затем нажмите кнопку отключения или включения на ленте (см. предыдущую иллюстрацию). Столбец состояние изменится на "отключено" или "включено" соответственно.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Записывает строку в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] журнал, если подписка либо включена, либо отключена. Например, в файле журнала сервера отчетов:  
  
 `C:\Program Files\Microsoft SQL Server Reporting Services\SSRS\LogFiles\RSPortal_2019_06_20_00_49_22.log`  
  
 можно увидеть строки, аналогичные приведенным ниже.  
  
 `RSPortal!subscription!RSPortal.exe!93!06/20/2019-01:16:47:: i INFO: Subscription 2b409d66-d4ea-408a-918c-0f9e41ce49ca disabled at 06/20/2019 01:16:47`  
  
 `RSPortal!subscription!RSPortal.exe!93!06/20/2019-01:16:51:: i INFO: Subscription 2b409d66-d4ea-408a-918c-0f9e41ce49ca enabled at 06/20/2019 01:16:51`  
  
![Содержимое, связанное с PowerShell](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/rs-powershellicon.jpg " PowerShell related content") **Отключение отдельной подписки с помощью Windows PowerShell.** Для отключения определенной подписки используйте приведенный ниже скрипт PowerShell. Обновите имя сервера и идентификатор подписки в скрипте.  
  
```PS  
#disable specific subscription  
$rs2010 = New-WebServiceProxy -Uri "https://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptionID = "subscription guid";  
$rs2010.DisableSubscription($subscriptionID);  
  
```  
  
 С помощью следующего сценария можно вывести список всех подписок с их идентификаторами. Обновите имя сервера.  
  
```  
#list all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "https://SERVERNAME /ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/");  
$subscriptions | select subscriptionid, report, status, path  
  
```  
  
 ![Содержимое, связанное с PowerShell](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") **Создание списка всех отключенных подписок с помощью Windows PowerShell**. Для получения списка всех отключенных подписок на текущем сервере отчетов в собственном режиме используйте приведенный ниже скрипт PowerShell. Обновите имя сервера.  
  
```  
#list all disabled subscriptions  
$rs2010 = New-WebServiceProxy -Uri "https://uetestb03/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/");  
Write-Host "--- Disabled Subscriptions ---";  
Write-Host "----------------------------------- ";  
$subscriptions | Where-Object {$_.Active.DisabledByUserSpecified -and $_.Active.DisabledByUser } | select subscriptionid, report, status, lastexecuted,path | format-table -auto  
```  
  
 ![Содержимое, связанное с PowerShell](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") **Включение всех отключенных подписок с помощью Windows PowerShell**. Для включения всех подписок, которые в настоящее время отключены, используйте приведенный ниже скрипт PowerShell. Обновите имя сервера.  
  
```  
#enable all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "https://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/") | Where-Object {$_.status -eq "disabled" } ;  
ForEach ($subscription in $subscriptions)  
{  
    $rs2010.EnableSubscription($subscription.SubscriptionID);  
    $subscription | select subscriptionid, report, path  
}  
  
```  
  
 ![Содержимое, связанное с PowerShell](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") **ОТКЛЮЧЕНИЕ всех подписок с помощью Windows PowerShell**. Для отключения **ВСЕХ** подписок используйте приведенный ниже скрипт PowerShell.  
  
```  
#DISABLE all subscriptions  
$rs2010 = New-WebServiceProxy -Uri "https://SERVERNAME/ReportServer/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
$subscriptions = $rs2010.ListSubscriptions("/") ;  
ForEach ($subscription in $subscriptions)  
{  
    $rs2010.DisableSubscription($subscription.SubscriptionID);  
    $subscription | select subscriptionid, report, path  
}  
```  
  
##  <a name="bkmk_pause_schedule"></a> Приостановка общего расписания  
 Если отчет или подписка выполняется по общему расписанию, можно приостановить расписание для предотвращения процесса обработки. Обработка всех отчетов и подписок, управляемая данным расписанием, откладывается до возобновления выполнения расписания.  
  
-   **Режим интеграции с SharePoint**. ![Параметры SharePoint](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "Параметры SharePoint") В разделе **Параметры сайта** выберите **Управление общими расписаниями**. Выберите расписание, а затем щелкните **Приостановка выбранных расписаний**.  
  
-   **Основной режим:** На веб-портале нажмите кнопку **параметры** ![кнопка параметры](media/ssrs-portal-settings-gear.png) в строке меню в верхней части экрана веб-портала и выберите в раскрывающемся меню пункт **Параметры сайта** . Перейдите на вкладку **расписания** , чтобы отобразить страницу расписания. Установите флажки рядом с расписаниями, которые необходимо включить или отключить, а затем нажмите кнопку **включить** или **Отключить** соответственно, чтобы выполнить нужное действие. Столбец состояние изменится на "отключено" или "включено" соответственно.  
  
##  <a name="bkmk_disable_shared_datasource"></a> Отключение общего источника данных  
 Одним из преимуществ использования общих источников данных является возможность отключения их, что позволяет избежать формирования отчета или запуска управляемой данными подписки. При отключении общих источников данных происходит разрыв соединения между отчетом и его внешним источником. После отключения источник данных становится недоступным для всех отчетов и подписок, которые его использовали.  
  
 Обратите внимание на то, что отчет продолжает загружаться, даже если источник данных недоступен. В отчете не содержится данных, но пользователи, обладающие соответствующими разрешениями, имеют доступ к страницам свойств отчета, настройкам безопасности, журналу отчета и информации о подписке, связанной с данным отчетом.  
  
-   **Режим SharePoint.** Чтобы отключить общий источник данных на сервере отчетов в режиме SharePoint, перейдите в библиотеку документов, которая содержит этот источник данных. ![Значок общего источника данных](../../reporting-services/report-data/media/hlp-16datasource.png "Значок общего источника данных") Щелкните источник данных, а затем снимите флажок **Включить этот источник данных**.  
  
-   **Основной режим.** Чтобы отключить общий источник данных на сервере отчетов в основном режиме, откройте этот источник данных на веб-портале и снимите флажок **Включить этот источник данных**.  
  
##  <a name="bkmk_modify_role_assignment"></a> Изменение назначений ролей для предотвращения доступа к отчету (основной режим)  
Один из способов сделать отчет недоступным — временно удалить назначение роли, которое предоставляет доступ к отчету. Этот подход можно использовать для всех отчетов независимо от того, было ли создано соединение с источником данных. Этот подход затрагивает только конкретный отчет, не влияя на работу остальных отчетов или других элементов.  
  
 Чтобы удалить назначение ролей, откройте страницу **Безопасность** отчета на веб-портале. Если отчет наследует свойства безопасности от родительского объекта, в диалоговом окне **безопасности элемента** можно выбрать **Настроить безопасность** и нажать кнопку **Подтвердить**. Будет создана ограничивающая политика безопасности, исключающая назначения роли, которые обеспечивают доступ большому количеству пользователей (например, можно удалить назначения роли, которые предоставляют доступ всем пользователям, и оставить назначения роли, которые предоставляют доступ небольшой группе пользователей, например администраторам).  
  
##  <a name="bkmk_remove_manage_subscriptions_permission"></a> Удаление разрешений на управление подписками из роли (основной режим)  
 Чтобы запретить пользователям создавать подписки, удалите задачу **Управление отдельными подписками** из роли. После этого страницы «Подписка» станут недоступны. На веб-портале папка "Мои подписки" отображается пустой (ее удалить нельзя), даже если она до этого содержала подписки. Удаление связанных с подписками задач запрещает пользователям создавать и изменять подписки, но не удаляет существующие подписки, Существующие подписки продолжают действовать до тех пор, пока не будут удалены. Чтобы удалить разрешение:  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 
  
2.  Подключитесь к серверу отчетов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
3.  Разверните узел **Безопасность** .  
  
4.  Разверните узел **роли** и выберите нужную роль.  
  
5.  Щелкните роль правой кнопкой мыши и выберите пункт **Свойства**.  
  
6.  Снимите флажок **Управление отдельными подписками** и задачи **Управление всеми подписками** .  
  
7.  Нажмите кнопку **ОК**, чтобы применить изменения.

  
##  <a name="bkmk_disable_extensions"></a> Отключение модулей доставки  
 Все модули доставки, установленные на сервере отчетов, доступны любому пользователю, который имеет разрешение на создание подписки на данный отчет. Следующие модули доставки доступны и настраиваются автоматически:  
  
-   Общая папка Windows  
  
-   Библиотека SharePoint (доступна только с сайта SharePoint, который интегрирован с сервером отчетов, работающим в режиме интеграции с SharePoint).  
  
 Доставку по электронной почте перед использованием необходимо настроить. Если настройка не выполнена, эта функция недоступна. Дополнительные сведения см. в разделе [Параметры электронной почты — Reporting Services собственном режиме (Configuration Manager)](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).  
  
 Если требуется отключить конкретные модули, можно удалить записи, относящиеся к этим модулям, из файла **RSReportServer.config** . Дополнительные сведения см. в разделе [Reporting Services файлы конфигурации](../../reporting-services/report-server/reporting-services-configuration-files.md) и [Параметры электронной почты — Reporting Services в основном режиме (Configuration Manager)](../install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).  
  
 После удаления модуля доставки он становится недоступным на веб-портале или на сайте SharePoint. При удалении модуля доставок могут появляться неактивные подписки. Обязательно удаляйте подписки или настраивайте их на использование другого модуля доставки, прежде чем удалить какой-либо модуль.  
  
## <a name="see-also"></a>См. также раздел  
 [Подписки и доставка (службы Reporting Services)](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Файлы конфигурации служб Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Configure the web portal](../../reporting-services/report-server/configure-web-portal.md)  (Настройка веб-портала)  
 [Сервер отчетов служб Reporting Services (основной режим)](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Веб-портал сервера отчетов (SSRS в собственном режиме)](../../reporting-services/web-portal-ssrs-native-mode.md)   
 [Защищаемые элементы](../../reporting-services/security/securable-items.md) 
  
