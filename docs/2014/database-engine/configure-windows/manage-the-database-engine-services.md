---
title: Управление службами компонента Database Engine | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, accessing
- Database Engine [SQL Server], services
- managing services [SQL Server], about service management
- services [SQL Server]
- SQL Server Agent service, managing
- SQL Server services, about SQL Server service
- MSSQLServer
- server configuration [SQL Server]
- managing services [SQL Server]
- SQL Server Agent service
- services [SQL Server], managing
- administering SQL Server, services
- SQL Server services
ms.assetid: aa732e43-53ba-4eea-bb9b-089da0766fc1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e747a85c816c8e57757be9acb61b14204266ff35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62782055"
---
# <a name="manage-the-database-engine-services"></a>Управление службами компонента Database Engine
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает в операционных системах в качестве службы. Служба — это особый вид приложения, которое выполняется в системе в фоновом режиме. Службы обычно обеспечивают базовые функции операционной системы, например: ведение журнала событий, доступ к файлам или веб-страницам. Службы могут выполняться без отображения своего пользовательского интерфейса на рабочем столе компьютера. 
  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и некоторые другие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняются как службы и обычно запускаются при запуске операционной системы. Некоторые службы по умолчанию не запускаются, это зависит от указанных при установке параметров. В этом разделе описывается управление различными службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Прежде чем входить в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо уметь запускать, останавливать, приостанавливать и возобновлять, а также перезапускать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После входа можно выполнять различные задачи: администрировать сервер или выполнять запросы к базе данных.  
  
## <a name="using-the-sql-server-service"></a>Использование службы SQL Server  
 При запуске экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]запускается служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После того как будет запущена служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пользователи смогут устанавливать новые соединения с сервером. Служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может запускаться и останавливаться как любая служба, локально или удаленно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Служба называется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER), если это экземпляр по умолчанию, или MSSQL $*\<имя_экземпляра>*, если это именованный экземпляр.  
  
## <a name="using-sql-server-configuration-manager"></a>Использование диспетчера конфигурации SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager позволяет останавливать, запускать или приостанавливать различные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager не может [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] управлять службами.  
  
 Диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать для просмотра свойств выбранной службы. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager является оснасткой консоли [!INCLUDE[msCoName](../../includes/msconame-md.md)] управления (MMC). Дополнительные сведения о консоли MMC и работе оснастки см. в справке по Windows.  
  
 **Доступ к диспетчер конфигурации SQL Server**  
  
-   В меню **Пуск** последовательно укажите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
 **Доступ к диспетчер конфигурации SQL Serverам с помощью Windows 8**  
  
 Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления [!INCLUDE[msCoName](../../includes/msconame-md.md)] , а не изолированной программой, при работе в Windows 8.0 диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение. Чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите в чудо-кнопке **Поиск** в области **Приложения**значение **SQLServerManager12.msc** (для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]), **SQLServerManager11.msc** (для [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) или **SQLServerManager10.msc** (для[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]) и нажмите клавишу **ВВОД**.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|||  
|-|-|  
|[Требования безопасности к службам управления](security-requirements-for-managing-services.md)|[Предотвращение автоматического запуска экземпляра SQL Server &#40;диспетчер конфигурации SQL Server&#41;](scm-services-prevent-automatic-startup-of-an-instance.md)|  
|[Настройка учетных записей службы Windows и разрешений](configure-windows-service-accounts-and-permissions.md)|[Измените стартовую учетную запись службы для SQL Server &#40;диспетчер конфигурации SQL Server&#41;](scm-services-change-the-service-startup-account.md)|  
|[Запуск SQL Server при наличии и отсутствии сети](run-sql-server-with-or-without-a-network.md)|[Настройка параметров запуска сервера &#40;диспетчер конфигурации SQL Server&#41;](scm-services-configure-server-startup-options.md)|  
|[Обозреватель SQL Server службы &#40;ядро СУБД и SSAS&#41;](sql-server-browser-service-database-engine-and-ssas.md)|[Изменение пароля учетных записей, используемых SQL Server &#40;диспетчер конфигурации SQL Server&#41;](scm-services-change-the-password-of-the-accounts-used.md)|  
|[Параметры запуска службы Database Engine](database-engine-service-startup-options.md)|[Настройка журналов ошибок SQL Server](scm-services-configure-sql-server-error-logs.md)|  
|[Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server](start-stop-pause-resume-restart-sql-server-services.md)|[Изменение режима проверки подлинности сервера](change-server-authentication-mode.md)|  
|[Запуск SQL Server в однопользовательском режиме](start-sql-server-in-single-user-mode.md)|[cлужба «Модуль записи SQL»](sql-writer-service.md)|  
|[Запустите SQL Server с минимальной конфигурацией](start-sql-server-with-minimal-configuration.md)|[Трансляция сообщения о завершении работы &#40;командной строки&#41;](broadcast-a-shutdown-message-command-prompt.md)|  
|[Подключение к другому компьютеру &#40;диспетчер конфигурации SQL Server&#41;](scm-services-connect-to-another-computer.md)|[Войдите в экземпляр SQL Server &#40;командной строки&#41;](log-in-to-an-instance-of-sql-server-command-prompt.md)|  
|[Задайте для экземпляра SQL Server автоматический запуск &#40;диспетчер конфигурации SQL Server&#41;](scm-services-set-an-instance-to-start-automatically.md)|[Настройка разрешений файловой системы для доступа к компоненту ядра СУБД](configure-file-system-permissions-for-database-engine-access.md)|  
  
## <a name="related-content"></a>См. также  
 [Configure SQL Server Agent](../../ssms/agent/sql-server-agent.md)  
  
 [Вход в систему SQL Server](logging-in-to-sql-server.md)  
  
  
