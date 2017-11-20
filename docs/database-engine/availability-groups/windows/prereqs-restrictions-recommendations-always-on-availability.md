---
title: "Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn | Документы Майкрософт"
ms.custom: 
ms.date: 05/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], WSFC clusters
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], Failover Cluster Instances
- Availability Groups [SQL Server], databases
- Availability Groups [SQL Server]
ms.assetid: edbab896-42bb-4d17-8d75-e92ca11f7abb
caps.latest.revision: 151
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5186cc2ea4ed54335c537fc3c0094c38b2c4a80f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="prereqs-restrictions-recommendations---always-on-availability-groups"></a>Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе приводятся рекомендации по развертыванию [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], в т. ч. предварительные условия, ограничения и рекомендации в отношении компьютеров, отказоустойчивых кластеров Windows Server (WSFC), экземпляров сервера и групп доступности. Для каждого из этих компонентов описываются имеющиеся вопросы безопасности и необходимые разрешения.  
  
> [!IMPORTANT]  
>  Перед началом развертывания [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]настоятельно рекомендуется ознакомиться со всеми подразделами данного раздела.  
    
##  <a name="DotNetHotfixes"></a> Исправления .Net, поддерживающие группы доступности  
 Возможно, потребуется установка дополнительных исправлений .Net, в зависимости от того, какие компоненты и возможности [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] будут использоваться вместе с [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Исправления приведены в следующей таблице. Исправления можно устанавливать в любом порядке.  
  
||Зависимый компонент|Исправление|Ссылка|  
|------|-----------------------|------------|----------|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]|Исправление для .Net 3.5 с пакетом обновления 1 (SP1) добавляет в клиент SQL поддержку функций AlwaysOn: Read-intent, readonly и multisubnetfailover. Это исправление необходимо установить на каждом сервере отчетов служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .|KB 2654347 [Исправление для .NET 3.5 с пакетом обновления 1 (SP1), добавляющее поддержку функций AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=242896)|  
  
##  <a name="SystemReqsForAOAG"></a> Рекомендации и системные требования Windows  
 **В этом разделе.**  
  
