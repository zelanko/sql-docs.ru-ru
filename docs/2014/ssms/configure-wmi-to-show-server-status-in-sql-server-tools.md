---
title: Настройка инструментария WMI для отображения состояния сервера в инструментальных средствах SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c0b0b8236187698917dddd3ca98830add6c3fde9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63245670"
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
  
7.  В **разрешения для**_\<группы или пользователя >_ выберите **Разрешить** столбец, для **включить удаленно** разрешение , для пользователей, которым требуется удаленно определить состояние службы.  
  
## <a name="see-also"></a>См. также  
 [Запуск, остановка или приостановка службы агента SQL Server](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
