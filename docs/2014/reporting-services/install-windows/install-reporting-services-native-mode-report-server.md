---
title: Установка сервера отчетов служб сервера отчетов в собственном режиме | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- report servers [Reporting Services], default configurations
- installation options [Reporting Services]
ms.assetid: 8f25e6dc-b753-400e-9e9a-50f4f35bf6c4
caps.latest.revision: 58
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0260982df5dff6640a4a273916c8e4455bd18621
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37329444"
---
# <a name="install-reporting-services-native-mode-report-server"></a>Установка сервера отчетов служб Reporting Services в собственном режиме
  Работающий в собственном режиме сервер отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно установить при помощи мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или из командной строки. В мастере установки можно выбрать либо 1) установку файлов и настройку сервера на параметры по умолчанию, либо 2) только установку файлов без настройки сервера мастером установки. В этом разделе описывается *конфигурация по умолчанию для собственного режима* , при которой программа установки устанавливает и настраивает экземпляр сервера отчетов. После завершения программы установки сервер отчетов будет запущен и готов к работе. Сервер отчетов, работающий в собственном режиме, запускается в качестве изолированного сервера приложений. Собственный режим является режимом сервера по умолчанию.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме|  
  
##  <a name="bkmk_top"></a> В этом разделе  
  
-   [Что такое конфигурация по умолчанию?](#bkmk_whatisdefaultconfiguration)  
  
-   [Когда следует установить конфигурацию по умолчанию для основного режима](#bkmk_whentoinstalldefaultconfig)  
  
-   [Требования](#bkmk_requirements)  
  
-   [Резервирование URL-адресов по умолчанию](#bkmk_defaultURLreservations)  
  
-   [Установка в собственном режиме с помощью мастера установки SQL Server](#bkmk_installwithwizard)  
  
-   [Установка в собственном режиме с помощью командной строки](#bkmk_commandline)  
  
##  <a name="bkmk_whatisdefaultconfiguration"></a> Что такое конфигурация по умолчанию?  
 При выборе конфигурации по умолчанию для собственного режима программой установки устанавливаются следующие компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
-   Служба сервера отчетов (в состав которой входит веб-служба сервера отчетов, приложение фоновой обработки и диспетчер отчетов)  
  
-   Диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   Программы командной строки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (rsconfig.exe, rskeymgmt.exe и rs.exe)  
  
 Этот параметр не затрагивает такие как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] или [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], которые должны быть выбраны как отдельные элементы, если вы хотите установить их.  
  
 В процессе установки сервера отчетов, работающего в собственном режиме, программой установки настраиваются следующие параметры.  
  
-   Учетная запись службы для службы сервера отчетов.  
  
-   URL-адрес веб-службы сервера отчетов.  
  
-   URL-адрес диспетчера отчетов.  
  
-   База данных сервера отчетов.  
  
-   Доступ учетной записи службы к базам данных сервера отчетов.  
  
-   DSN-соединение с базами данных сервера отчетов.  
  
 Программа установки не производит настройку учетной записи автоматического выполнения, электронной почты сервера отчетов, резервного копирования ключей шифрования и масштабного развертывания. Для настройки этих свойств вы можете использовать диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
##  <a name="bkmk_whentoinstalldefaultconfig"></a> Когда следует установить конфигурацию по умолчанию для основного режима  
 При конфигурации по умолчанию службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] устанавливаются в рабочее состояние, и сервер отчетов можно использовать сразу после завершения программы установки. Выберите этот режим, чтобы сократить количество шагов и пропустить выполнение задач настройки, которые в противном случае пришлось бы выполнять в средстве настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Установка конфигурации по умолчанию не гарантирует, что сервер отчетов будет работать после завершения программы установки. Регистрация URL-адресов по умолчанию может завершиться ошибкой при запуске службы. Всегда тестируйте установку, чтобы убедиться, что служба запускается и выполняется правильно.  
  
##  <a name="bkmk_requirements"></a> Требования  
 Этот режим настройки для задания основных параметров, необходимых для приведения сервера отчетов в рабочее состояние, использует параметры конфигурации по умолчанию. К нему предъявляются следующие требования.  
  
-   Оборудование должно соответствовать минимальным требованиям для работы Microsoft SQL Server. Дополнительные сведения см. в разделе [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] должны устанавливаться на одном и том же экземпляре. Экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] размещает базу данных сервера отчетов, которую создает и настраивает программа установки.  
  
-   Учетная запись пользователя, использованная для выполнения программы установки, должна быть членом локальной группы администраторов. Кроме того, она должна обладать разрешениями для доступа и создания баз данных в экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором размещены базы данных сервера отчетов.  
  
-   Программа установки должна иметь возможность использовать значения по умолчанию, чтобы резервировать URL-адреса, которые обеспечивают доступ к серверу и диспетчеру отчетов. Этими значениями являются порт 80, строгий подстановочный знак и имена виртуальных каталогов в формате **ReportServer_\<***имя_экземпляра***>** и **Reports_\<***имя_экземпляра***>**.  
  
-   Программа установки должна иметь возможность создания баз данных сервера отчетов с использованием значений по умолчанию. Это значения **ReportServer** и **ReportServerTempDB**. Если от предыдущей установки остались базы данных, то программа установки будет заблокирована, поскольку она не сможет настроить сервер отчетов в конфигурации по умолчанию для собственного режима. Чтобы снять блокировку программы установки, следует переименовать, переместить или удалить базы данных.  
  
 Если компьютер не отвечает всем требованиям для установки по умолчанию, нужно установить службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме «только файлы», а после установки настроить компьютер с помощью диспетчера настройки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Не пытайтесь изменить настройки компьютера только для продолжения установки по умолчанию. Это может потребовать несколько часов работы, тогда как этот параметр установки может значительно сэкономить время. Наилучшим решением является установка [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме только для файлов и настройте сервер отчетов для использования определенных значений.  
  
##  <a name="bkmk_defaultURLreservations"></a> Резервирование URL-адресов по умолчанию  
 Резервирование URL-адреса состоит из префикса, имени узла, номера порта и имени виртуального каталога.  
  
|Часть|Описание|  
|----------|-----------------|  
|Prefix|Префиксом по умолчанию является HTTP. Если сертификат SSL уже установлен, программа установки попытается создать резервирование URL-адресов с префиксом HTTPS.|  
|Имя узла|Именем узла по умолчанию является строгий шаблон (+). Он указывает, что сервер отчетов принимает все HTTP-запросы по заданному порту для любого имени узла, который соответствует компьютеру, включая http://\<имя_компьютера > / reportserver, http://localhost/reportserver, или http://\<IP-адрес > / ReportServer.|  
|Порт|По умолчанию используется порт 80. Следует иметь в виду, что если используется порт, отличный от 80, то его необходимо явным образом указывать в URL-адресе при открытии веб-приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в окне браузера.|  
|Виртуальный каталог|По умолчанию имена виртуальных каталогов создаются в формате ReportServer_\<*имя_экземпляра*> для сервера веб-службы отчетов и по модели Reports_\<*имя_экземпляра*> для диспетчера отчетов. Для веб-службы сервера отчетов по умолчанию используется виртуальный каталог **reportserver**. Для диспетчера отчетов используется виртуальный каталог по умолчанию **reports**.|  
  
 Ниже приведен пример полного URL-адреса.  
  
-   http://+:80/reportserver, предоставляет доступ к серверу отчетов.  
  
-   http://+:80/reports, предоставляет доступ к диспетчеру отчетов.  
  
##  <a name="bkmk_installwithwizard"></a> Установка в собственном режиме с помощью мастера установки SQL Server  
 В следующем списке описываются конкретные шаги и параметры служб  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , выбираемые в мастере установки SQL Server. В этом списке описаны не все страницы мастера установки, а только страницы, связанные со службами [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которые являются частью установки в собственном режиме.  
  
1.  На странице **Роль установки** выберите **Установка компонентов SQL Server**.  
  
     ![Установка компонентов SQL Server для роли установки](../../../2014/sql-server/install/media/rs-setuprole.gif "Установка компонентов SQL Server для роли установки")  
  
2.  Выберите следующие компоненты на странице **Выбор компонентов** :  
  
    -   **Службы компонента Database Engine**, если еще не установлен компонент database engine.  
  
    -   **Reporting Services собственный**.  
  
    -   **Средства управления — базовые**. Средства управления не являются обязательными, однако их установка рекомендуется в том случае, если вы не используете какие-либо другие средства управления. Параметр настройки по умолчанию приведет к установке функционального сервера отчетов, однако позднее может потребоваться изменить параметры. Некоторые параметры, такие как «Мои отчеты», управляются через [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
     ![Выбор служб SSRS в собственном режиме в выборе компонентов](../../../2014/sql-server/install/media/rs-setupfeatureselection-native-withcircles.gif "Выбор служб SSRS в собственном режиме в выборе компонентов")  
  
3.  Если вы планируете использовать [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] функцию подписки, то на **конфигурации сервера** страницы, необходимо проверить агента SQL Server настроен для **автоматического** тип запуска.  
  
4.  На странице **Конфигурация служб Reporting Services** выберите **Установка и настройка**.  
  
     ![Настройка служб SSRS в собственном режиме](../../../2014/sql-server/install/media/rs-setupconfiguration-native-with-circles.gif "Настройка служб SSRS в собственном режиме")  
  
5.  После завершения мастера установки SQL Server проверьте установку собственного режима по умолчанию, используя следующие основные шаги.  
  
    -   Откройте диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и убедитесь, что вы можете подключиться к серверу отчетов.  
  
    -   Откройте браузер с правами администратора и подключитесь к диспетчеру отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], например `http://loclahost/Reports`.  
  
    -   Откройте браузер с правами администратора и подключитесь к странице сервера отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Например  `http://loclahost/ReportServer`  
  
 Дополнительные сведения см. в подразделе «Собственный режим» следующих двух разделов:  
  
 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)  
  
 [Устранение неполадок при установке служб Reporting Services](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)  
  
##  <a name="bkmk_commandline"></a> Установка в собственном режиме с помощью командной строки  
 Следующий пример использует службу компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], поскольку это необходимо для конфигурации по умолчанию.  
  
```  
setup /q /ACTION=install /FEATURES=SQL,RS,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS"   
/RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK   
SERVICE" /RSSVCSTARTUPTYPE="Manual" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
 Дополнительные сведения и примеры см. в разделе [командной строки установки из Reporting Services в режиме SharePoint и собственного режима](../../reporting-services/install-windows/install-reporting-services-at-the-command-prompt.md) и [Установка SQL Server 2014 из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок при установке служб Reporting Services](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
 [Проверка установки служб Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Настройка URL-адресов сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Настройка подключения к базе данных сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Установка в режиме "только файлы" (службы Reporting Services)](../../reporting-services/install-windows/files-only-installation-reporting-services.md)   
 [Инициализация сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Настройка соединений SSL для сервера отчетов в собственном режиме](../security/configure-ssl-connections-on-a-native-mode-report-server.md)   
 [Настройка URL-адресов сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [Быстрая установка SQL Server 2014](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
