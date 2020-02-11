---
title: Перенос установки служб Reporting Services (режим интеграции с SharePoint) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 61290949-690a-4e19-b078-57c99b6b30fa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1f23dad22e1d748f39b1dd390b5874806193276
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75253193"
---
# <a name="migrate-a-reporting-services-installation-sharepoint-mode"></a>Перенос установки служб Reporting Services (режим интеграции с SharePoint)
  В этом разделе дается обзор шагов, необходимых для миграции развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint из одной среды SharePoint в другую. Конкретные шаги могут различаться в зависимости от версии, с которой выполняется перенос. Дополнительные сведения о сценариях обновления и переноса в режиме интеграции с SharePoint см. в разделе [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md). Если вы хотите скопировать элементы отчета с одного сервера на другой, см. раздел [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
 Сведения о миграции развертывания служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , работающих в собственном режиме, см. в статье [Перенос установки служб Reporting Services (собственный режим)](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010 и SharePoint 2013|  
  
 Обычная причина выполнения миграции — обновление развертывания SharePoint 2010 до SharePoint 2013. SharePoint 2013 не поддерживает обновление на месте с SharePoint 2010, поэтому необходимо выполнить процедуру **обновления присоединения базы данных** или перенести только содержимое.  
  
 Дополнительные сведения об обновлении SharePoint 2013 см. в следующих материалах:  
  
-   [Обзор процесса обновления до SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Обновите базы данных с sharepoint 2010 на sharepoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
-   [Перемещение баз данных содержимого в SharePoint 2013](https://technet.microsoft.com/library/cc262792.aspx).  
  
 
  
##  <a name="bkmk_prior_versions"></a>Миграция из Reporting Services версий в режиме интеграции с SharePoint до SQL Server 2012  
 Архитектура служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint изменилась в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], включая схему базы данных приложения службы. [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] Если вы хотите перейти в режим интеграции с SharePoint из версии [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], более ранней, создайте новую среду SharePoint, установив SharePoint и [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Mode. Дополнительные сведения см. в разделе [Reporting Services SharePoint Mode установка &#40;sharepoint 2010 и sharepoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
 Как только новая среда SharePoint будет запущена, можно выбрать между переносом только содержимого и полным переносом на уровне баз данных, включая базы данных содержимого.  
  
###  <a name="bkmk_content_only_migration"></a>Перенос только содержимого  
 **Reporting Services перенос только содержимого:** Если вы хотите скопировать [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] содержимое в новую ферму, необходимо использовать такие средства, как **RS. exe** , для копирования содержимого в новую установку SharePoint. Дополнительные сведения о переносах только содержимого см. в следующих материалах:  
  
-   ** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Сценарии RSS:** Скрипты могут переносить содержимое и ресурсы между сервером отчетов в собственном режиме и в режиме интеграции с SharePoint. Дополнительные сведения см. в разделе [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md) и [Скрипт RS.exe служб Reporting Services, который переносит содержимое с одного сервера отчетов на другой](https://azuresql.codeplex.com/releases/view/115207).  
  
-   **Средство миграции Reporting Services:** Средство может копировать элементы отчета с сервера в собственном режиме на сервер в режиме интеграции с SharePoint. Дополнительные сведения см. в разделе [средство миграции служб Reporting Services](https://www.microsoft.com/download/details.aspx?id=29560).  
  
###  <a name="bkmk_full_migration"></a>Полная миграция  
 **Полная миграция:** При переносе баз данных содержимого SharePoint вместе с базами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] данных каталога в новую ферму можно выполнить ряд параметров резервного копирования и восстановления, приведенных в этом разделе. В некоторых случаях на этапе восстановления необходимо использовать инструменты, отличные от инструментов, которые использовались при резервном копировании. Например, можно [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] использовать Configuration Manager для резервного копирования ключей шифрования из предыдущей версии, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] но для восстановления ключей шифрования в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] установку в режиме интеграции с SharePoint необходимо использовать центр администрирования SharePoint или PowerShell.  
  
####  <a name="bkmk_databases"></a>Базы данных, которые будут отображаться в завершенной миграции  
 В следующей таблице описаны базы данных SQL Server, которые связаны с [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и доступны после успешного переноса установки SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
|База данных|Пример имени||  
|--------------|------------------|-|  
|База данных каталогов|ReportingService_ [идентификатор GUID приложения службы **]\*()**|Пользователь выполняет перенос.|  
|Временная база данных|ReportingService_ [GUID приложения службы] TempDB **(\*)**|Пользователь выполняет перенос.|  
|База данных предупреждений|ReportingService_[идентификатор GUID приложения служб]_Alerting|Создается во время создания приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
  
 **(\*)** Имена примеров, приведенные в таблице, соответствуют соглашению об именовании, используемому службами SSRS при создании нового приложения службы SSRS. При выполнении переноса с другого сервера используются имена для каталога и временных баз данных из исходной установки.  
  
####  <a name="bkmk_backup_operations"></a>Операции резервного копирования  
 В данном разделе описываются типы информации, которые необходимы для переноса, и инструменты или процессы, которые используются для резервного копирования.  
  
 ![Базовая диаграмма миграции служб SSRS SharePoint](../../../2014/sql-server/install/media/rs-sharepoint-migration.gif "Базовая диаграмма миграции служб SSRS SharePoint")  
  
||Объекты|Метод|Заметки|  
|-|-------------|------------|-----------|  
|**1**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ключи шифрования.|**Rskeymgmt. exe** или [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. См. статью [Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).|Указанные инструменты можно использовать для резервного копирования. Для восстановления используйте страницы управления приложением служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или PowerShell.|  
|**2**|База данных содержимого SharePoint.||Создайте резервную копию базы данных и отсоедините базу данных.<br /><br /> Дополнительные сведения см. в разделе об обновлении присоединения баз данных в статье [Определение стратегии обновления до SharePoint 2010 (https://technet.microsoft.com/library/cc263447.aspx)](https://technet.microsoft.com/library/cc263447.aspx)).|  
|**3-5**|База данных SQL Server, которая используется в качестве базы данных каталогов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|Резервное копирование и восстановление баз данных SQL Server<br /><br /> или диспетчер конфигурации служб<br /><br /> Присоединение и отсоединение баз данных SQL Server||  
|**4**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]файлы конфигурации.|Простая копия файла.|Если выполнена настройка файла, то необходимо скопировать только rsreportserver.config. Пример местоположения файлов по умолчанию: C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting<br /><br /> RSReportServer.config<br /><br /> Rssvrpolicy.config<br /><br /> Web.config для приложения ASP.NET сервера отчетов.<br /><br /> Machine.config для ASP.NET.|  
  
####  <a name="bkmk_restore_operations"></a>Операции восстановления  
 В данном разделе описываются типы информации, которые необходимы для переноса, и инструменты или процессы, которые используются для восстановления. Инструменты, которые используются для восстановления, могут отличаться от инструментов, используемых при резервном копировании.  
  
 Перед восстановлением необходимо установить и настроить новую ферму SharePoint и службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. Дополнительные сведения об базовой установке режима интеграции с [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint см. в статьях Reporting Services установки в режиме интеграции с SharePoint [&#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
||Объекты|Метод|Заметки|  
|-|-------------|------------|-----------|  
|**1**|Восстановите базы данных содержимого SharePoint в новую ферму.|Метод "Обновление присоединения базы данных" SharePoint.|Основные шаги:<br /><br /> 1) Восстановите базу данных на новом сервере.<br /><br /> 2) Подключите базу данных содержимого к веб-приложению, указав URL-адрес.<br /><br /> 3) Используйте Get-SPWebapplication для вывода списка всех веб-приложений и URL-адресов.<br /><br /> Дополнительные сведения см. в разделе об обновлении присоединения баз данных в статьях [Определение стратегии обновления до SharePoint 2010 (https://technet.microsoft.com/library/cc263447.aspx)](https://technet.microsoft.com/library/cc263447.aspx)) и [Присоединение баз данных и обновление до SharePoint Server 2010 (https://technet.microsoft.com/library/cc263299.aspx)](https://technet.microsoft.com/library/cc263299.aspx)).|  
|**2**|Восстановите базу данных SQL, которая является базой данных каталогов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (ReportServer).|Резервное копирование и восстановление баз данных SQL.<br /><br /> **ни**<br /><br /> Присоединение и отсоединение баз данных SQL Server.|При первом использовании базы данных службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] обновляют схему баз данных, которая требуется для работы со средой [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .|  
|**3-5**|Создайте новое приложение службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Центр администрирования SharePoint.|При создании нового приложения службы настройте его для использования скопированной базы данных сервера отчетов.<br /><br /> Дополнительные сведения об использовании центра администрирования SharePoint см. в подразделе "шаг 3. Создание приложения службы Reporting Services" статьи [установка Reporting Services SharePoint для sharepoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).<br /><br /> Примеры использования PowerShell см. в разделе "Создание приложения службы Reporting Services с помощью PowerShell" в статье [Служба и приложения службы Reporting Services в SharePoint](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md).|  
|**4**|Восстановите файлы конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Простая копия файла.|Пример расположения файлов по умолчанию: C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting\.|  
|**5.0**|Восстановите ключи шифрования служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|Восстановите файл с резервной копией ключей с помощью страницы SystemSettings приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].<br /><br /> **ни**<br /><br /> PowerShell.|См. раздел "Управление ключами" в статье [Управление приложением службы Reporting Services в SharePoint](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).|  
  
#####  <a name="bkmk_additional_configuration"></a>Дополнительная настройка  
 В зависимости от настройки предыдущей среды SharePoint, возможно, потребуется выполнить одну или несколько следующих операций.  
  
1.  Настройте проверку подлинности NTLM для приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Дополнительные сведения см. в статье [Настройка электронной почты для приложения служб Reporting Services (SharePoint 2010 и SharePoint 2013)](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).  
  
##  <a name="bkmk_migrate_from_ctp"></a>Миграция из развертывания SQL Server 2012  
 В ферме из нескольких серверов базы данных содержимого и каталога пользователей обычно размещаются на разных компьютерах. В этом случае необходимо добавить к ферме SharePoint новый сервер с установленными службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , а затем удалить старый сервер. Копировать базы данных не требуется.  
  
### <a name="backup-operations"></a>Операции резервного копирования  
  
1.  Создайте резервную копию ключей шифрования служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  Создайте резервную копию приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в центре администрирования SharePoint (или используйте PowerShell). При этом также создаются резервные копии баз данных приложения в SharePoint Дополнительные сведения см. в статье  [Резервное копирование и восстановление служебного приложения SharePoint службы Reporting Services](../../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md).  
  
3.  При наличии учетной записи автоматического выполнения и использовании проверки подлинности Windows запишите учетные данные, чтобы их можно было использовать в процессе восстановления.  
  
4.  Дополнительные сведения см. в разделе [Резервное копирование приложений службы в SharePoint 2013](https://technet.microsoft.com/library/ee428318.aspx).  
  
### <a name="restore-operations"></a>Операции восстановления  
  
1.  Восстановите приложение служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с помощью центра администрирования SharePoint. Также можно использовать PowerShell.  
  
2.  Восстановите ключи шифрования служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
     См. раздел "Управление ключами" раздела [Управление приложением службы Reporting Services SharePoint](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md) .  
  
3.  Настройте учетную запись автоматического выполнения и учетные данные Windows для приложения служб.  
  
4.  Дополнительные сведения см. в разделе [Восстановление приложений службы в SharePoint 2013](https://technet.microsoft.com/library/ee428305.aspx).  
  
##  <a name="bkmk_additional_resources"></a>Дополнительные ресурсы  
  
-   [Начало работы с обновлениями до SharePoint 2013https://technet.microsoft.com/library/ee833948.aspx)(](https://technet.microsoft.com/library/ee833948.aspx).  
  
-   [Общие сведения о процессе обновления до SharePoint 2013 (https://technet.microsoft.com/library/cc262483.aspx)](https://technet.microsoft.com/library/cc262483.aspx).  
  
## <a name="see-also"></a>См. также:  
 [Обновление и миграция Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
 [Миграция Reporting Services установки &#40;основном режиме&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)  
  
