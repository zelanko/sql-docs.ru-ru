---
title: "Обновление базы данных сервера отчетов | Документы Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading databases
- report server database
- upgrading Reporting Services
ms.assetid: 4091cf87-9d97-4048-a393-67f1f9207401
caps.latest.revision: 44
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 89bb5de5f669d033dd18bc63e11ef5bd29644542
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---

# <a name="upgrade-a-report-server-database"></a>Обновление базы данных сервера отчетов

База данных сервера отчетов обеспечивает хранение одного или нескольких экземпляров сервера отчетов. Схема базы данных сервера отчетов с каждым новым выпуском служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]может меняться, поэтому версия базы данных должна совпадать с версией используемого экземпляра сервера отчетов. В большинстве случаев обновление базы данных сервера отчетов может быть выполнено автоматически, без необходимости выполнения каких-либо действий со стороны пользователя.  
  
 **Собственный режим.** В собственном режиме [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] база данных сервера отчетов на самом деле состоит из двух баз данных с именами по умолчанию ReportServer и ReportServerTempDB.  
  
 **Режиме интеграции с SharePoint:** в режиме SQL Server 2016 Reporting Services SharePoint сервера отчетов базы данных является фактически является коллекцией баз данных, который создается для каждого экземпляра [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] приложения службы.  

## <a name="ways-to-upgrade-a-native-mode-report-server-database"></a>Способы обновления базы данных сервера отчетов в собственном режиме

 В следующем списке приведены условия, при соблюдении которых происходит обновление базы данных сервера отчетов.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Программа установки обновит одиночный экземпляр сервера отчетов. Схема базы данных сервера отчетов будет автоматически обновлена, после того как служба запустится и сервер отчетов определит, что версия схемы базы данных не совпадает с версией сервера.  
  
     При запуске службы сервер отчетов проверяет версию схемы базы данных, чтобы определить, соответствует ли она версии сервера. Если у схемы базы данных более старая версия, то она будет автоматически обновлена до версии, необходимой серверу отчетов. Функция автоматического обновления особенно полезна при восстановлении из резервной копии или подключении старой базы данных сервера отчетов. В файл журнала трассировки сервера отчетов выводится сообщение об обновлении версии схемы базы данных.  
  
-   Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] обновляет локальную или удаленную базу данных сервера отчетов, если для использования с более новым экземпляром сервера отчетов выбрана предыдущая версия. В этом случае необходимо подтвердить выполнение обновления, прежде чем оно будет осуществлено.  
  
     В диспетчере конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] больше нет отдельной кнопки «Обновить» и скрипта обновления. Эти средства устарели, начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , в связи с появлением в службе сервера отчетов функции автоматического обновления.  
  
 После обновления схемы откат до предыдущей версии становится невозможным. Чтобы иметь возможность повторно создать предыдущую установку, всегда создавайте резервную копию базы данных сервера отчетов.  
  
## <a name="how-the-schema-metadata-and-report-server-content-is-updated"></a>Обновление схемы, метаданных и содержимого сервера отчетов  
 База данных сервера отчетов обновляется в три этапа.  
  
1.  Схема обновляется автоматически после установки и запуска службы или же после выбора базы данных сервера отчетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в собственном режиме в диспетчере конфигурации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который имеет более старую версию. Кроме этого, служба сервера отчетов осуществляет проверку версии базы данных во время запуска. Если сервер отчетов соединяется с базой данных предыдущей версии, то он обновляет ее во время своего запуска.  
  
2.  Дескрипторы безопасности обновляются при первом использовании базы данных сервера отчетов после обновления схемы.  
  
3.  Опубликованные отчеты и скомпилированные моментальные снимки отчетов обновляются при первом использовании. Дополнительные сведения см. в разделе [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md).  
  
 Кроме базы данных сервера отчетов при работе сервера отчетов используется временная база данных. Она обновляется автоматически при обновлении базы данных сервера отчетов.  
  
## <a name="permissions-required-to-upgrade-a-report-server-database"></a>Разрешения, необходимые для обновления базы данных сервера отчетов  
 При обновлении установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , включающем базу данных сервера отчетов, может появиться сообщение об ошибке, если обновление базы данных выполняется с недостаточными разрешениями. По умолчанию программа установки для соединения с удаленным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и обновления схемы пользуется токеном безопасности пользователя, запустившего программу установки. База данных будет обновлена, если у пользователя есть разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sysadmin** на доступ к серверу базы данных с расположенными базами данных сервера отчетов. Аналогичным образом при запуске программы установки из командной строки с указанием аргументов RSUPGRADEDATABASEACCOUNT и RSUPGRADEPASSWORD с учетными данными, обладающими разрешением **sysadmin** на изменение схемы на удаленном компьютере, обновление данных также произойдет успешно.  
  
 Однако, если разрешение **sysadmin** на изменение схемы на удаленном компьютере отсутствуют, в соединении будет отказано со следующей ошибкой.  
  
 `"Setup was not able to upgrade the report server database schema. You must update the database schema manually after setup is finished. To update the schema, run the Reporting Services Configuration Manager, open the Database Setup page, re-select the database, and click Apply. The database will be upgraded automatically."`  
  
 В этот момент произойдет обновление программных файлов сервера отчетов, однако версия формата базы данных сервера отчетов останется прежней. Сервер отчетов будет недоступен до тех пор, пока процесс обновления не будет завершен (для этого базу данных необходимо обновить вручную).  
  
#### <a name="to-upgrade-a-native-mode-database-with-scripts"></a>Обновление базы данных в собственном режиме с помощью скриптов  
 Для обновления базы данных сервера отчетов можно использовать скрипты WMI. Дополнительные сведения см. в статье [Метод GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting)](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-generatedatabaseupgradescript.md).  
  
## <a name="next-steps"></a>Следующие шаги

[Диспетчер конфигурации служб Reporting Services](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
[Создать базу данных сервера отчетов](../../reporting-services/install-windows/ssrs-report-server-create-a-report-server-database.md)   
[Мастер изменения базы данных](http://msdn.microsoft.com/library/1a2e8d18-5997-482f-a9c1-87d99f7407b8)   
[Обновление и перенос служб Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
[Перенос установки служб Reporting Services](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
