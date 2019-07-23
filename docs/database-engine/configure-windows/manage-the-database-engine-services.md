---
title: Управление службами компонента Database Engine | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
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
ms.openlocfilehash: 6ac35c702783ca5b80367c6f41af9c4c450e0be7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997967"
---
# <a name="manage-the-database-engine-services"></a>Управление службами компонента Database Engine
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается в операционной системе в качестве службы. Служба — это особый вид приложения, которое выполняется в системе в фоновом режиме. Службы обычно обеспечивают базовые функции операционной системы, например: ведение журнала событий, доступ к файлам или веб-страницам. Службы могут выполняться без отображения своего пользовательского интерфейса на рабочем столе компьютера. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и некоторые другие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняются как службы и обычно запускаются при запуске операционной системы. Некоторые службы по умолчанию не запускаются, это зависит от указанных при установке параметров. В этом разделе описывается управление различными службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Прежде чем входить в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо уметь запускать, останавливать, приостанавливать и возобновлять, а также перезапускать экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. После входа можно выполнять различные задачи: администрировать сервер или выполнять запросы к базе данных.  
  
## <a name="using-the-sql-server-service"></a>Использование службы SQL Server  
 При запуске экземпляра [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]запускается служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После того как будет запущена служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пользователи смогут устанавливать новые соединения с сервером. Служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может запускаться и останавливаться как любая служба, локально или удаленно. Служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER), если это экземпляр по умолчанию, или MSSQL$ *\<имя_экземпляра>* , если это именованный экземпляр.  
  
## <a name="using-sql-server-configuration-manager"></a>Использование диспетчера конфигурации SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет останавливать, запускать и приостанавливать различные службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Диспетчер конфигурации не может управлять службами [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 Диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать для просмотра свойств выбранной службы. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Диспетчер конфигурации является оснасткой консоли управления [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MMC). Дополнительные сведения о консоли MMC и работе оснастки см. в справке по Windows.  
  
 **Запуск диспетчера конфигурации SQL Server**  
  
-   В меню **Пуск** последовательно укажите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
 **Доступ к диспетчеру конфигурации SQL Server с помощью Windows 8**  
  
 Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления [!INCLUDE[msCoName](../../includes/msconame-md.md)] , а не изолированной программой, при работе в Windows 8.0 диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение. Чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите в чудо-кнопке **Поиск** в области **Приложения**значение **SQLServerManager12.msc** (для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]), **SQLServerManager11.msc** (для [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) или **SQLServerManager10.msc** (для[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]) и нажмите клавишу **ВВОД**.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|||  
|-|-|  
|[Требования безопасности к службам управления](../../database-engine/configure-windows/security-requirements-for-managing-services.md)|[Отключение автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/scm-services-prevent-automatic-startup-of-an-instance.md)|  
|[Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)|[Изменение стартовой учетной записи службы для SQL Server (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/scm-services-change-the-service-startup-account.md)|  
|[Запуск SQL Server при наличии и отсутствии сети](../../database-engine/configure-windows/run-sql-server-with-or-without-a-network.md)|[Настройка параметров запуска сервера (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)|  
|[Служба обозревателя SQL Server (компонент Database Engine и SSAS)](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md)|[Изменение пароля учетных записей, используемых SQL Server (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/scm-services-change-the-password-of-the-accounts-used.md)|  
|[Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md)|[Настройка журналов ошибок SQL Server](../../database-engine/configure-windows/scm-services-configure-sql-server-error-logs.md)|  
|[Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)|[Изменение режима проверки подлинности сервера](../../database-engine/configure-windows/change-server-authentication-mode.md)|  
|[Запуск SQL Server в однопользовательском режиме](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)|[cлужба «Модуль записи SQL»](../../database-engine/configure-windows/sql-writer-service.md)|  
|[Запустите SQL Server с минимальной конфигурацией](../../database-engine/configure-windows/start-sql-server-with-minimal-configuration.md)|[Рассылка сообщения о завершении работы (командная строка)](../../database-engine/configure-windows/broadcast-a-shutdown-message-command-prompt.md)|  
|[Подключение к другому компьютеру (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/scm-services-connect-to-another-computer.md)|[Вход в экземпляр SQL Server (командная строка)](../../database-engine/configure-windows/log-in-to-an-instance-of-sql-server-command-prompt.md)|  
|[Настройка автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/scm-services-set-an-instance-to-start-automatically.md)|[Настройка разрешений файловой системы для доступа к компоненту ядра СУБД](../../database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access.md)|  
  
## <a name="related-content"></a>См. также  
 [Настройка агента SQL Server](../../ssms/agent/configure-sql-server-agent.md)  
  
 [Вход в систему SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)  
  
  
