---
title: Настройка автоматического изменения запуска экземпляра SQL Server (диспетчер конфигурации SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
caps.latest.revision: 34
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fdb191490353e6260467b50c26f94892ff6ce83b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37254696"
---
# <a name="set-an-instance-of-sql-server-to-start-automatically-sql-server-configuration-manager"></a>Настройка автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server)
  В этом разделе описано, как настроить автоматический запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации SQL Server. Во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно настраивается для автоматического запуска. Если это не было выполнено, настройку можно произвести в любой момент.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a>Настройка автоматического запуска экземпляра SQL Server  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
    > [!NOTE]  
    >  Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), а не изолированной программой, при работе в более новых версиях Windows диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.  
    >   
    >  -   **Windows 10**:  
    >          Чтобы открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager на **начальная страница**, введите SQLServerManager12.msc (для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). Для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] замените 12 на меньшее число. Щелкнув SQLServerManager12.msc Откроется диспетчер конфигурации. Чтобы закрепить диспетчер конфигурации на начальной странице или панели задач, щелкните правой кнопкой мыши SQLServerManager12.msc и нажмите кнопку **открыть расположение файла**. В проводнике Windows щелкните правой кнопкой мыши SQLServerManager12.msc затем **закрепить на начальном экране** или **закрепить на панели задач**.  
    > -   **Windows 8**:  
    >          Чтобы открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager в **поиска** чудо **приложений**, тип **SQLServerManager\<версия > .msc** например `SQLServerManager12.msc`, а затем нажмите клавишу **ввод**.  
  
2.  Откройте **Диспетчер конфигурации SQL Server**, раскройте **Службы**и щелкните **SQL Server**.  
  
3.  В области сведений щелкните правой кнопкой имя экземпляра, который должен запускаться автоматически, и выберите пункт **Свойства**.  
  
4.  В диалоговом окне **Свойства SQL Server \<***имя_экземпляра***>** установите для параметра **Режим запуска** значение **Автоматически**.  
  
5.  Нажмите кнопку **ОК**и закройте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Отключение автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server)](scm-services-prevent-automatic-startup-of-an-instance.md)   
 [Подключение к другому компьютеру (диспетчер конфигурации SQL Server)](scm-services-connect-to-another-computer.md)   
 [Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
