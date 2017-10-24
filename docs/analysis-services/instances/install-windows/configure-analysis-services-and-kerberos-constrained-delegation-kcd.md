---
title: "Настройка Analysis Services и ограниченного делегирования Kerberos (KCD) | Документы Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0006e143-d3ba-4d10-a415-e42c45e2bb0a
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4c13b9095224d1c33e09c9513121e46483da05c0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="configure-analysis-services-and-kerberos-constrained-delegation-kcd"></a>Настройка служб Analysis Services и ограниченного делегирования Kerberos (KCD)
  Ограниченное делегирование Kerberos (KCD) — это протокол проверки подлинности, который можно настроить с проверкой подлинности Windows для делегирования клиентских учетных данных от службы к службе в вашей среде. Для проверки подлинности Kerberos требуется дополнительная инфраструктура, например контроллер домена, и дополнительная настройка среды. KCD является обязательным в некоторых сценариях, включающих данные [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] с SharePoint 2016. В SharePoint 2016 службы Excel перемещены за пределы фермы SharePoint на отдельный новый сервер **Office Online Server**. Так как Office Online Server является отдельным, существует возросшая потребность в способе делегирования клиентских учетных данных в типичных сценариях двух прыжков.  
  
||  
|-|  
|**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2016|  
  
## <a name="overview"></a>Обзор  
 Ограниченное делегирование Kerberos позволяет учетной записи олицетворять другую учетную запись для предоставления доступа к ресурсам. Олицетворяющая учетная запись будет учетной записью службы, назначенной веб-приложению, или учетной записью компьютера веб-сервера, а олицетворяемая учетная запись будет учетной записью пользователя, которому требуется доступ к ресурсам. KCD работает на уровне службы, чтобы олицетворяющая учетная запись могла предоставлять доступ к выбранным службам на сервере, в то время как доступ к другим службам на этом сервере или к службам на других серверах запрещен.  
  
 В разделах этой статьи дается обзор распространенных сценариев с [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , в которых требуется KCD, а также приводится пример развертывания сервера с общей сводкой того, что необходимо установить и настроить. Ссылки на более подробные сведения о рассматриваемых технологиях, таких как контроллеры домена и KCD, см. в разделе [Дополнительные сведения и материалы сообщества](#bkmk_moreinfo) .  
  
## <a name="scenario-1-workbook-as-data-source-wds"></a>Сценарий 1. Книга в качестве источника данных (WDS)  
 ![1. в разделе](../../../analysis-services/instances/install-windows/media/ssas-callout1.png "1 в разделе") Office Online Server открывает книгу Excel и ![. в разделе 2](../../../analysis-services/instances/install-windows/media/ssas-callout2.png ". в разделе 2") обнаруживает подключение данных к другой книге. Office Online Server отправляет запрос на [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] при использовании службы перенаправителя ![. в разделе 3](../../../analysis-services/instances/install-windows/media/ssas-callout3.png ". в разделе 3") , чтобы открыть вторую книгу и данные ![4 в разделе](../../../analysis-services/instances/install-windows/media/ssas-callout4.png "4 в разделе ").  
  
 В этом сценарии пользовательские учетные данные нужно делегировать из Office Online Server в службу перенаправителя SharePoint [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в SharePoint.  
  
 ![книга в качестве источника данных](../../../analysis-services/instances/install-windows/media/ssas-kcd-wtih-wds.png "книга в качестве источника данных")  
  
## <a name="scenario-2-an-analysis-services-tabular-model-links-to-an-excel-workbook"></a>Сценарий 2. Табличная модель служб Analysis Services ссылается на книгу Excel  
 Модели служб Analysis Services табличной ![1 в разделе](../../../analysis-services/instances/install-windows/media/ssas-callout1.png "1 в разделе") ссылки на книгу Excel, которая содержит модель Power Pivot. В этом сценарии, когда [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] загружает табличную модель, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] обнаруживает ссылку на эту книгу. При обработке модели [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] отправляет запрос в SharePoint, чтобы загрузить книгу. В этом сценарии клиентские учетные данные **не** требуется делегировать из служб Analysis Services в SharePoint, однако клиентское приложение может перезаписать сведения источника данных во внешней привязке. Если запрос внешней привязки предписывает олицетворять текущего пользователя, то пользовательские учетные данные необходимо делегировать, что требует настройки KCD между [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и SharePoint.  
  
 ![office online server](../../../analysis-services/instances/install-windows/media/ssas-kcd-wtih-oos.png "office online server")  
  
## <a name="example-deployment-of-kcd-with-office-online-server-and-analysis-services"></a>Пример развертывания KCD с Office Online Server и службами Analysis Services  
 В этом разделе описывается пример развертывания, в котором используются четыре компьютера. В следующих разделах приведены основные шаги установки и настройки для каждого компьютера. Перед началом развертывания рекомендуется привести компьютеры в актуальное состояние с помощью исправлений ОС и знать имена компьютеров, поскольку они необходимы в некоторых шагах настройки.  
  
-   Контроллер домена  
  
-   Ядро СУБД SQL Server и службы Analysis Services в режиме Power Pivot. Экземпляр ядра базы данных будет использоваться для баз данных контента SharePoint.  
  
-   Сервер SharePoint 2016  
  
-   Office Online Server  
  
 ![domain controller](../../../analysis-services/instances/install-windows/media/ssas-kcd-domainserver-icon.png "domain controller")  
  
### <a name="domain-controller"></a>Контроллер домена  
 Ниже приведен краткий обзор того, что следует установить для контроллера домена (DC).  
  
-   **Роль:** доменные службы Active Directory. Общие сведения см. в разделе [Настройка Active Directory (AD DS) в Windows Server 2012](http://sharepointgeorge.com/2012/configuring-active-directory-ad-ds-in-windows-server-2012/).  
  
-   **Роль:** DNS-сервер  
  
-   **Компонент:** компоненты .NET Framework 3.5 или .NET Framework 3.5  
  
-   **Компонент:** средства удаленного администрирования сервера и средства администрирования ролей  
  
-   Настройте Active Directory, чтобы создать новый лес и присоединить компьютеры к домену. Прежде чем пытаться добавить в частный домен другие компьютеры, необходимо настроить в DNS на клиентских компьютерах IP-адрес контроллера домена. На компьютере контроллера домена запустите `ipconfig /all` , чтобы получить адреса IPv4 и IPv6 для следующего шага.  
  
-   Рекомендуется настроить оба адреса IPv4 и IPv6. Это можно сделать в панели управления Windows следующим образом.  
  
    1.  Щелкните **Центр управления сетями и общим доступом**.  
  
    2.  Щелкните Ethernet-подключение.  
  
    3.  Нажмите кнопку **Свойства**.  
  
    4.  Щелкните **IP версии 6 (TCP/IPv6)**.  
  
    5.  Нажмите кнопку **Свойства**.  
  
    6.  Щелкните **Использовать следующие адреса DNS-серверов**.  
  
    7.  Введите IP-адрес из команды ipconfig.  
  
    8.  Нажмите кнопку **Дополнительно** , перейдите на вкладку **DNS** и проверьте правильность DNS-суффиксов.  
  
    9. Щелкните **Дописывать следующие DNS-суффиксы**.  
  
    10. Повторите эти шаги для IPv4.  
  
-   **Примечание** . Компьютеры можно присоединить к домену с помощью панели управления Windows в разделе "Параметры системы". Дополнительные сведения см. в разделе [Присоединение Windows Server 2012 к домену](http://social.technet.microsoft.com/wiki/contents/articles/20260.how-to-join-windows-server-2012-to-a-domain.aspx).  
  
 ![SSAS-сервере в режиме powerpivot](../../../analysis-services/instances/install-windows/media/ssas-kcd-powerpivotserver-icon.png "ssas-сервере в режиме powerpivot")  
  
### <a name="2016-sql-server-database-engine-and-analysis-services-in-power-pivot-mode"></a>Ядро СУБД SQL Server 2016 и службы Analysis Services в режиме Power Pivot  
 Ниже приведено краткое описание того, что следует установить на компьютере [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 ![Примечание](../../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "Примечание") в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] мастер установки [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в Power Pivot режиме устанавливается как часть рабочего процесса выбора компонентов.  
  
1.  Запустите мастер установки [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] и на странице выбора компонентов щелкните ядро СУБД, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]и средства управления. На последующих этапах работы мастера установки можно указать режим [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
2.  Для настройки экземпляра настройте именованный экземпляр POWERPIVOT.  
  
3.  На странице настройки служб Analysis Services настройте режим **Power Pivot** для сервера служб Analysis Services и добавьте **имя компьютера** Office Online Server в список администраторов сервера служб Analysis Services. Дополнительные сведения см. в разделе [Install Analysis Services in Power Pivot Mode](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md).  
  
4.  Обратите внимание, что по умолчанию тип объекта "Компьютер" не включен в поиск. Нажмите кнопку ![выберите объекты для добавления учетной записи компьютера](../../../analysis-services/instances/install-windows/media/ss-objects-button.png "выберите объекты для добавления учетной записи компьютера") добавлен объект компьютеров.  
  
     ![Добавление учетных записей компьютеров в качестве администраторов служб ssas](../../../analysis-services/instances/media/ssas-in-ssms-computerobjects.png "добавить учетные записи компьютеров в качестве администраторов служб ssas")  
  
5.  Создайте имена субъектов-служб (SPN) для экземпляра служб Analysis Services.  
  
     Ниже приведены полезные команды имен субъектов-служб.  
  
    -   Получение списка SPN для конкретного имени учетной записи, в которой работает интересующая служба: `SetSPN -l <account-name>`  
  
    -   Задание SPN для учетной записи, в которой работает интересующая служба: `SetSPN -a <SPN> <account-name>`  
  
    -   Удаление SPN из конкретного имени учетной записи, в которой работает интересующая служба: `SetSPN -D <SPN> <account-name>`  
  
    -   Поиск повторяющихся SPN: `SetSPN -X`  
  
     SPN для экземпляра PowerPivot будет в следующей форме:  
  
    ```  
    MSSQLSvc.3/\<Fully Qualified Domain Name (FQDN)>:POWERPIVOT  
    MSSQLSvc.3/<NetBIOS Name>:POWERPIVOT  
    ```  
  
     Здесь полное доменное имя и имя NetBIOS являются именем компьютера, на котором размещается экземпляр. Эти SPN будут размещены в учетной записи домена, который используется для учетной записи службы.  Если используется сетевая служба, локальная система или идентификатор службы, вы захотите поместить SPN в учетную запись компьютера домена.  Если используется учетная запись пользователя домена, вы разместите SPN в этой учетной записи.  
  
6.  Создайте SPN для службы браузера SQL на компьютере служб Analysis Services.  
  
     [Дополнительные сведения](https://support.microsoft.com/en-us/kb/950599)  
  
7.  **Настройте параметры ограниченного делегирования** в учетной записи служб Analysis Services для любого внешнего источника, от которого вы будете обновляться, такого как SQL Server или файлы Excel. В учетной записи служб Analysis Services мы хотим убедиться, что установлено следующее.  
  
     **Примечание** . Если в разделе "Пользователи и компьютеры Active Directory" отсутствует вкладка делегирования для учетной записи, значит, для этой учетной записи нет SPN.  Чтобы эта вкладка появилась, можно добавить фиктивный SPN, например `my/spn`.  
  
     **Доверять этому пользователю делегирование указанных служб** и **Использовать любой протокол проверки подлинности**.  
  
     Это называется ограниченным делегированием и является обязательным, поскольку токен Windows будет получен из службы Claims to Windows Token Services (C2WTS), которая требует ограниченное делегирование со сменой протоколов.  
  
     ![Службы Analysis Services — ограниченное делегирование](../../../analysis-services/instances/install-windows/media/analysis-services-constrained-delegation.png "службы Analysis Services — ограниченного делегирования")  
  
     Кроме того, потребуется добавить службы, доступ к которым будет делегироваться. Это будет зависеть от среды.  
  
### <a name="office-online-server"></a>Office Online Server  
  
1.  Установите Office Online Server.  
  
2.  **Настройте Office Online Server** для подключения к серверу [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Обратите внимание, что учетная запись компьютера Office Online Server должна быть администратором на сервере [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Это было выполнено в предыдущем разделе этой статьи, посвященном установке сервера [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
    1.  На сервере Office Online Server откройте окно PowerShell с правами администратора и выполните следующую команду.  
  
    2.  `New-OfficeWebAppsExcelBIServer –ServerId <AS instance name>`  
  
    3.  Образец. `New-OfficeWebAppsExcelBIServer –ServerId "MTGQLSERVER-13\POWERPIVOT"`  
  
3.  **Настройте Active Directory** , чтобы разрешить учетной записи компьютера Office Online Server олицетворять пользователей для учетной записи службы SharePoint. Итак, установите свойство делегирования в субъекте, запускающем пул приложений для веб-служб SharePoint, на Office Online Server: команды PowerShell в этом разделе требуют объекты PowerShell Active Directory (AD).  
  
    1.  Получите удостоверение Active Directory сервера Office Online Server.  
  
        ```  
        $computer1 = Get-ADComputer -Identity [ComputerName]  
        ```  
  
         Чтобы найти имя субъекта, посмотрите имя пользователя w3wp.exe в разделе "Диспетчер задач"/"Сведения". Например, svcSharePoint.  
  
        ```  
        Set-ADUser svcSharePoint -PrincipalsAllowedToDelegateToAccount $computer1  
  
        ```  
  
    2.  Чтобы проверить правильность установки свойства:  
  
    3.  ```  
        Get-ADUser svcSharePoint –Properties PrincipalsAllowedToDelegateToAccount  
        ```  
  
4.  **Настройте параметры ограниченного делегирования** в учетной записи Office Online Server для экземпляра Power Pivot служб Analysis Services. Это должна быть учетная запись, в которой работает Office Online Server. В учетной записи Office Online Server мы хотим убедиться, что установлено следующее.  
  
     **Примечание** . Если в разделе "Пользователи и компьютеры Active Directory" отсутствует вкладка делегирования для учетной записи, значит, для этой учетной записи нет SPN.  Чтобы эта вкладка появилась, можно добавить фиктивный SPN, например `my/spn`.  
  
     **Доверять этому пользователю делегирование указанных служб** и **Использовать любой протокол проверки подлинности**.  
  
     Это называется ограниченным делегированием и является обязательным, поскольку токен Windows будет получен из службы Claims to Windows Token Services (C2WTS), которая требует ограниченное делегирование со сменой протоколов.  Затем следует разрешить делегирование именам субъектов-служб MSOLAPSvc.3 и MSOLAPDisco.3, созданным ранее.  
  
5.  Настройте службу Claims to Windows Token Service (C2WTS). **Это необходимо для сценария 1**. Дополнительные сведения см. в разделе [Обзор службы Claims to Windows Token Service (c2WTS)](https://msdn.microsoft.com/library/ee517278.aspx).  
  
6.  **Настройте параметры ограниченного делегирования** в учетной записи службы C2WTS.  Эти параметры должны соответствовать тому, что вы делали на шаге 4.  
  
 ![сервер SharePoint](../../../analysis-services/instances/install-windows/media/ssas-kcd-sharepointserver-icon.png "сервер sharepoint")  
  
### <a name="sharepoint-server-2016"></a>SharePoint Server 2016  
 Ниже приведен краткий обзор установки SharePoint Server.  
  
1.  Запуск предварительного установщика SharePoint.  
  
2.  Запуск и установка SharePoint и выбор роли установки **Ферма с одним сервером** .  
  
3.  Запуск надстройки PowerPivot для SharePoint (spPowerPivot16.msi). Дополнительные сведения см. в разделе [Установка или удаление надстройки Power Pivot для надстройки SharePoint (SharePoint 2016)](../../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2016.md)  
  
4.  Запуск мастера настройки PowerPivot. См. раздел [Средства настройки PowerPivot](../../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md).  
  
5.  Подключение SharePoint к Office Online Server.    ??Configure_xlwac_on_SPO.ps1 ??  
  
6.  Настройка поставщиков проверки подлинности SharePoint для Kerberos. **Это требуется для сценария 1**. Дополнительные сведения см. в разделе [Планирование проверки подлинности Kerberos в SharePoint 2013](https://technet.microsoft.com/library/ee806870.aspx).  
  
##  <a name="bkmk_moreinfo"></a> Дополнительные сведения и материалы сообщества  
 [Kerberos для занятого администратора](http://blogs.technet.com/b/askds/archive/2008/03/06/kerberos-for-the-busy-admin.aspx)  
  
 [Основные сведения о двойном прыжке Kerberos](http://blogs.technet.com/b/askds/archive/2008/06/13/understanding-kerberos-double-hop.aspx)  
  
 [Все о .Net и SharePoint](http://sbrickey.com/Tech/Blog/Post/Kerberos_Primer)  
  
 [Ограниченное делегирование Kerberos на основе ресурсов](http://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)  
  
 [Начало работы с KERBEROS — видео](http://blog.martinlund.it/kerberos-primer/)  
  
 [Диспетчер конфигурации Microsoft® Kerberos для SQL Server®](http://www.microsoft.com/en-us/download/details.aspx?id=39046)  
  
  

