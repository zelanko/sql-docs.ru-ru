---
title: Настройка параметров запуска сервера (диспетчер конфигурации SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
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
manager: craigg
ms.openlocfilehash: b5a2bde2933c8495da25c87da3aa6a40a9585b96
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072934"
---
# <a name="configure-server-startup-options-sql-server-configuration-manager"></a>Настройка параметров запуска сервера (диспетчер конфигурации SQL Server)
  В этом разделе описано, как настроить параметры запуска, которые будут использоваться при каждом запуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список параметров запуска см. в разделе [Параметры запуска службы Database Engine](database-engine-service-startup-options.md).  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
### <a name="limitations-and-restrictions"></a>Ограничения  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает параметры запуска в реестр. Они вступают в силу при следующем запуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 В кластере изменения должны вноситься на активном сервере, пока [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] находится в режиме «в сети», и вступают в силу при перезапуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . При следующей отработке отказа произойдет обновление реестра другого узла.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Настраивать параметры запуска сервера могут только пользователи, уполномоченные изменять соответствующие записи в реестре. Это следующие пользователи.  
  
-   Члены локальной группы администраторов.  
  
-   Учетная запись домена, используемая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] настроен для работы под определенной учетной записью домена.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-configure-startup-options"></a>Настройка параметров запуска  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберите пункт **Службы SQL Server**.  
  
    > [!NOTE]  
    >  Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), а не изолированной программой, при работе в более новых версиях Windows диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.  
    >   
    >  -   **Windows 10**:  
    >          Чтобы открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager на **начальная страница**, введите SQLServerManager12.msc (для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). Для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] замените 12 на меньшее число. Щелкнув SQLServerManager12.msc Откроется диспетчер конфигурации. Чтобы закрепить диспетчер конфигурации на начальной странице или панели задач, щелкните правой кнопкой мыши SQLServerManager12.msc и нажмите кнопку **открыть расположение файла**. В проводнике Windows щелкните правой кнопкой мыши SQLServerManager12.msc затем **закрепить на начальном экране** или **закрепить на панели задач**.  
    > -   **Windows 8**:  
    >          Чтобы открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager в **поиска** чудо **приложений**, тип **SQLServerManager\<версия > .msc** например `SQLServerManager12.msc`, а затем нажмите клавишу **ввод**.  
  
2.  На правой панели щелкните правой кнопкой мыши элемент **SQL Server (***<имя_экземпляра>***)** и выберите пункт **Свойства**.  
  
3.  На вкладке **Параметры запуска** в поле **Укажите параметр запуска** введите параметр и нажмите кнопку **Добавить**.  
  
     Например, для запуска в однопользовательском режиме, введите `-m` в **укажите параметр запуска** поле и нажмите кнопку **добавить**. (Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапускается в однопользовательском режиме, остановите агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В противном случае агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может установить соединение первым, что не позволит подключиться второму пользователю.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Перезапустите компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
    > [!WARNING]  
    >  После завершения работы в однопользовательском режиме, в параметры запуска, выберите `-m` параметр в **существующие параметры** , а затем щелкните **удалить**. Чтобы вернуться к обычному многопользовательскому режиму [!INCLUDE[ssDE](../../includes/ssde-md.md)] , перезапустите компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Запуск SQL Server в однопользовательском режиме](start-sql-server-in-single-user-mode.md)   
 [Подключение к SQL Server в случае, если доступ системных администраторов заблокирован](connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Запуск, остановка или приостановка службы агента SQL Server](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
