---
title: Сетевая конфигурация сервера SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 07/27/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- connections [SQL Server], server network configuration
- Database Engine [SQL Server], network configurations
- server network configuration [SQL Server]
- protocols [SQL Server], choosing
- ports [SQL Server], changing
- server configuration [SQL Server]
ms.assetid: 890c09a1-6dad-4931-aceb-901c02ae34c5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 826a2b2305354807b6db7bbb167f86d165b98b45
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68025609"
---
# <a name="server-network-configuration"></a>Сетевая конфигурация сервера
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Задачи сетевой конфигурации сервера включают активацию протоколов, изменение порта или канала, используемого протоколом, настройку шифрования, настройку службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , отображение или скрытие компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в сети и регистрацию имени участника-службы сервера. Обычно изменять сетевую конфигурацию сервера не требуется. Проводить перенастройку сетевых протоколов сервера следует только в случае особых требований сети.  
  
 Настройка сети для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]применялась программа Server Network Utility, которая поставлялась вместе с ними.  
  
## <a name="protocols"></a>Протоколы  
 Диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применяется для включения или отключения протоколов, используемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и настройки параметров, доступных протоколам. Может быть активировано более одного протокола. Необходимо включить все протоколы, которые будут использоваться клиентами. Все протоколы имеют равный доступ к серверу. Сведения о том, какие протоколы следует использовать, см. в разделах [Включение или отключение сетевого протокола сервера](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) и [Сетевая конфигурация SQL Server по умолчанию](../../database-engine/configure-windows/default-sql-server-network-protocol-configuration.md).  
  
### <a name="changing-a-port"></a>Изменение порта  
 Протоколы TCP/IP могут быть настроены на прослушивание определенного порта. По умолчанию экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] по умолчанию прослушивает TCP-порт 1433. Именованные экземпляры компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и [!INCLUDE[ssEW](../../includes/ssew-md.md)] настроены для использования динамических портов. Это означает, что при запуске службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для них выбирается свободный порт. Служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет клиентам определить порт при подключении.  
  
 При настройке на динамические порты порт, используемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , может меняться при каждом запуске. При подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через брандмауэр необходимо открыть порт, используемый компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следует настраивать компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на использование определенного порта, что позволит настроить брандмауэр так, чтобы он разрешал связь с сервером. Дополнительные сведения см. в разделе [Настройка сервера для прослушивания указанного TCP-порта (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
### <a name="changing-a-named-pipe"></a>Изменение именованного канала  
 Можно настроить протокол именованного канала на прослушивание определенного именованного канала. По умолчанию экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] прослушивает канал \\\\.\pipe\sql\query для экземпляра по умолчанию и \\\\.\pipe\MSSQL$ *\<имя_экземпляра>* \sql\query для именованного экземпляра. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] может прослушивать только один именованный канал, но при желании можно изменить имя канала на другое. Служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет клиентам определить канал при подключении. Дополнительные сведения см. в разделе [Настройка сервера для прослушивания альтернативного канала (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/configure-a-server-to-listen-on-an-alternate-pipe.md).  
  
## <a name="force-encryption"></a>Принудительное шифрование  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] можно настроить так, чтобы требовать шифрования во время связи с клиентскими приложениями. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
## <a name="extended-protection-for-authentication"></a>Расширенная защита для проверки подлинности  
 Поддержка расширенной защиты для проверки подлинности с помощью привязки каналов и привязки служб доступна в операционных системах, поддерживающих расширенную защиту. Дополнительные сведения см. в разделе [Соединение с компонентом Database Engine с использованием расширенной защиты](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md).  
  
## <a name="authenticating-by-using-kerberos"></a>Проверка подлинности Kerberos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает проверку подлинности Kerberos. Дополнительные сведения о регистрации SPN для SQL Server вручную см. в разделах [Регистрация имени участника-службы для соединений Kerberos](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md) и [Диспетчер конфигураций Microsoft Kerberos для SQL Server](https://www.microsoft.com/download/details.aspx?id=39046).  
  
### <a name="registering-a-server-principal-name-spn"></a>Регистрация имени участника-службы сервера (SPN)  
 Служба проверки подлинности протокола Kerberos использует имя участника-службы для проверки подлинности служб. Дополнительные сведения см. в разделе [Регистрация имени участника-службы для соединений Kerberos](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).  
  
 Для повышения защищенности проверки подлинности пользователя при соединении с NTLM можно также использовать SPN. Дополнительные сведения см. в разделе [Соединение с компонентом Database Engine с использованием расширенной защиты](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md).  
  
## <a name="sql-server-browser-service"></a>служба «SQL Server, браузер»  
 Служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется на сервере и позволяет клиентским компьютерам находить экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не требует настройки, но она должна быть запущена для некоторых сценариев соединения. Дополнительные сведения о браузере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Служба обозревателя SQL Server (компоненты Database Engine и SSAS)](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md)  
  
## <a name="hiding-sql-server"></a>Скрытие экземпляра SQL Server  
 При выполнении браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отвечает на запросы, сообщая имя, версию и сведения о соединении для каждого установленного экземпляра. Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]флаг **Скрыть экземпляр** указывает на то, что браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не должен возвращать сведения об этом экземпляре сервера. Клиентские приложения по-прежнему могут подключиться, но при этом им следует иметь необходимые сведения для соединения. Дополнительные сведения см. в статье [Скрытие экземпляра компонента Database Engine SQL Server](../../database-engine/configure-windows/hide-an-instance-of-sql-server-database-engine.md).  
  
## <a name="related-content"></a>См. также  
 [Конфигурация клиентской сети](../../database-engine/configure-windows/client-network-configuration.md)  
  
 [Управление службами компонента Database Engine](../../database-engine/configure-windows/manage-the-database-engine-services.md)  
  
  
