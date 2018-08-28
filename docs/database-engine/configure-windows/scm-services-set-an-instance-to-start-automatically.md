---
title: Службы SCM. Настройка автоматического запуска экземпляра | Документы Майкрософт
ms.custom: ''
ms.date: 01/06/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
caps.latest.revision: 35
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 34430bf70af547a54402c776b05ac6666bee8b71
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40415887"
---
# <a name="scm-services---set-an-instance-to-start-automatically"></a>Службы SCM. Настройка автоматического запуска экземпляра
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описано, как настроить автоматический запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации SQL Server. Во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно настраивается для автоматического запуска. Если это не было выполнено, настройку можно произвести в любой момент.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a>Настройка автоматического запуска экземпляра SQL Server  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
    > [!NOTE]  
    >  Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), а не изолированной программой, при работе в более новых версиях Windows диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.  
    >   
    >  -   **Windows 10**:  
    >          чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите на **начальной странице**SQLServerManager13.msc (для [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). Для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] замените 13 на меньшее число. Если щелкнуть SQLServerManager13.msc, откроется диспетчер конфигурации. Чтобы закрепить диспетчер конфигурации на начальной странице или панели задач, щелкните правой кнопкой мыши SQLServerManager13.msc и выберите пункт **Открыть папку с файлом**. В проводнике щелкните правой кнопкой мыши SQLServerManager13.msc, а затем выберите команду **Закрепить на начальном экране** или **Закрепить на панели задач**.  
    > -   **Windows 8**:  
    >          Чтобы открыть диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью чудо-кнопки **Поиск**, введите на вкладке **Приложения** текст **SQLServerManager\<версия>.msc** (например, **SQLServerManager13.msc**) и нажмите клавишу **ВВОД**.  
  
2.  Откройте **Диспетчер конфигурации SQL Server**, раскройте **Службы**и щелкните **SQL Server**.  
  
3.  В области сведений щелкните правой кнопкой имя экземпляра, который должен запускаться автоматически, и выберите пункт **Свойства**.  
  
4.  В диалоговом окне **Свойства SQL Server \<***имя_экземпляра***>** установите для параметра **Режим запуска** значение **Автоматически**.  
  
5.  Нажмите кнопку **ОК**и закройте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Отключение автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/scm-services-prevent-automatic-startup-of-an-instance.md)   
 [Подключение к другому компьютеру (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/scm-services-connect-to-another-computer.md)   
 [Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
