---
title: Настройка клиентских протоколов | Документы Майкрософт
description: Узнайте о различных способах настройки протоколов, используемых клиентскими приложениями в SQL Server. Поддерживаются протоколы TCP/IP, протокол именованных каналов и протокол общей памяти.
ms.custom: ''
ms.date: 07/27/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default protocols
- network protocols [SQL Server], client configuration
- TCP/IP [SQL Server], client protocols
- disabling client protocols
- ordering protocols [SQL Server]
- protocols [SQL Server], order for client computers
- configure client protocols
- client protocols [SQL Server]
- protocols [SQL Server], client configuration
- default protocols, client
ms.assetid: 3dfa2702-ba65-43b4-a777-6727846e133a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5cca0b54c983fe7a4ef122a45070e53d2143a05e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85697981"
---
# <a name="configure-client-protocols"></a>настройка клиентских протоколов
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В этом разделе описано, как настроить клиентские протоколы, используемые клиентскими приложениями [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает клиентский обмен данными через сетевой протокол TCP/IP и протокол именованных каналов. Может также использоваться протокол общей памяти, если клиент устанавливает соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на том же компьютере. Существуют три наиболее часто используемых способа для выбора протокола.  
  
-   Настройте все клиентские приложения для использования одного и того же сетевого протокола, определив порядок протоколов в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Настройте отдельное клиентское приложение для использования другого сетевого протокола, создав псевдоним. Дополнительные сведения см. в разделе [Создание или удаление псевдонима сервера для использования клиентом (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md).  
  
-   Для некоторых клиентских приложений, например sqlcmd.exe, можно указать протокол как часть строки соединения. Дополнительные сведения см. в разделе [Подключение к компоненту Database Engine при помощи программы sqlcmd](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md).  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
###  <a name="to-enable-or-disable-a-client-protocol"></a><a name="EnableDisable"></a> Включение или отключение протокола клиента  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разверните узел **Конфигурация SQL Server Native Client**, щелкните правой кнопкой мыши элемент **Клиентские протоколы** и выберите пункт **Свойства**.  
  
2.  Выберите протокол в окне **Отключенные протоколы** и нажмите **Включить**, чтобы разрешить его работу.  
  
3.  Выберите протокол в окне **Включенные протоколы** и нажмите кнопку **Отключить**, чтобы запретить его работу.  
  
###  <a name="to-change-the-default-protocol-or-the-protocol-order-for-client-computers"></a><a name="ChangeDefault"></a> Изменение протокола по умолчанию или порядка задействования протоколов для компьютера клиента  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разверните узел **Конфигурация SQL Server Native Client**, щелкните правой кнопкой мыши элемент **Клиентские протоколы** и выберите пункт **Свойства**.  
  
2.  В окне **Включенные протоколы** нажмите кнопку **Вверх** или **Вниз**для изменения порядка, в котором задействуются протоколы при попытке соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Верхний протокол в окне **Разрешенные протоколы** является протоколом по умолчанию.  
  
    > [!IMPORTANT]  
    >  Диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает параметры реестра для конфигураций псевдонимов сервера и клиентскую сетевую библиотеку по умолчанию. Однако приложение не устанавливает какие-либо клиентские сетевые библиотеки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или сетевые протоколы. Клиентские сетевые библиотеки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливаются во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; сетевые протоколы ― во время установки Microsoft Windows (или через элемент **Сеть** на **панели управления**). Конкретный сетевой протокол может быть недоступен при установке Windows. Дополнительные сведения об установке этих сетевых протоколов см. в документации поставщика.  
  
###  <a name="to-configure-a-client-to-use-tcpip"></a><a name="Configure"></a> Настройка клиента для использования TCP/IP  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разверните узел **Конфигурация SQL Server Native Client**, щелкните правой кнопкой мыши элемент **Клиентские протоколы** и выберите пункт **Свойства**.  
  
2.  В поле **Включенные протоколы** используйте кнопки со стрелками вниз и вверх, чтобы изменить порядок применения протоколов при попытках установить соединение с SQL Server. Верхний протокол в окне **Разрешенные протоколы** является протоколом по умолчанию.  
  
 Протокол общедоступной памяти активируется отдельно, установкой флажка **Включенный протокол общей памяти** .  
  
## <a name="see-also"></a>См. также:  
 [Настройка параметра конфигурации сервера «remote login timeout»](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md)  
  
  
