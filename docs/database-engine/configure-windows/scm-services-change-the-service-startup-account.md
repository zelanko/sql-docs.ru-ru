---
title: "Службы SCM. Изменение стартовой учетной записи службы | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server services, startup account changes
- startup accounts [SQL Server]
- changing startup accounts for services
ms.assetid: d721c796-0397-46a7-901b-1a9a3c3fb385
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dd24d37939ba9d1a97b0645ec17622a74461c0c1
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="scm-services---change-the-service-startup-account"></a>Службы SCM. Изменение стартовой учетной записи службы
  В этом разделе описывается использование диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для изменения параметров запуска служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и изменения учетных записей служб, которые используются компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] браузером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или PowerShell. Дополнительные сведения о выборе учетной записи службы см. в разделе [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
> [!IMPORTANT]  
>  После изменения стартовой учетной записи службы для компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо перезапустить службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)]), чтобы изменение вступило в силу. При перезапуске службы все базы данных, связанные с этим экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , станут недоступны до того момента, когда служба успешно перезапустится. Если нужно изменить стартовую учетную запись службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , это можно делать только в период планового обслуживания или в случае, если базы данных можно перевести в режим «вне сети», не создавая помех для повседневной работы.  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Кластеризованные серверы  
  
     Изменение учетной записи службы, которая используется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должно выполняться из активного узла кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Во время работы на Windows Server 2008 (в нестандартной конфигурации, использующей группы домена) для изменения учетной записи службы, которая используется продуктом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо остановить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , отключив группы ресурсов.  
  
-   Обновление номера SKU (от[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] до другого номера SKU)  
  
     Во время установки [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] служба « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент» настраивается для использование учетной записи Network Service, но отключается. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно изменить учетную запись, назначенную для службы « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агент», но нельзя включить или запустить эту службу. После обновления номера SKU с [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] до другого номера SKU служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не включается автоматически, но при необходимости ее можно включить с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и задать для нее тип запуска «Вручную» или «Авто».  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-change-the-sql-server-service-startup-account"></a>Изменение стартовой учетной записи службы SQL Server  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
    > [!NOTE]  
    >  Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), а не изолированной программой, при работе в более новых версиях Windows диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.  
    >   
    >  -   **Windows 10**:  
    >          чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите на **начальной странице**SQLServerManager13.msc (для [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). Для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] замените 13 на меньшее число. Если щелкнуть SQLServerManager13.msc, откроется диспетчер конфигурации. Чтобы закрепить диспетчер конфигурации на начальной странице или панели задач, щелкните правой кнопкой мыши SQLServerManager13.msc и выберите пункт **Открыть папку с файлом**. В проводнике щелкните правой кнопкой мыши SQLServerManager13.msc, а затем выберите команду **Закрепить на начальном экране** или **Закрепить на панели задач**.  
    > -   **Windows 8**:  
    >          Чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью чудо-кнопки **Поиск**, введите на вкладке **Приложения** текст **SQLServerManager\<версия>.msc** (например, **SQLServerManager13.msc**) и нажмите клавишу **ВВОД**.  
  
2.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выберите пункт **Службы SQL Server**.  
  
3.  В области сведений щелкните правой кнопкой мыши имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого нужно изменить стартовую учетную запись службы, и пункт **Свойства**.  
  
4.  В диалоговом окне **Свойства SQL Server \<***имя_экземпляра***>** перейдите на вкладку **Вход** и выберите один из типов учетных записей в поле **Использовать для входа**.  
  
5.  Выбрав новую стартовую учетную запись службы, нажмите кнопку **ОК**.  
  
     Появится окно сообщения с подтверждением перезапуска службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
6.  Нажмите **Да**и закройте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)   
 [Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server](http://msdn.microsoft.com/library/7e97197b-ed4d-40d1-9a52-9ab1d92401d7)  
  
  

