---
title: Перенос установки служб Reporting Services (режим интеграции с SharePoint) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 61290949-690a-4e19-b078-57c99b6b30fa
caps.latest.revision: 21
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bfca955a9c6e2f27835cff6ae6af2531a4e743c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37242674"
---
# <a name="migrate-a-reporting-services-installation-sharepoint-mode"></a>Перенос установки служб Reporting Services (режим интеграции с SharePoint)
  В этом разделе дается обзор шагов, необходимых для миграции развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint из одной среды SharePoint в другую. Конкретные шаги могут различаться в зависимости от версии, с которой выполняется перенос. Дополнительные сведения о сценариях обновления и переноса в режиме интеграции с SharePoint см. в разделе [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md). Если требуется только скопировать элементы отчета с одного сервера на другой, см. в разделе [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
 Сведения о миграции развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , работающих в собственном режиме, см. в статье [Перенос установки служб Reporting Services (собственный режим)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010 и SharePoint 2013|  
  
 Обычная причина выполнения миграции — обновление развертывания SharePoint 2010 до SharePoint 2013. SharePoint 2013 не поддерживает обновление на месте с SharePoint 2010, поэтому необходимо выполнить процедуру **обновления базы данных присоединения** или перенести только содержимое.  
  
 Дополнительные сведения об обновлении SharePoint 2013 см. в следующих материалах:  
  
-   [Общие сведения о процессе обновления до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Обновление баз данных с SharePoint 2010 до SharePoint 2013](http://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
-   [Перемещение баз данных содержимого в SharePoint 2013](http://technet.microsoft.com/library/cc262792.aspx).  
  
 
  
##  <a name="bkmk_prior_versions"></a> Перенос из версий служб Reporting Services в режиме интеграции SharePoint, предшествующих SQL Server 2012  
 Архитектура служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint изменилась в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], включая схему базы данных приложения службы. Если нужно перенести систему в [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] в режиме интеграции с SharePoint с версий, предшествующих [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], сначала создайте новую среду SharePoint, установив SharePoint и службы [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. Дополнительные сведения см. в разделе [SharePoint режим установки служб Reporting Services &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
 Как только новая среда SharePoint будет запущена, можно выбрать между переносом только содержимого и полным переносом на уровне баз данных, включая базы данных содержимого.  
  
###  <a name="bkmk_content_only_migration"></a> Перенос только содержимого  
 **Перенос только содержимого служб Reporting Services** . Если требуется скопировать содержимое [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в новую ферму, то необходимо использовать такие инструменты, как **rs.exe** , чтобы скопировать содержимое в новый установленный экземпляр SharePoint. Дополнительные сведения о переносах только содержимого см. в следующих материалах:  
  
-   **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .** Скрипты могут переносить содержимое и ресурсы между серверами отчетов в собственном режиме и режиме интеграции с SharePoint. Дополнительные сведения см. в разделе [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md) и [скрипт RS.exe служб Reporting Services, который переносит содержимое с одного сервера отчетов на другой](http://azuresql.codeplex.com/releases/view/115207).  
  
-   **Средство миграции служб Reporting Services.** Это средство миграции может скопировать элементы отчета с сервера, работающего в собственном режиме, на сервер, работающий в режиме интеграции с SharePoint. Дополнительные сведения см. в разделе [средство миграции служб Reporting Services](http://www.microsoft.com/download/details.aspx?id=29560).  
  
###  <a name="bkmk_full_migration"></a> Полный перенос  
 **Полная миграция** . При переносе в новую ферму баз данных содержимого SharePoint вместе с базами данных каталогов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно использовать серию параметров архивации и восстановления, представленных в данном разделе. В некоторых случаях на этапе восстановления необходимо использовать инструменты, отличные от инструментов, которые использовались при резервном копировании. Например, диспетчер конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно использовать для резервного копирования ключей шифрования из предыдущей версии [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Но для восстановления ключей шифрования в установку [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint необходимо использовать центр администрирования SharePoint или PowerShell.  
  
####  <a name="bkmk_databases"></a> Базы данных, доступные для просмотра после завершения миграции  
 В следующей таблице описаны базы данных SQL Server, которые связаны с [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и доступны после успешного переноса установки SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
|База данных|Пример имени||  
|--------------|------------------|-|  
|База данных каталогов|ReportingService_[идентификатор GUID приложения службы] **(\*)**|Пользователь выполняет перенос.|  
|Временная база данных|ReportingService_[идентификатор GUID приложения службы]TempDB **(\*)**|Пользователь выполняет перенос.|  
|База данных предупреждений|ReportingService_[идентификатор GUID приложения служб]_Alerting|Создается во время создания приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
 **(\*)** Представленные в таблице примеры имен соответствуют соглашению об именовании SSRS, которое используется при создании нового приложения служб SSRS. При выполнении переноса с другого сервера используются имена для каталога и временных баз данных из исходной установки.  
  
####  <a name="bkmk_backup_operations"></a> Операции резервного копирования  
 В данном разделе описываются типы информации, которые необходимы для переноса, и инструменты или процессы, которые используются для резервного копирования.  
  
 ![Базовая диаграмма миграции служб SSRS SharePoint](../../../2014/sql-server/install/media/rs-sharepoint-migration.gif "Базовая диаграмма миграции служб SSRS SharePoint")  
  
||Объекты|Метод|Примечания|  
|-|-------------|------------|-----------|  
|**1**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|**Rskeymgmt.exe** или диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . См. статью [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).|Указанные инструменты можно использовать для резервного копирования. Для восстановления используйте страницы управления приложением служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или PowerShell.|  
|**2**|База данных содержимого SharePoint.||Создайте резервную копию базы данных и отсоедините базу данных.<br /><br /> Дополнительные сведения см. в подразделе об обновлении присоединения баз данных в разделе [Определение стратегии обновления до SharePoint 2010 (http://technet.microsoft.com/library/cc263447.aspx)](http://technet.microsoft.com/library/cc263447.aspx).|  
|**3**|База данных SQL Server, которая используется в качестве базы данных каталогов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|Резервное копирование и восстановление баз данных SQL Server<br /><br /> или диспетчер конфигурации служб<br /><br /> Присоединение и отсоединение баз данных SQL Server||  
|**4**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Простая копия файла.|Если выполнена настройка файла, то необходимо скопировать только rsreportserver.config. Пример местоположения файлов по умолчанию: C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting<br /><br /> Rsreportserver.config<br /><br /> Rssvrpolicy.config<br /><br /> Web.config для приложения ASP.NET сервера отчетов.<br /><br /> Machine.config для ASP.NET.|  
  
####  <a name="bkmk_restore_operations"></a> Операции восстановления  
 В данном разделе описываются типы информации, которые необходимы для переноса, и инструменты или процессы, которые используются для восстановления. Инструменты, которые используются для восстановления, могут отличаться от инструментов, используемых при резервном копировании.  
  
 Перед восстановлением необходимо установить и настроить новую ферму SharePoint и службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. Дополнительные сведения об установке из [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] режиме интеграции с SharePoint см. в разделе [SharePoint режим установки служб Reporting Services &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
||Объекты|Метод|Примечания|  
|-|-------------|------------|-----------|  
|**1**|Восстановите базы данных содержимого SharePoint в новую ферму.|Метод «Обновление присоединения базы данных» SharePoint.|Основные шаги:<br /><br /> 1) Восстановите базу данных на новом сервере.<br /><br /> 2) Подключите базу данных содержимого к веб-приложению, указав URL-адрес.<br /><br /> 3) Используйте Get-SPWebapplication для вывода списка всех веб-приложений и URL-адресов.<br /><br /> Дополнительные сведения см. в подразделе об обновлении присоединения баз данных в разделе [Определение стратегии обновления до SharePoint 2010 (http://technet.microsoft.com/library/cc263447.aspx)](http://technet.microsoft.com/library/cc263447.aspx) и [Присоединение баз данных и обновление до SharePoint Server 2010 (http://technet.microsoft.com/library/cc263299.aspx)](http://technet.microsoft.com/library/cc263299.aspx).|  
|**2**|Восстановите базу данных SQL, которая является базой данных каталогов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (ReportServer).|Резервное копирование и восстановление баз данных SQL.<br /><br /> **или диспетчер конфигурации служб**<br /><br /> Присоединение и отсоединение баз данных SQL Server.|При первом использовании базы данных службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] обновляют схему баз данных, которая требуется для работы со средой [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**3**|Создайте новое приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Центр администрирования SharePoint.|При создании нового приложения службы настройте его для использования скопированной базы данных сервера отчетов.<br /><br /> Дополнительные сведения об использовании центра администрирования SharePoint см. в разделе «Шаг 3: создание Reporting Services службы приложения» в [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).<br /><br /> Примеры использования PowerShell см. в разделе «Создание приложения службы Reporting Services с помощью PowerShell» в [Reporting Services SharePoint Service and Service Applications](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md).|  
|**4**|Восстановите файлы конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Простая копия файла.|Пример расположения файлов по умолчанию: C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting\.|  
|**5**|Восстановление [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ключей шифрования.|Восстановите файл с резервной копией ключей с помощью страницы SystemSettings приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .<br /><br /> **или диспетчер конфигурации служб**<br /><br /> PowerShell.|См. раздел "Управление ключами" в статье [Управление служебным приложением SharePoint службы Reporting Services](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).|  
  
#####  <a name="bkmk_additional_configuration"></a> Дополнительная настройка  
 В зависимости от настройки предыдущей среды SharePoint, возможно, потребуется выполнить одну или несколько следующих операций.  
  
1.  Настройте проверку подлинности NTLM для приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Дополнительные сведения см. в статье [Настройка электронной почты для приложения служб Reporting Services (SharePoint 2010 и SharePoint 2013)](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).  
  
##  <a name="bkmk_migrate_from_ctp"></a> Перенос из развертывания SQL Server 2012  
 В ферме из нескольких серверов базы данных содержимого и каталога пользователей обычно размещаются на разных компьютерах. В этом случае необходимо добавить к ферме SharePoint новый сервер с установленными службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , а затем удалить старый сервер. Копировать базы данных не требуется.  
  
### <a name="backup-operations"></a>Операции резервного копирования  
  
1.  Создайте резервную копию ключей шифрования служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  Создайте резервную копию приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в центре администрирования SharePoint (или используйте PowerShell). При этом также создаются резервные копии баз данных приложения в SharePoint См. в разделе [резервного копирования и восстановления SharePoint приложений службы Reporting Services](../../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md)  
  
3.  При наличии учетной записи автоматического выполнения и использовании проверки подлинности Windows запишите учетные данные, чтобы их можно было использовать в процессе восстановления.  
  
4.  Дополнительные сведения см. в разделе [Резервное копирование приложений службы в SharePoint 2013](http://technet.microsoft.com/library/ee428318.aspx).  
  
### <a name="restore-operations"></a>Операции восстановления  
  
1.  Восстановите приложение служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с помощью центра администрирования SharePoint. Также можно использовать PowerShell.  
  
2.  Восстановите ключи шифрования служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
     См. в разделе «Управление ключами» в разделе [управление приложения SharePoint службы Reporting Services](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)  
  
3.  Настройте учетную запись автоматического выполнения и учетные данные Windows для приложения служб.  
  
4.  Дополнительные сведения см. в разделе [Восстановление приложений службы в SharePoint 2013](http://technet.microsoft.com/library/ee428305.aspx).  
  
##  <a name="bkmk_additional_resources"></a> Дополнительные ресурсы  
  
-   [Обновление до SharePoint 2013 (http://technet.microsoft.com/library/ee833948.aspx)](http://technet.microsoft.com/library/ee833948.aspx).  
  
-   [Общие сведения об обновлении до SharePoint 2013 (http://technet.microsoft.com/library/cc262483.aspx)](http://technet.microsoft.com/library/cc262483.aspx).  
  
## <a name="see-also"></a>См. также  
 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
 [Перенос установки служб Reporting Services (собственный режим)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)  
  
  
