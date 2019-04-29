---
title: Использование диспетчера конфигурации служб Reporting Services (собственный режим) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- configuration options [Reporting Services]
- report servers [Reporting Services], configuring
- components [Reporting Services], Reporting Services Configuration tool
ms.assetid: 379eab68-7f13-4997-8d64-38810240756e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 285170d1860d7ba19102e2476758ed951bfe06c4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057592"
---
# <a name="reporting-services-configuration-manager-native-mode"></a>Использование диспетчера конфигурации служб Reporting Services (собственный режим)
  Используйте диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для настройки установленных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме. Если сервер отчетов был установлен в режиме «только файлы», то перед использованием сервера необходимо воспользоваться диспетчером конфигурации. Если сервер отчетов устанавливался в режиме по умолчанию, используйте диспетчер настройки для проверки или изменения настроек, заданных во время установки. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] может использоваться для настройки экземпляра локального или удаленного сервера отчетов.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме.  
  
> [!NOTE]  
>  Начиная с выпуска [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не предназначен для управления серверами отчетов, работающими в режиме интеграции с SharePoint. Управление и настройка режима интеграции с SharePoint осуществляются с использованием центра администрирования SharePoint и скриптов PowerShell. Сведения см. в разделе [SharePoint режим установки служб Reporting Services &#40;SharePoint 2010 и SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
 **В этом разделе:**  
  
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
 Содержит рекомендации, описывает шаги для изменения учетной записи службы и пароля.  
  
 [Настройка URL-адресов сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
 Описание способов настройки URL-адресов, используемых для обращения к веб-службе сервера отчетов и к диспетчеру отчетов.  
  
 [Создание базы данных сервера отчетов (диспетчер конфигурации служб SSRS)](../../../2014/sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
 Описывает, как создать базу данных сервера отчетов, необходимую для хранения метаданных и объектов сервера.  
  
 [Настройка подключения к базе данных сервера отчетов (диспетчер конфигураций служб Reporting Services)](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
 Описывает, как изменить строку, используемую сервером отчетов для подключения к базе данных сервера отчетов.  
  
 [Настройка учетной записи автоматического выполнения (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
 Описывает, как настроить пользовательскую учетную запись для обработки отчетов в автоматическом режиме.  
  
 [Настройка сервера отчетов для доставки электронной почты &#40;диспетчер конфигурации служб SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
 Описывает, как настроить сервер отчетов для поддержки рассылки отчетов по электронной почте.  
  
 [Настройка масштабного развертывания сервера отчетов в основном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
 Содержит сведения о настройке нескольких экземпляров сервера отчетов для использования общей базы данных сервера отчетов.  
  
 [Настройка ключей шифрования и управление ими (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
 Объясняет, как пользоваться и управлять ключами шифрования, используемыми при сохранении конфиденциальных данных.  
  
 [Управление сервером отчетов Reporting Services в собственном режиме](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
 Предоставляет пошаговую инструкцию по выполнению типичных задач.  
  
 [Разделы справки F1 диспетчера конфигурации служб Reporting Services &#40;собственный режим служб SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
 Содержит разделы справки по страницам в программе настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 **В этом разделе:**  
  
-   [Сценарии использования диспетчера конфигурации Reporting Services](#bkmk_scenarios)  
  
-   [Требования](#bkmk_requirements)  
  
-   [Чтобы запустить диспетчер конфигурации служб Reporting Services](#bkmk_start_configuration_manager)  
  
##  <a name="bkmk_scenarios"></a> Сценарии использования диспетчера конфигурации служб Reporting Services  
 С помощью программы настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно выполнять следующие задачи.  
  
-   Настройка учетной записи службы сервера отчетов. Учетная запись службы сервера отчетов изначально настраивается в процессе установки, но может быть изменена с помощью программы настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , если требуется обновить пароль или использовать другую учетную запись.  
  
-   Создание и настройка URL-адресов. Сервер отчетов и диспетчер отчетов являются приложениями [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] , доступ к которым осуществляется через URL-адреса. URL-адрес сервера отчетов обеспечивает доступ к конечным точкам SOAP сервера отчетов. URL-адрес диспетчера отчетов используется для запуска диспетчера отчетов. Для каждого приложения можно настроить один или несколько URL-адресов.  
  
-   Создание и настройка базы данных сервера отчетов. Сервер отчетов представляет собой сервер без сохранения состояния, которому необходима база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве внутреннего хранилища. Программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно использовать для создания базы данных сервера отчетов и настройки соединения с сервером отчетов. Можно также выбрать существующую базу данных сервера отчетов, содержащую нужные данные.  
  
-   Настройка масштабного развертывания в собственном режиме. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживают топологию развертывания, которая позволяет всем экземплярам сервера отчетов использовать одну и ту же общую базу данных сервера отчетов. В случае масштабного развертывания сервера отчетов используйте программу настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , чтобы подключить каждый сервер отчетов к общей базе данных сервера отчетов.  
  
-   Резервное копирование, восстановление или замена симметричного ключа, используемого для шифрования хранимых строк соединения и учетных данных. Если изменяется учетная запись службы или база данных сервера отчетов перемещается на другой компьютер, необходимо иметь резервную копию симметричного ключа.  
  
-   Настройка учетной записи автоматического выполнения. Эта учетная запись используется для удаленных соединений при запланированных операциях или в случае, если недоступны учетные данные пользователя.  
  
-   Настройка электронной почты сервера отчетов. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] включают модуль доставки электронной почты сервера отчетов, в котором для доставки отчетов или уведомлений об обработке отчетов по электронной почте используется протокол SMTP. С помощью диспетчера конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно указать SMTP-сервер или сетевой шлюз, который используется для доставки электронной почты.  
  
 Программа настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не предназначена для управления содержимым сервера отчетов, включения дополнительных компонентов или предоставления доступа к серверу. Для полного развертывания также необходимо в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] включить дополнительные компоненты или изменить значения по умолчанию, а также диспетчер отчетов, чтобы предоставить пользователю доступ к серверу.  
  
##  <a name="bkmk_requirements"></a> Требования  
 Диспетчер конфигурации работает только с конкретной версией служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который устанавливается вместе с этой версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не может применяться для настройки более ранней версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Если на одном компьютере работает нескольких версий служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , для настройки каждого экземпляра должен использоваться диспетчер конфигурации служб Reporting Services, который поставляется с соответствующей версией.  
  
 Для использования диспетчера настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] необходимо иметь следующее.  
  
-   Разрешения локального системного администратора на компьютере, размещающем сервер отчетов, который нужно настроить. Для настройки удаленного компьютера необходимы также разрешения администратора локальной системы на этом компьютере.  
  
-   Разрешение на создание баз данных в компоненте [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , размещающем базу данных сервера отчетов.  
  
-   На каждом настраиваемом сервере отчетов должна быть включена и запущена служба инструментария управления Windows (WMI). Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] производит подключение к локальным и удаленным серверам отчетов через поставщик WMI сервера отчетов. Если настраивается удаленный сервер отчетов, на компьютере должен быть разрешен удаленный доступ к инструментарию WMI. Дополнительные сведения о подготовке сервера отчетов для удаленного администрирования см. в разделе [Настройка сервера отчетов для удаленного администрирования](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md).  
  
-   Перед подключением к удаленному экземпляру сервера отчетов для его настройки необходимо обеспечить пропускание удаленных вызовов инструментария управления Windows (WMI) через брандмауэр Windows. Дополнительные сведения см. в разделе [Настройка сервера отчетов для удаленного администрирования](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 URL-адрес [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] устанавливается автоматически при установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
##  <a name="bkmk_start_configuration_manager"></a> Запуск диспетчера конфигурации служб Reporting Services  
  
#### <a name="to-start-reporting-services-configuration"></a>Запуск программы настройки служб Reporting Services  
  
1.  Следующий шаг должен соответствовать версии ОС Microsoft Windows.  
  
    -   На стартовом экране Windows введите **Отчеты** и в результатах поиска выберите **Диспетчер конфигурации служб Reporting Services** .  
  
    -   Нажмите кнопку **Пуск**, выберите **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], а затем **Средства настройки**.  
  
         Если необходимо настроить экземпляр сервера отчетов предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], откройте соответствующую ей папку установки. Например, укажите [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] вместо [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] , чтобы открыть средства настройки для компонентов сервера [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .  
  
         Выберите **Диспетчер конфигурации служб Reporting Services**.  
  
2.  Появится диалоговое окно **Подключение для конфигурации служб Reporting Services** , в котором можно выбрать настраиваемый экземпляр сервера отчетов. Нажмите кнопку **Соединить**.  
  
3.  В поле **Имя сервера**укажите имя компьютера, на котором установлен экземпляр сервера отчетов. По умолчанию это поле содержит имя локального компьютера, но если необходимо подключиться к серверу отчетов, установленному на другом компьютере, в него можно ввести имя удаленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  Если указан удаленный компьютер, для установления соединения нажмите кнопку **Найти** .  
  
5.  В списке **Report Server В спискеstance**выберите экземпляр служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , который необходимо настроить. В списке отображаются только экземпляры сервера отчетов для данной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Более ранние версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]настраивать нельзя.  
  
6.  Нажмите кнопку **Соединить**.  
  
## <a name="see-also"></a>См. также  
 [Диспетчер отчетов (службы Reporting Services в основном режиме)](../../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Инструментальные средства служб Reporting Services](../../reporting-services/tools/reporting-services-tools.md)   
 [Настройка подключения к базе данных сервера отчетов (диспетчер конфигураций служб Reporting Services)](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Диспетчер конфигурации SQL Server](../../relational-databases/sql-server-configuration-manager.md)   
 [Настройка и администрирование сервера отчетов (службы Reporting Services в собственном режиме)](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
