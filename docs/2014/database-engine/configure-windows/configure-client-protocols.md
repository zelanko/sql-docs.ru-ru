---
title: Настройка клиентских протоколов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.assetid: 3dfa2702-ba65-43b4-a777-6727846e133a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4ac07771f2b47a8bab11ab4b02ff7780c89e1733
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935785"
---
# <a name="configure-client-protocols"></a>настройка клиентских протоколов
  В этом разделе описано, как настроить клиентские протоколы, используемые клиентскими приложениями [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает клиентский обмен данными через сетевой протокол TCP/IP и протокол именованных каналов. Может также использоваться протокол общей памяти, если клиент устанавливает соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на том же компьютере. Существуют три наиболее часто используемых способа для выбора протокола.  
  
-   Настройте все клиентские приложения для использования одного и того же сетевого протокола, определив порядок протоколов в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Настройте отдельное клиентское приложение для использования другого сетевого протокола, создав псевдоним. Дополнительные сведения см. в разделе [Создание или удаление псевдонима сервера для использования клиентом (диспетчер конфигурации SQL Server)](create-or-delete-a-server-alias-for-use-by-a-client.md).  
  
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
 [Настройка параметра конфигурации сервера «remote login timeout»](configure-the-remote-login-timeout-server-configuration-option.md)  
  
  
