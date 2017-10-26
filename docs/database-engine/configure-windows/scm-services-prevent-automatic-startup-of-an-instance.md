---
title: "Службы SCM. Отключение автоматического запуска экземпляра | Документы Майкрософт"
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
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3f6a163ec9e6bb37cbbb190395a28273e0521765
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="scm-services---prevent-automatic-startup-of-an-instance"></a>Службы SCM. Отключение автоматического запуска экземпляра
  В этом разделе описано, как отключить автоматический запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации SQL Server. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно настраивается для автоматического запуска. Это вы можете изменить, задав для экземпляра режим запуска вручную.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a>Отключение автоматического запуска экземпляра SQL Server  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
    > [!NOTE]  
    >  Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), а не изолированной программой, при работе в более новых версиях Windows диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.  
    >   
    >  -   **Windows 10**:  
    >          чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите на **начальной странице**SQLServerManager13.msc (для [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). Для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] замените 13 на меньшее число. Если щелкнуть SQLServerManager13.msc, откроется диспетчер конфигурации. Чтобы закрепить диспетчер конфигурации на начальной странице или панели задач, щелкните правой кнопкой мыши SQLServerManager13.msc и выберите пункт **Открыть папку с файлом**. В проводнике щелкните правой кнопкой мыши SQLServerManager13.msc, а затем выберите команду **Закрепить на начальном экране** или **Закрепить на панели задач**.  
    > -   **Windows 8**:  
    >          Чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью чудо-кнопки **Поиск**, введите на вкладке **Приложения** текст **SQLServerManager\<версия>.msc** (например, **SQLServerManager13.msc**) и нажмите клавишу **ВВОД**.  
  
2.  В диспетчере конфигурации SQL Server разверните **Службы**, затем выберите **SQL Server**.  
  
3.  В области сведений щелкните правой кнопкой мыши **MSSQLServer**и выберите пункт **Свойства**.  
  
4.  В поле **Свойства** диалогового окна **Свойства SQL Server \<***имя_экземпляра***>** установите для параметра **Режим запуска** значение **Вручную**.  
  
5.  Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Свойства SQL Server \<***имя_экземпляра***>**, а затем закройте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  

