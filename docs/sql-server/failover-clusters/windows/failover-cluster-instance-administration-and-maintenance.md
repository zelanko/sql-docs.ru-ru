---
title: "Администрирование и обслуживание экземпляров отказоустойчивого кластера | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "учетные записи пользователей [SQL Server], отказоустойчивая кластеризация"
  - "кластеры [SQL Server], обслуживание"
  - "узлы [отказоустойчивый кластер]"
  - "отказоустойчивая кластеризация [SQL Server], обслуживание"
  - "добавление узлов"
  - "виртуальные серверы [SQL Server], удаление узлов"
  - "кластеризованный экземпляр SQL Server"
  - "узлы [отказоустойчивый кластер], удаление"
  - "узлы [отказоустойчивый кластер], добавление"
  - "учетные записи служб [SQL Server]"
  - "удаление узлов"
  - "виртуальные серверы [SQL Server], добавление узлов"
ms.assetid: 2d5c63e9-8061-45c3-94db-8dd3100b8a91
caps.latest.revision: 35
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 35
---
# Администрирование и обслуживание экземпляров отказоустойчивого кластера
  Такие задачи сопровождения, как добавление или удаление узлов из существующего экземпляра отказоустойчивого кластера AlwaysOn (FCI), выполняются с помощью программы установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Другие задачи администрирования, например смена ресурса IP-адреса и восстановление в некоторых сценариях FCI, выполняются с помощью оснастки управления «Диспетчер отказоустойчивости кластеров» для службы кластера WSFC.  
  
## Обслуживание экземпляра отказоустойчивого кластера  
 После установки экземпляра FCI его можно изменять и восстанавливать с помощью программы установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Например, можно добавить дополнительные узлы к экземпляру FCI, запустить его как изолированный экземпляр или удалить узел из конфигурации FCI.  
  
### Добавление узла к существующему экземпляру отказоустойчивого кластера  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет режим обслуживания существующего экземпляра FCI. Если выбран этот режим, в конфигурацию FCI можно добавить другие узлы, запустив программу установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на компьютере, который нужно добавить в кластер. Дополнительные сведения см. в разделе [Создание отказоустойчивого кластера SQL Server (программа установки)](../../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) и [Добавление или удаление узлов отказоустойчивого кластера SQL Server (программа установки)](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### Удаление узла из существующего экземпляра отказоустойчивого кластера  
 Удалить узел из конфигурации FCI можно путем запуска на компьютере, который необходимо удалить из FCI, программы установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Каждый узел в FCI считается одноранговым узлом без зависимостей от других узлов FCI, поэтому можно удалить любой узел. Поврежденный узел не может быть удален, а процесс удаления не может удалить [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с недоступного узла. Удаленный узел можно в любой момент опять включить в состав FCI. Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server (настройка)](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### Изменение учетных записей служб  
 Не изменяйте пароли для любых учетных записей служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , если любой из узлов FCI отключен или находится в режиме «вне сети». Если все же необходимо это сделать, переустановите пароль еще раз при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , когда все узлы вновь будут находиться в режиме «в сети».  
  
 Если учетная запись службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не является администратором кластера, административные общие папки нельзя будет удалить ни на одном узле кластера. Для нормальной работы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в кластере должны быть доступны административные общие папки.  
  
> [!IMPORTANT]  
>  Не используйте одну и ту же учетную запись для учетной записи службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и для учетной записи службы WSFC. Если сменить пароль для учетной записи службы WSFC, экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] перестанет работать.  
  
 В [!INCLUDE[nextref_longhorn](../../../includes/nextref-longhorn-md.md)]идентификаторы безопасности службы используются для учетных записей служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Настройка учетных записей службы Windows и разрешений](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## Администрирование экземпляра отказоустойчивого кластера  
  
|Описание задачи|Ссылка на раздел|  
|----------------------|----------------|  
|Описывает, как добавить зависимости к ресурсу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|[добавить зависимости к ресурсу SQL Server](../../../sql-server/failover-clusters/windows/add-dependencies-to-a-sql-server-resource.md)|  
|Kerberos – это сетевой протокол, позволяющий реализовать надежную проверку подлинности в клиентских и серверных приложениях. Kerberos обеспечивает совместимость и в то же время повышает безопасность проверки подлинности в масштабе всей корпоративной сети. Можно использовать проверку подлинности Kerberos с изолированными экземплярами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или экземплярами FCI AlwaysOn.|[Регистрация имя участника-службы для соединений Kerberos](../../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).|  
|Предоставляет ссылки на содержимое, которое описывает включение проверки подлинности Kerberos||  
|Описывает процедуру, используемую для восстановления после сбоя отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|[Восстановление по журналу после сбоя экземпляра отказоустойчивого кластера](../../../sql-server/failover-clusters/windows/recover-from-failover-cluster-instance-failure.md)|  
|Описывает процедуру смены ресурса IP-адреса для экземпляра отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|[Изменение IP-адреса экземпляра отказоустойчивого кластера](../../../sql-server/failover-clusters/windows/change-the-ip-address-of-a-failover-cluster-instance.md)|  
  
## См. также:  
 [Настройка параметров свойства HealthCheckTimeout](../../../sql-server/failover-clusters/windows/configure-healthchecktimeout-property-settings.md)   
 [Настройка параметров свойства FailureConditionLevel](../../../sql-server/failover-clusters/windows/configure-failureconditionlevel-property-settings.md)   
 [Просмотр и чтение журнала диагностики экземпляра отказоустойчивого кластера](../../../sql-server/failover-clusters/windows/view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  