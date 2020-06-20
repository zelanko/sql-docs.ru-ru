---
title: Настройка параметров запуска сервера (диспетчер конфигурации SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], startup options
- SQL Server, startup options
- single-user mode [SQL Server], starting in
- startup options [SQL Server]
- SQL Server services, setting startup options
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af822eb405fb66f5e91340d42fc79bef0d769fbf
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935065"
---
# <a name="configure-server-startup-options-sql-server-configuration-manager"></a>Настройка параметров запуска сервера (диспетчер конфигурации SQL Server)
  В этом разделе описано, как настроить параметры запуска, которые будут использоваться при каждом запуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], с помощью Configuration Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список параметров запуска см. в разделе [Параметры запуска службы Database Engine](database-engine-service-startup-options.md).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
### <a name="limitations-and-restrictions"></a>Ограничения  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает параметры запуска в реестр. Они вступают в силу при следующем запуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 В кластере изменения должны вноситься на активном сервере, пока [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] находится в режиме «в сети», и вступают в силу при перезапуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . При следующей отработке отказа произойдет обновление реестра другого узла.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Настраивать параметры запуска сервера могут только пользователи, уполномоченные изменять соответствующие записи в реестре. Это следующие пользователи.  
  
-   Члены локальной группы администраторов.  
  
-   Учетная запись домена, используемая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] настроен для работы под определенной учетной записью домена.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-configure-startup-options"></a>Настройка параметров запуска  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберите пункт **Службы SQL Server**.  
  
    > [!NOTE]  
    >  Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), а не изолированной программой, при работе в более новых версиях Windows диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.  
    >   
    >  -   **Windows 10**:  
    >          Чтобы открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, на **начальной странице**введите SQLServerManager12. msc (для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ). Для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] замените 12 на меньшее число. Если щелкнуть SQLServerManager12.msc, откроется диспетчер конфигурации. Чтобы закрепить Configuration Manager на начальной странице или на панели задач, щелкните правой кнопкой мыши SQLServerManager12. msc и выберите **открыть расположение файла**. В проводнике Windows щелкните правой кнопкой мыши файл SQLServerManager12. msc и выберите пункт **закрепить на** **панели задач или закрепить на**ней.  
    > -   **Windows 8**:  
    >          Чтобы открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, во вложенном поле **Поиск** в разделе **приложения**введите **SQLServerManager \<version> . msc** , например `SQLServerManager12.msc` , и нажмите клавишу **Ввод**.  
  
2.  На правой панели щелкните правой кнопкой мыши элемент **SQL Server (***<имя_экземпляра>***)** и выберите пункт **Свойства**.  
  
3.  На вкладке **Параметры запуска** в поле **Укажите параметр запуска** введите параметр и нажмите кнопку **Добавить**.  
  
     Например, чтобы запустить в однопользовательском режиме, введите `-m` в поле **укажите параметр запуска** и нажмите кнопку **добавить**. (Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапускается в однопользовательском режиме, остановите агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В противном случае агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может установить соединение первым, что не позволит подключиться второму пользователю.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Перезапустите компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
    > [!WARNING]  
    >  Завершив работу в однопользовательском режиме, в поле Параметры запуска выберите `-m` параметр в поле **существующие параметры** , а затем нажмите кнопку **Удалить**. Чтобы вернуться к обычному многопользовательскому режиму [!INCLUDE[ssDE](../../includes/ssde-md.md)] , перезапустите компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Запуск SQL Server в однопользовательском режиме](start-sql-server-in-single-user-mode.md)   
 [Подключение к SQL Server при блокировке системных администраторов](connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
