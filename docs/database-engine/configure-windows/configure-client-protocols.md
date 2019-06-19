---
title: Настройка клиентских протоколов | Документы Майкрософт
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
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 204617360c30dd4ea7201c86486af2483482fa08
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799482"
---
# <a name="configure-client-protocols"></a>настройка клиентских протоколов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описано, как настроить клиентские протоколы, используемые клиентскими приложениями [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает клиентский обмен данными через сетевой протокол TCP/IP и протокол именованных каналов. Может также использоваться протокол общей памяти, если клиент устанавливает соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на том же компьютере. Существуют три наиболее часто используемых способа для выбора протокола.  
  
-   Настройте все клиентские приложения для использования одного и того же сетевого протокола, определив порядок протоколов в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Настройте отдельное клиентское приложение для использования другого сетевого протокола, создав псевдоним. Дополнительные сведения см. в разделе [Создание или удаление псевдонима сервера для использования клиентом (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md).  
  
-   Для некоторых клиентских приложений, например sqlcmd.exe, можно указать протокол как часть строки соединения. Дополнительные сведения см. в разделе [Подключение к компоненту Database Engine при помощи программы sqlcmd](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md).  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
###  <a name="EnableDisable"></a> Включение или отключение протокола клиента  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разверните узел **Конфигурация SQL Server Native Client**, щелкните правой кнопкой мыши элемент **Клиентские протоколы** и выберите пункт **Свойства**.  
  
2.  Выберите протокол в окне **Отключенные протоколы** и нажмите **Включить**, чтобы разрешить его работу.  
  
3.  Выберите протокол в окне **Включенные протоколы** и нажмите кнопку **Отключить**, чтобы запретить его работу.  
  
###  <a name="ChangeDefault"></a> Изменение протокола по умолчанию или порядка задействования протоколов для компьютера клиента  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разверните узел **Конфигурация SQL Server Native Client**, щелкните правой кнопкой мыши элемент **Клиентские протоколы** и выберите пункт **Свойства**.  
  
2.  В окне **Включенные протоколы** нажмите кнопку **Вверх** или **Вниз**для изменения порядка, в котором задействуются протоколы при попытке соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Верхний протокол в окне **Разрешенные протоколы** является протоколом по умолчанию.  
  
    > [!IMPORTANT]  
    >  Диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает параметры реестра для конфигураций псевдонимов сервера и клиентскую сетевую библиотеку по умолчанию. Однако приложение не устанавливает какие-либо клиентские сетевые библиотеки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или сетевые протоколы. Клиентские сетевые библиотеки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливаются во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; сетевые протоколы ― во время установки Microsoft Windows (или через элемент **Сеть** на **панели управления**). Конкретный сетевой протокол может быть недоступен при установке Windows. Дополнительные сведения об установке этих сетевых протоколов см. в документации поставщика.  
  
###  <a name="Configure"></a> Настройка клиента для использования TCP/IP  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разверните узел **Конфигурация SQL Server Native Client**, щелкните правой кнопкой мыши элемент **Клиентские протоколы** и выберите пункт **Свойства**.  
  
2.  В поле **Включенные протоколы** используйте кнопки со стрелками вниз и вверх, чтобы изменить порядок применения протоколов при попытках установить соединение с SQL Server. Верхний протокол в окне **Разрешенные протоколы** является протоколом по умолчанию.  
  
 Протокол общедоступной памяти активируется отдельно, установкой флажка **Включенный протокол общей памяти** .  
  
## <a name="see-also"></a>См. также:  
 [Настройка параметра конфигурации сервера «remote login timeout»](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md)  
  
  
