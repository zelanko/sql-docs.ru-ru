---
title: "Настройка параметров запуска сервера (диспетчер конфигурации SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "параметры [SQL Server], параметры запуска"
  - "SQL Server, параметры запуска"
  - "однопользовательский режим [SQL Server], запуск"
  - "параметры запуска [SQL Server]"
  - "службы SQL Server, настройка параметров запуска"
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Настройка параметров запуска сервера (диспетчер конфигурации SQL Server)
  В этом разделе описано, как настроить параметры запуска, которые будут использоваться при каждом запуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список параметров запуска см. в разделе [Параметры запуска службы Database Engine](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
### Ограничения  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записывает параметры запуска в реестр. Они вступают в силу при следующем запуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 В кластере изменения должны вноситься на активном сервере, пока [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] находится в режиме «в сети», и вступают в силу при перезапуске компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . При следующей отработке отказа произойдет обновление реестра другого узла.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Настраивать параметры запуска сервера могут только пользователи, уполномоченные изменять соответствующие записи в реестре. Это следующие пользователи.  
  
-   Члены локальной группы администраторов.  
  
-   Учетная запись домена, используемая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] настроен для работы под определенной учетной записью домена.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### Настройка параметров запуска  
  
1.  Нажмите кнопку **Пуск** , укажите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
    > [!NOTE]  
    >  Так как диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления ([!INCLUDE[msCoName](../../includes/msconame-md.md)]), а не изолированной программой, при работе в более новых версиях Windows диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.  
    >   
    >  -   **Windows 10**:  
    >          чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], введите на **начальной странице** "SQLServerManager13.msc" (для [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). Для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] замените 13 на меньшее число. Если щелкнуть SQLServerManager13.msc, откроется диспетчер конфигурации. Чтобы закрепить диспетчер конфигурации на начальной странице или панели задач, щелкните правой кнопкой мыши SQLServerManager13.msc и выберите пункт **Открыть папку с файлом**. В проводнике щелкните правой кнопкой мыши SQLServerManager13.msc, а затем выберите команду **Закрепить на начальном экране** или **Закрепить на панели задач**.  
    > -   **Windows 8**:  
    >          чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с помощью чудо-кнопки **Поиск** на вкладке **Приложения** введите **SQLServerManager\<версия>.msc** (например, **SQLServerManager13.msc**) и нажмите клавишу **ВВОД**.  
  
2.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберите пункт **Службы SQL Server**.  
  
3.  На правой панели щелкните правой кнопкой мыши элемент **SQL Server (***\<имя_экземпляра>***)** и выберите пункт **Свойства**.  
  
4.  На вкладке **Параметры запуска** в поле **Укажите параметр запуска** введите параметр и нажмите кнопку **Добавить**.  
  
     Например, для запуска в однопользовательском режиме введите **-m** в поле **Укажите параметр запуска** и нажмите кнопку **Добавить**. (Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапускается в однопользовательском режиме, остановите агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В противном случае агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может установить соединение первым, что не позволит подключиться второму пользователю.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Перезапустите компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
    > [!WARNING]  
    >  После завершения работы в однопользовательском режиме выберите в окне "Параметры запуска" в поле **Существующие параметры** параметр **-m** и нажмите кнопку **Удалить**. Чтобы вернуться к обычному многопользовательскому режиму [!INCLUDE[ssDE](../../includes/ssde-md.md)], перезапустите компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## См. также:  
 [Запуск SQL Server в однопользовательском режиме](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)   
 [Подключение к SQL Server в случае, если доступ системных администраторов заблокирован](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Запуск, остановка или приостановка службы агента SQL Server](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  