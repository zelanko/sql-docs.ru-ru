---
title: Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e24e138e44a9c0493e5dcd9acac14de61b468c17
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43819890"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server
  В этом разделе описывается настройка инструментария WMI для отображения состояния сервера в средствах SQL Server в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. При соединении с сервером компоненты «Зарегистрированные серверы» и «Обозреватель объектов» среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], как и диспетчер конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , используют инструментарий WMI для получения сведений о состоянии служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) и агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER). Для отображения состояния службы пользователь должен иметь права удаленного доступа к объекту инструментария WMI. Для настройки этого разрешения на сервере должен быть установлен инструментарий WMI.  
  
##  <a name="SSMSProcedure"></a> Настройка разрешения WMI  
  
1.  В меню **Пуск** на удаленном сервере выберите **Выполнить**.  
  
2.  В **откройте** поле типа `wmimgmt.msc`, а затем нажмите кнопку **ОК**.  
  
3.  В программе **инфраструктуры управления Windows** щелкните правой кнопкой мыши **Элемент управления WMI (локальный)** и выберите **Свойства**.  
  
4.  В диалоговом окне **Свойства элемента управления WMI (локальный)** на вкладке **Безопасность** разверните **Корень**и щелкните **CIMV2**.  
  
5.  Щелкните **Безопасность** , чтобы открыть диалоговое окно **Защита для ROOT\CIMV2** .  
  
6.  Добавьте группу или пользователя в поле **Имена групп или пользователей** и выберите их.  
  
7.  В **разрешения для ***\<группы или пользователя >* выберите **Разрешить** столбец, для **включить удаленно** у пользователей, которым требуется удаленно определить состояние службы.  
  
## <a name="see-also"></a>См. также  
 [Запуск, остановка или приостановка службы агента SQL Server](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
