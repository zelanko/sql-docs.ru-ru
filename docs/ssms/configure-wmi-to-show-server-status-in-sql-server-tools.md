---
title: "Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 950c4d2fdef0359042ebbed168c761e44316ab03
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server
В этом разделе описывается настройка инструментария WMI для отображения состояния сервера в средствах SQL Server в [!INCLUDE[ssCurrent](../includes/sscurrent_md.md)]. При соединении с сервером компоненты «Зарегистрированные серверы» и «Обозреватель объектов» среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)], как и диспетчер конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] , используют инструментарий WMI для получения сведений о состоянии служб [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] (MSSQLSERVER) и агента [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] (MSSQLSERVER). Для отображения состояния службы пользователь должен иметь права удаленного доступа к объекту инструментария WMI. Для настройки этого разрешения на сервере должен быть установлен инструментарий WMI.  
  
## <a name="SSMSProcedure"></a>Настройка разрешения WMI  
  
1.  В меню **Пуск** на удаленном сервере выберите **Выполнить**.  
  
2.  В окне **Открыть** введите **wmimgmt.msc**и нажмите кнопку **ОК**.  
  
3.  В программе **инфраструктуры управления Windows** щелкните правой кнопкой мыши **Элемент управления WMI (локальный)**и выберите **Свойства**.  
  
4.  В диалоговом окне **Свойства элемента управления WMI (локальный)** на вкладке **Безопасность** разверните **Корень**и щелкните **CIMV2**.  
  
5.  Щелкните **Безопасность** , чтобы открыть диалоговое окно **Защита для ROOT\CIMV2** .  
  
6.  Добавьте группу или пользователя в поле **Имена групп или пользователей** и выберите их.  
  
7.  В поле **Разрешение для***<group or user>* выберите столбец **Разрешить** для разрешения **Включить удаленно** у пользователей, которым требуется удаленно определить состояние службы.  
  
## <a name="see-also"></a>См. также:  
[Запуск, остановка или приостановка службы агента SQL Server](../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  