-   [Контрольный список: требования](#SystemRequirements)  
  
-   [Рекомендации для компьютеров, на которых размещены реплики доступности (ОС Windows](#ComputerRecommendations)  
  
-   [Разрешения](#PermissionsWindows)  
  
-   [Связанные задачи](#RelatedTasksWindows)  
  
-   [См. также](#RelatedContentWS)  
  
###  <a name="SystemRequirements"></a> Контрольный список: требования (ОС Windows)  
 Чтобы обеспечить поддержку функции [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , необходимо, чтобы каждый компьютер, участвующий в одной или нескольких группах доступности, соответствовал следующим основным требованиям.  
  
||Требование|Ссылка|  
|------|-----------------|----------|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Убедитесь, что система не является контроллером домена.|Группы доступности не поддерживаются на контроллерах домена.|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Убедитесь в том, что каждый компьютер работает под управлением Windows Server 2012 или более поздней версии.|[Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Убедитесь, что каждый компьютер является узлом в кластере WSFC.|[Отказоустойчивая кластеризация Windows Server (WSFC) с SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Убедитесь, что кластер WSFC содержит достаточное количество узлов для поддержки требуемых конфигураций групп доступности.|На узле кластера можно размещать только одну реплику доступности для отдельной группы доступности. На каждом отдельном узле кластера один или несколько экземпляров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] могут содержать реплики доступности для многих групп доступности.<br /><br /> Обратитесь к администраторам базы данных, чтобы узнать, сколько узлов кластера требуется для поддержки реплик доступности для планируемых групп доступности.<br /><br /> [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).|  
  
> [!IMPORTANT]  
>  Кроме того, убедитесь, что среда правильно настроена для соединения с группой доступности. Дополнительные сведения см. в разделе [Подключение клиента AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/always-on-client-connectivity-sql-server.md).  
  
###  <a name="ComputerRecommendations"></a> Рекомендации для компьютеров, на которых размещены реплики доступности (ОС Windows)  
  
-   **Сопоставимые системы.**  Для одной группы доступности все реплики доступности должны работать на сопоставимых системах, способных выдержать примерно одинаковую рабочую нагрузку.  
  
-   **Выделенные сетевые адаптеры**  . Для наилучшей производительности при использовании [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]используйте выделенный сетевой адаптер.  
  
-   **Достаточно свободного места на диске.**  Каждый компьютер, на котором экземпляр сервера содержит реплику доступности, должен иметь достаточно свободного места на диске для всех баз данных в группе доступности. Помните, что по мере роста баз данных-источников так же будут расти и соответствующие базы данных-получатели.  
  
###  <a name="PermissionsWindows"></a> Разрешения (ОС Windows)  
 Для администрирования кластера WSFC пользователь должен быть системным администратором на каждом узле кластера.  
  
 Дополнительные сведения об учетной записи для администрирования кластера см. в [Приложении A. Требования к отказоустойчивому кластеру](http://technet.microsoft.com/library/dd197454.aspx).  
  
###  <a name="RelatedTasksWindows"></a> Связанные задачи (ОС Windows)  
  
|Задача|Ссылка|  
|----------|----------|  
|Установите значение HostRecordTTL.|[Изменение параметра HostRecordTTL (с помощью Windows PowerShell)](#ChangeHostRecordTTLps)|  
  
####  <a name="ChangeHostRecordTTLps"></a> Изменение параметра HostRecordTTL (с помощью Windows PowerShell)  
  
1.  Откройте окно Powershell с помощью варианта **Запуск от имени администратора**.  
  
2.  Импортируйте модуль FailoverClusters.  
  
3.  С помощью командлета **Get-ClusterResource** найдите ресурс сетевого имени, а затем с помощью командлета **Set-ClusterParameter** задайте значение **HostRecordTTL** следующим образом:  
  
     Get-ClusterResource "*\<имя_сетевого_ресурса>*" | Set-ClusterParameter HostRecordTTL *\<время_в_секундах>*  
  
     В следующем примере для PowerShell задается значение HostRecordTTL в 300 секунд для сетевого ресурса сетевого имени `SQL Network Name (SQL35)`.  
  
    ```  
    Import-Module FailoverClusters  
  
    $nameResource = "SQL Network Name (SQL35)"  
    Get-ClusterResource $nameResource | Set-ClusterParameter ClusterParameter HostRecordTTL 300  
    ```  
  
    > [!TIP]  
    >  Каждый раз при открытии нового окна PowerShell потребуется импортировать модуль **FailoverClusters** .  
  
##### <a name="related-content-powershell"></a>См. также (PowerShell)  
  
-   [Кластеризация и высокая доступность](http://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (блог группы отказоустойчивой кластеризации и балансировки сетевой нагрузки)  
  
-   [Приступая к работе с Windows PowerShell в отказоустойчивом кластере](http://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Команды ресурса кластера и соответствующие командлеты Windows PowerShell](http://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
###  <a name="RelatedContentWS"></a> См. также (система Windows)  
  
-   [Настройка параметров DNS для многосайтового отказоустойчивого кластера](http://technet.microsoft.com/library/dd197562\(WS.10\).aspx)  
  
-   [Регистрация DNS в ресурсе сетевого имени](http://blogs.msdn.com/b/clustering/archive/2009/07/17/9836756.aspx)  
  

##  <a name="ServerInstance"></a> Предварительные условия и ограничения для экземпляров SQL Server  
 Каждой группе доступности требуется набор партнеров по обеспечению отработки отказа, известных как *реплики доступности*, которые расположены в экземплярах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Данный экземпляр сервера может быть *изолированным экземпляром* или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]*экземпляром отказоустойчивого кластера* .  
  
 **В этом разделе.**  
  
-   [Контрольный список: предварительные требования](#PrerequisitesSI)  
  
-   [Использование потока группами доступности](#ThreadUsage)  
  
-   [Разрешения](#PermissionsSI)  
  
-   [Связанные задачи](#RelatedTasksSI)  
  
-   [См. также](#RelatedContentSI)  
  
###  <a name="PrerequisitesSI"></a> Контрольный список: предварительные требования (экземпляр сервера)  
  
||Предварительные требования|Ссылки|  
|-|------------------|-----------|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Этот компьютер должен быть узлом кластера WSFC. Экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], на которых размещаются реплики доступности для данной группы доступности, размещаются на отдельных узлах одного кластера. При переносе в другой кластер группа доступности может временно находиться в двух кластерах. В SQL Server 2016 появились распределенные группы доступности. В распределенной группе доступности две группы доступности находятся в разных кластерах.|[Отказоустойчивая кластеризация Windows Server (WSFC) с SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)<br /><br /> [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)<br/> <br/> [Распределенные группы доступности (группы доступности AlwaysOn)](../../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Если необходима группа доступности для работы с Kerberos:<br /><br /> Все экземпляры сервера, на которых размещена реплика доступности для группы доступности, должны использовать одинаковые учетные записи службы SQL Server.<br /><br /> Администратору домена необходимо вручную зарегистрировать имя участника-службы (SPN) с помощью службы каталогов Active Directory на учетной записи службы SQL Server для виртуального сетевого имени (VNN) прослушивателя группы доступности. Если имя участника-службы (SPN) зарегистрировано на учетной записи, отличной от учетной записи службы SQL Server, то проверку подлинности пройти не удастся.<br /><br /> <br /><br /> **\*\* Важно! \*\*** При изменении учетной записи службы SQL Server администратору домена необходимо вручную повторно зарегистрировать имя субъекта-службы (SPN).|[Регистрация имя участника-службы для соединений Kerberos](../../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)<br /><br /> **Краткое описание:**<br /><br /> Kerberos и имена участников-служб обеспечивают взаимную проверку подлинности. Имя участника-службы (SPN) сопоставляется с учетной записью Windows, которая запускает службы SQL Server. Если регистрация имени участника-службы (SPN) не была выполнена должным образом или завершилась неудачно, уровень безопасности Windows не может определить учетную запись, связанную с именем участника-службы, и проверка подлинности Kerberos не может использоваться.<br /><br /> <br /><br /> Примечание. Для NTLM нет таких требований.|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Если вы планируете использовать экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для размещения реплики доступности, убедитесь, что понимаете ограничения, связанные с использованием отказоустойчивых кластеров, и что требования для создания такого кластера удовлетворены.|[Необходимые условия и требования, связанные с использованием экземпляра отказоустойчивого кластера SQL Server для размещения реплики доступности](#FciArLimitations) (далее в этом разделе)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|На каждом экземпляре сервера должен быть установлен выпуск [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]Enterprise Edition.|[Возможности, поддерживаемые различными выпусками SQL Server 2016](../../../sql-server/editions-and-supported-features-for-sql-server-2016.md)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Все экземпляры сервера, на которых размещены реплики доступности для одной группы доступности, должны использовать одинаковые параметры сортировки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[Задание или изменение параметров сортировки сервера](../../../relational-databases/collations/set-or-change-the-server-collation.md)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Необходимо включить функцию [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] на каждом экземпляре сервера, на котором будет размещена реплика доступности для группы доступности. На одном компьютере можно включить столько экземпляров серверов, поддерживающих [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , сколько поддерживает установка [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[Включение и отключение групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)<br /><br /> <br /><br /> **\*\* Важно! \*\*** При удалении и повторном создании кластера WSFC необходимо отключить и повторно включить функцию [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в каждом экземпляре сервера, в котором была включена функция [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в исходном кластере.|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Каждый экземпляр сервера должен иметь конечную точку зеркального отображения базы данных. Обратите внимание, что эта конечная точка совместно используется всеми репликами доступности и участниками зеркального отображения базы данных на этом экземпляре сервера.<br /><br /> Если экземпляр сервера, выбранный для размещения реплики доступности, работает под доменной учетной записью и еще не содержит конечной точки зеркального отображения базы данных, то [мастер создания группы доступности](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md) (или [мастер добавления реплики в группу доступности](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)) может создать конечную точку и предоставить учетной записи службы экземпляра сервера разрешение CONNECT, если этот экземпляр запускается с учетной записью службы домена. Но если служба [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] запущена от имени встроенной учетной записи, такой как «Локальная система», «Локальная служба» или «Сетевая служба», или от имени учетной записи, не входящей в домен, то для проверки подлинности конечных точек необходимо пользоваться сертификатами, а мастер не сможет создать точку зеркального отображения базы данных на этом экземпляре сервера. В этом случае рекомендуется создавать конечные точки зеркального отображения базы данных вручную до запуска мастера.<br /><br /> <br /><br /> **\*\* Примечание по безопасности \*\*** . Механизм безопасности транспорта для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] такой же, как и при зеркальном отображении базы данных.|[Конечная точка зеркального отображения базы данных (SQL Server)](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)<br /><br /> [Безопасность транспорта для зеркального отображения баз данных и групп доступности AlwaysOn (SQL Server)](../../../database-engine/database-mirroring/transport-security-database-mirroring-always-on-availability.md)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Если в группу доступности будут добавляться любые базы данных, использующие FILESTREAM, убедитесь, что функция FILESTREAM включена на каждом экземпляре сервера, на котором планируется разместить реплику доступности.|[Включение и настройка FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Если в группу доступности будут добавляться любые автономные базы данных, то убедитесь, что параметру сервера **contained database authentication** присвоено значение **1** на каждом экземпляре, где планируется разместить реплику доступности.|[Параметр конфигурации сервера «проверка подлинности автономной базы данных»](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md)<br /><br /> [Параметры конфигурации сервера (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)|  
  
###  <a name="ThreadUsage"></a> Использование потока группами доступности  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] предъявляет к рабочим потокам следующие требования.  
  
-   На простаивающем экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] используется 0 потоков.  
  
-   Максимальное число потоков, используемых для групп доступности, — это заданный настройками параметр максимального числа потоков сервера ("**max worker threads**") минус 40.  
  
-   Реплики доступности, размещенные на конкретном экземпляре сервера, совместно используют один пул потоков.  
  
     Потоки совместно используются по требованию следующим образом.  
  
    -   Обычно имеется 3–10 общих потоков, но это число может возрасти в зависимости от рабочей нагрузки первичной реплики.  
  
    -   Если заданный поток в течение определенного периода времени простаивает, то он возвращается в общий пул потоков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Обычно неактивный поток освобождается примерно через 15 секунд неактивности. Однако в зависимости от последней активности бездействующий поток может сохраняться дольше.  

    - Экземпляр SQL Server использует до 100 потоков параллельного повтора для вторичных реплик. Каждая база данных использует до половины от общего числа ядер ЦП, но не более 16 потоков на базу данных. Если общее число требуемых потоков для одного экземпляра превышает 100, SQL Server использует один поток повтора для каждой из оставшихся баз данных. Потоки повтора освобождаются примерно через 15 секунд неактивности. 

  
-   Кроме того, группы доступности используют неразделенные потоки следующим образом.  
  
    -   Каждая первичная реплика использует по одному потоку для записи журнала в каждой базе данных-источнике. Кроме того, она использует по одному потоку для отправки журнала в каждой из баз данных-получателей. Потоки отправки журнала освобождаются примерно через 15 секунд неактивности.    
  
    -   Резервное копирование на вторичной реплике удерживает поток на первичной реплике на время операции резервного копирования.  
  
 Дополнительные сведения см. в разделе [Обучающая серия AlwaysOn — HADRON: использование рабочего пула для баз данных с поддержкой HADRON](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx) (блог инженеров CSS [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ).  
  
###  <a name="PermissionsSI"></a> Разрешения (экземпляр сервера)  
  
|Задача|Необходимые разрешения|  
|----------|--------------------------|  
|Создание конечной точки зеркального отображения базы данных|Требуется разрешение CREATE ENDPOINT или членство в предопределенной роли сервера **sysadmin** .  Также требуется разрешение CONTROL ON ENDPOINT. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений на конечные точки (Transact-SQL)](../../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).|  
|Включение [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]|Требуется членство в группе **Администратор** на локальном компьютере и полный контроль над кластером WSFC.|  
  
###  <a name="RelatedTasksSI"></a> Связанные задачи (экземпляр сервера)  
  
|Задача|Раздел|  
|----------|-----------|  
|Определение наличия конечной точки зеркального отображения базы данных|[sys.database_mirroring_endpoints (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)|  
|Создание конечной точки зеркального отображения базы данных (если она еще не существует)|[Создание конечной точки зеркального отображения базы данных с проверкой подлинности Windows (Transact-SQL)](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)<br /><br /> [Использование сертификатов для конечной точки зеркального отображения базы данных (Transact-SQL)](../../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)<br /><br /> [Создание конечной точки зеркального отображения базы данных для групп доступности AlwaysOn (SQL Server PowerShell)](../../../database-engine/availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)|  
|Включение групп доступности|[Включение и отключение групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)|  
  
###  <a name="RelatedContentSI"></a> См. также (экземпляр сервера)  
  
-   [Обучающая серия AlwaysOn — HADRON: использование рабочего пула для баз данных с поддержкой HADRON](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
##  <a name="NetworkConnect"></a> Рекомендации по сетевым возможностям подключения  
 Настоятельно рекомендуется использовать одни и те же сетевые соединения для обмена данными между узлами WSFC и репликами доступности.  Использование отдельных сетевых соединений может привести к непредвиденному поведению в случае отказа даже некоторых из них.  
  
 Например, чтобы группа доступности поддерживала автоматический переход на другой ресурс, вторичная реплика, которая является участником обработки отказа, должна находиться в состоянии SYNCHRONIZED. В случае отказа (даже временного) сетевого соединения с этой вторичной репликой она переходит в состояние UNSYNCHRONIZED и не может начать повторную синхронизацию до тех пор, пока соединение не будет восстановлено. Если кластер WSFC запрашивает автоматический переход на другой ресурс, пока вторичная реплика не синхронизирована, автоматический переход на другой ресурс не выполняется.  
  
##  <a name="ClientConnSupport"></a> Поддержка возможности подключения клиента  
 Сведения о поддержке [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] для обеспечения клиентского соединения см. в разделе [Подключение клиента AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/always-on-client-connectivity-sql-server.md).  
  
##  <a name="FciArLimitations"></a> Предварительные условия и ограничения, связанные с использованием экземпляра отказоустойчивого кластера SQL Server для размещения реплики доступности  
 **В этом разделе.**  
  
-   [Ограничения](#RestrictionsFCI)  
  
-   [Контрольный список: предварительные требования](#PrerequisitesFCI)  
  
-   [Связанные задачи](#RelatedTasksFCIs)  
  
-   [См. также](#RelatedContentFCIs)  
  
###  <a name="RestrictionsFCI"></a> Ограничения (экземпляры отказоустойчивого кластера)  
  
> [!NOTE]  
> Экземпляры отказоустойчивого кластера поддерживают кластерные общие тома (CSV). Дополнительные сведения о CSV-файле см. в разделе [Основные сведения о кластерных общих томах в отказоустойчивом кластере](http://technet.microsoft.com/library/dd759255.aspx).  
  
-   **На узле кластера FCI может быть размещена только одна реплика для одной группы доступности.** При добавлении в FCI реплики доступности узлы кластера WSFC, которые являются возможными владельцами FCI, не могут содержать другую реплику той же группы доступности.  
  
     Более того, каждая реплика должна быть размещена в экземпляре SQL Server 2016, который находится на отдельном узле WSFC того же кластера WSFC. Единственное исключение состоит в том, что при переносе в другой кластер группа доступности может временно находиться в двух кластерах.  
  
-   **FCI не поддерживают автоматический переход на другой ресурс для групп доступности.**  FCI не поддерживают автоматический переход на другой ресурс для групп доступности, поэтому любая реплика доступности, размещенная в FCI, может быть настроена только для перехода на другой ресурс вручную.  
  
-   **Изменение сетевого имени отказоустойчивого кластера FCI.**  Если необходимо изменить сетевое имя FCI, на котором размещена реплика доступности, то сначала необходимо удалить эту реплику из группы доступности, а затем вернуть ее обратно в эту же группу доступности. Удалить основную реплику нельзя, поэтому при переименовании экземпляра отказоустойчивого кластера, на котором размещена основная реплика, необходимо выполнить отработку отказа на вторичную реплику, удалить из группы доступности основную реплику и добавить ее снова. Обратите внимание, что переименование FCI может привести к изменению URL-адреса конечной точки зеркального отображения базы данных. При добавлении реплики убедитесь, что указываете URL-адрес текущей конечной точки.  
  
###  <a name="PrerequisitesFCI"></a> Контрольный список: предварительные требования FCI)  
  
||Предварительные требования|Ссылка|  
|-|------------------|----------|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Убедитесь, что каждый экземпляр отказоустойчивого кластера SQL Server обладает требуемым пространством хранения, как и в случае со стандартным экземпляром отказоустойчивого кластера SQL Server.||  
  
###  <a name="RelatedTasksFCIs"></a> Связанные задачи (FCI)  
  
|Задача|Раздел|  
|----------|-----------|  
|Установка отказоустойчивого кластера SQL Server|[Создание отказоустойчивого кластера SQL Server (программа установки)](../../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)|  
|Обновление существующего отказоустойчивого кластера SQL Server на месте|[Обновление экземпляра отказоустойчивого кластера SQL Server (программа установки)](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md)|  
|Обслуживание существующего отказоустойчивого кластера SQL Server|[Добавление или удаление узлов отказоустойчивого кластера SQL Server (программа установки)](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)|  
  
###  <a name="RelatedContentFCIs"></a> См. также (FCI)  
  
-   [Отказоустойчивая кластеризация и группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)  
  
-   [Руководство по архитектуре AlwaysOn. Построение решения для обеспечения высокого уровня доступности и аварийного восстановления с помощью экземпляров отказоустойчивого кластера и групп доступности](http://technet.microsoft.com/library/jj215886.aspx)  
  
##  <a name="PrerequisitesForAGs"></a> Обязательные условия и ограничения для группы доступности  
 **В этом разделе.**  
  
-   [Ограничения](#RestrictionsAG)  
  
-   [Требования](#RequirementsAG)  
  
-   [Безопасность](#SecurityAG)  
  
-   [Связанные задачи](#RelatedTasksAGs)  
  
###  <a name="RestrictionsAG"></a> Ограничения (группы доступности)  
  
-   **Реплики доступности должны размещаться на разных узлах одного кластера WSFC.** Для каждой группы доступности реплики доступности должны находиться на разных экземплярах сервера, работающих на разных узлах одного и того же кластера WSFC. Единственное исключение состоит в том, что при переносе в другой кластер группа доступности может временно находиться в двух кластерах.  
  
    > [!NOTE]  
    >  На каждой виртуальной машине на одном физическом компьютере может размещаться реплика доступности для одной и той же группы доступности, так как каждая виртуальная машина работает как отдельный компьютер.  
  
-   **Уникальное имя группы доступности.** Имя каждой группы доступности должно быть уникальным в пределах кластера WSFC. Максимальная длина имени группы доступности составляет 128 символов.  
  
-   **Реплики доступности.**  Каждая группа доступности поддерживает одну первичную реплику и до восьми вторичных реплик. Все реплики могут выполняться в режиме асинхронной фиксации или до трех из них могут работать в режиме синхронной фиксации (одна первичная реплика с двумя синхронными вторичными репликами).  
  
-   **Максимальное количество групп доступности и баз данных доступности на компьютер** . Фактическое количество баз данных и групп доступности, которые можно разместить на компьютере (физической или виртуальной машине), зависит от оборудования и загрузки, но какое-либо строгое ограничение отсутствует. В корпорации Майкрософт проводились интенсивные испытания 10 групп доступности и 100 баз данных на один физический компьютер. К символам перегрузки систем могут относиться, помимо прочего, исчерпание ресурса рабочего потока, увеличенное время ответа для системных представлений групп доступности и динамических административных представлений или остановка дампов системы диспетчера. Обязательно проведите тщательное тестирование среды с рабочей нагрузкой, чтобы убедиться, что система в состоянии обрабатывать пиковую нагрузку в рамках соглашений об уровне обслуживания приложений. При рассмотрении соглашений об уровне обслуживания обязательно проверяйте нагрузку в условиях сбоя, а также ожидаемое время ответа.  
  
-   **Не используйте диспетчер отказоустойчивости кластеров для управления группами доступности.**  
  
     Например:  
  
    -   Не изменяйте свойства групп доступности, такие как список возможных владельцев.  
  
    -   Не используйте диспетчер отказоустойчивости кластеров для переключения групп доступности. Необходимо использовать [!INCLUDE[tsql](../../../includes/tsql-md.md)] или среду [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
###  <a name="RequirementsAG"></a> Предварительные условия (группы доступности)  
 При создании или повторной настройке конфигурации групп доступности обязательно следуйте описанным ниже требованиям.  
  
||Предварительные требования|Description|  
|-|------------------|-----------------|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Если вы планируете использовать экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для размещения реплики доступности, убедитесь, что понимаете ограничения, связанные с использованием отказоустойчивых кластеров, и что требования для создания такого кластера удовлетворены.|[Предварительные условия и ограничения, связанные с использованием экземпляра отказоустойчивого кластера SQL Server для размещения реплики доступности](#FciArLimitations) (ранее в этом разделе)|  
  
###  <a name="SecurityAG"></a> Безопасность (группы доступности)  
  
-   Параметры безопасности наследуются от WSFC. Отказоустойчивая кластеризация Windows Server обеспечивает два уровня безопасности пользователей на уровне всего кластера.  
  
    -   Доступ только для чтения.  
  
    -   Полный доступ  
  
         [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] должен обладать всеми возможностями управления, поэтому использование [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] дает ему полный контроль над кластером (через идентификатор безопасности службы).  
  
         Нельзя напрямую повышать или снижать уровень безопасности для экземпляра сервера средствами диспетчера кластера. Для управления сеансами безопасности кластера следует использовать диспетчер конфигураций [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или эквивалент WMI из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Каждый экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должен иметь разрешения для доступа к реестру, кластеру и т. д.  
  
-   Для подключений между экземплярами сервера, на которых размещаются реплики доступности [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , рекомендуется использовать шифрование.  
  
#### <a name="permissions-availability-groups"></a>Разрешения (группы доступности)  
  
|Задача|Необходимые разрешения|  
|----------|--------------------------|  
|Создание группы доступности|Требуется членство в предопределенной роли сервера **sysadmin** и разрешение сервера CREATE AVAILABILITY GROUP, ALTER ANY AVAILABILITY GROUP или CONTROL SERVER.|  
|Изменение группы доступности.|Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.<br /><br /> Кроме того, для присоединения базы данных к группе доступности требуется членство в предопределенной роли базы данных **db_owner** .|  
|Удаление группы доступности|Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER. Для удаления группы доступности, которая не размещена в локальной реплике, необходимо разрешение CONTROL SERVER или разрешение CONTROL на эту группу доступности.|  
  
###  <a name="RelatedTasksAGs"></a> Связанные задачи (группы доступности)  
  
|Задача|Раздел|  
|----------|-----------|  
|Создание группы доступности|[Использование группы доступности (мастер создания группы доступности)](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)<br /><br /> [Создание группы доступности (Transact-SQL)](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)<br /><br /> [Создание группы доступности (SQL Server PowerShell)](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)<br /><br /> [Укажите URL-адрес конечной точки при добавлении или изменении реплики доступности (SQL Server)](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)|  
|Изменение числа реплик доступности|[Добавление вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [Присоединение вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [Удаление вторичной реплики из группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
|Создание прослушивателя группы доступности|[Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)|  
|Удаление группы доступности|[Удаление группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md)|  
  
##  <a name="PrerequisitesForDbs"></a> Обязательные условия и ограничения для базы данных доступности  
 Для добавления в группу доступности база данных должна соответствовать следующим предварительным условиям и ограничениям.  
  
 **В этом разделе.**  
  
-   [Требования](#RequirementsDb)  
  
-   [Ограничения](#RestrictionsDb)  
  
-   [Рекомендации для компьютеров, на которых размещены реплики доступности (ОС Windows](#TDEdbs)  
  
-   [Разрешения](#PermissionsDbs)  
  
-   [Связанные задачи](#RelatedTasksADb)  
  
###  <a name="RequirementsDb"></a> Контрольный список: требования (базы данных доступности)  
 Для добавления в группу доступности база данных должна соответствовать следующим требованиям.  
  
||Требования|Ссылка|  
|-|------------------|----------|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Быть пользовательской базой данных. Системные базы данных не могут принадлежать к группе доступности.||  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Находиться на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором создана группа доступности, и быть доступной для экземпляра сервера.||  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Быть базой, доступной для чтения и записи. Базы данных только для чтения не могут быть добавлены в группу доступности.|[sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) (**is_read_only** = 0)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Быть многопользовательской базой данных.|[sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) (**user_access** = 0)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Не использовать параметр AUTO_CLOSE.|[sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) (**is_auto_close_on** = 0)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Используйте модель полного восстановления (также известную как режим полного восстановления).|[sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) (**recovery_model** = 1)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Необходима по крайней мере одна полная резервная копия базы данных.<br /><br /> Примечание. После переключения базы данных в режим полного восстановления потребуется создать полную резервную копию для включения цепочки журналов полного восстановления.|[Создание полной резервной копии базы данных (SQL Server)](../../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Не принадлежать ни к одной другой группе доступности.|[sys.databases](../../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) (**group_database_id** = NULL)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Не быть настроенной для зеркального отображения базы данных.|[sys.database_mirroring](../../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md) (если база данных не участвует в зеркальном отображении, все столбцы с префиксом "mirroring_" имеют значение NULL)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Перед добавлением в группу доступности базы данных, в которой используется FILESTREAM, следует убедиться, что FILESTREAM поддерживается на всех экземплярах серверов, на которых размещены или будут размещены реплики доступности для группы доступности.|[Включение и настройка FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Перед добавлением автономной базы данных в группу доступности убедитесь, что параметру сервера **contained database authentication** присвоено значение **1** на каждом экземпляре сервера, где размещена или будет размещена реплика доступности для группы доступности.|[Параметр конфигурации сервера «проверка подлинности автономной базы данных»](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md)<br /><br /> [Параметры конфигурации сервера (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)|  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] работает с любым поддерживаемым уровнем совместимости базы данных.  
  
###  <a name="RestrictionsDb"></a> Ограничения (базы данных доступности)  
  
-   Если путь к файлу (в том числе буква диска) базы данных-получателя отличается от пути в соответствующей базе данных-источнике, применимы следующие ограничения.  
  
    -   **[!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]/[!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)]:**  Параметр **Полная** не поддерживается (на странице[Выбор начальной синхронизации данных](../../../database-engine/availability-groups/windows/select-initial-data-synchronization-page-always-on-availability-group-wizards.md) ).  
  
    -   **RESTORE WITH MOVE:**  чтобы создать базы данных-получатели, файлы базы данных должны обладать атрибутом RESTORED WITH MOVE на каждом экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором размещена вторичная реплика.  
  
    -   **Воздействие на операции добавления файлов.**  Операция добавления файлов, выполняемая позднее в основной реплике, может завершиться неудачей в базах данных-получателях. Эта ошибка может вызвать приостановку работы баз данных-получателей. Это, в свою очередь, вызовет переход дополнительных реплик в состояние NOT SYNCHRONIZING.  
  
        > [!NOTE]  
        >  Дополнительные сведения об отсутствии отклика на неудачную операцию добавления файла см. в разделе [Устранение неполадок с операцией добавления файлов, давшей сбой (группы доступности AlwaysOn)](../../../database-engine/availability-groups/windows/troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md).  
  
-   Нельзя удалить базу данных, которая принадлежит какой-либо группе доступности.  
  
###  <a name="TDEdbs"></a> Дальнейшие действия для баз данных, защищаемых прозрачным шифрованием  
 Если используется прозрачное шифрование данных (TDE), то сертификат или асимметричный ключ службы для создания и расшифровки других ключей должен быть одинаков на всех экземплярах сервера, где размещены реплики группы доступности. Дополнительные сведения см. в разделе [Перемещение базы данных, защищаемой прозрачным шифрованием, в другой экземпляр SQL Server](../../../relational-databases/security/encryption/move-a-tde-protected-database-to-another-sql-server.md).  
  
###  <a name="PermissionsDbs"></a> Разрешения (базы данных доступности)  
 Необходимо разрешение ALTER на базу данных.  
  
###  <a name="RelatedTasksADb"></a> Связанные задачи (базы данных доступности)  
  
|Задача|Раздел|  
|----------|-----------|  
|Подготовка базы данных-получателя (вручную)|[Подготовка базы данных-получателя для присоединения к группе доступности вручную (SQL Server)](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)|  
|Присоединение базы данных-получателя к группе доступности (вручную)|[Присоединение базы данных-получателя к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)|  
|Изменение числа баз данных доступности|[Добавление базы данных в группу доступности (SQL Server)](../../../database-engine/availability-groups/windows/availability-group-add-a-database.md)<br /><br /> [Удаление базы данных-получателя из группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-a-secondary-database-from-an-availability-group-sql-server.md)<br /><br /> [Удаление базы данных-источника из группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md)|  
  
##  <a name="RelatedContent"></a> См. также  
  
-   [Руководство по решениям режима AlwaysOn в Microsoft SQL Server для обеспечения высокой доступности и аварийного восстановления](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [Блоги команды разработчиков SQL Server AlwaysOn: официальный блог по SQL Server AlwaysOn](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
-   [Обучающая серия AlwaysOn — HADRON: использование рабочего пула для баз данных с поддержкой HADRON](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Подключение клиента AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/always-on-client-connectivity-sql-server.md)  
  
    
  
--------------------------------------------------  


