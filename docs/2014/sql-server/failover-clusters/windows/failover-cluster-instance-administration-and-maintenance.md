---
title: Администрирование и обслуживание экземпляров отказоустойчивого кластера | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- user accounts [SQL Server], failover clustering
- clusters [SQL Server], maintaining
- nodes [Faillover Clustering]
- failover clustering [SQL Server], maintaining
- adding nodes
- virtual servers [SQL Server], removing nodes
- clustered instance of SQL Server
- nodes [Faillover Clustering], removing
- nodes [Faillover Clustering], adding
- service accounts [SQL Server]
- removing nodes
- virtual servers [SQL Server], adding nodes
ms.assetid: 2d5c63e9-8061-45c3-94db-8dd3100b8a91
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a954eb61a7cf5b4ed39ca2cd62ab763d753ac3d1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317564"
---
# <a name="failover-cluster-instance-administration-and-maintenance"></a>Администрирование и обслуживание экземпляров отказоустойчивого кластера
  Задачи обслуживания, такие как добавление или удаление узлов из существующего отработки отказа экземпляра кластера AlwaysOn (FCI), выполняются с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] программу установки. Другие задачи администрирования, например смена ресурса IP-адреса и восстановление в некоторых сценариях FCI, выполняются с помощью оснастки управления «Диспетчер отказоустойчивости кластеров» для службы кластера WSFC.  
  
## <a name="maintaining-a-failover-cluster-instance"></a>Обслуживание экземпляра отказоустойчивого кластера  
 После установки экземпляра FCI его можно изменять и восстанавливать с помощью программы установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Например, можно добавить дополнительные узлы к экземпляру FCI, запустить его как изолированный экземпляр или удалить узел из конфигурации FCI.  
  
### <a name="adding-a-node-to-an-existing-failover-cluster-instance"></a>Добавление узла к существующему экземпляру отказоустойчивого кластера  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предоставляет режим обслуживания существующего экземпляра FCI. Если выбран этот режим, в конфигурацию FCI можно добавить другие узлы, запустив программу установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на компьютере, который нужно добавить в кластер. Дополнительные сведения см. в разделе [Создание отказоустойчивого кластера SQL Server (программа установки)](../install/create-a-new-sql-server-failover-cluster-setup.md) и [Добавление или удаление узлов отказоустойчивого кластера SQL Server (программа установки)](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### <a name="removing-a-node-from-an-existing-failover-cluster-instance"></a>Удаление узла из существующего экземпляра отказоустойчивого кластера  
 Удалить узел из конфигурации FCI можно путем запуска на компьютере, который необходимо удалить из FCI, программы установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Каждый узел в FCI считается одноранговым узлом без зависимостей от других узлов FCI, поэтому можно удалить любой узел. Поврежденный узел не может быть удален, а процесс удаления не может удалить [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с недоступного узла. Удаленный узел можно в любой момент опять включить в состав FCI. Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server (настройка)](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### <a name="changing-service-accounts"></a>Изменение учетных записей служб  
 Не изменяйте пароли для любых учетных записей служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , если любой из узлов FCI отключен или находится в режиме «вне сети». Если все же необходимо это сделать, переустановите пароль еще раз при помощи диспетчера конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , когда все узлы вновь будут находиться в режиме «в сети».  
  
 Если учетная запись службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не является администратором кластера, административные общие папки нельзя будет удалить ни на одном узле кластера. Для нормальной работы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в кластере должны быть доступны административные общие папки.  
  
> [!IMPORTANT]  
>  Не используйте одну и ту же учетную запись для учетной записи службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и для учетной записи службы WSFC. Если сменить пароль для учетной записи службы WSFC, экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] перестанет работать.  
  
 В [!INCLUDE[nextref_longhorn](../../../includes/nextref-longhorn-md.md)]идентификаторы безопасности службы используются для учетных записей служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Настройка учетных записей службы Windows и разрешений](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## <a name="administering-a-failover-cluster-instance"></a>Администрирование экземпляра отказоустойчивого кластера  
  
|Описание задачи|Ссылка на раздел|  
|----------------------|----------------|  
|Описывает, как добавить зависимости к ресурсу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[добавить зависимости к ресурсу SQL Server](add-dependencies-to-a-sql-server-resource.md)|  
|Kerberos – это сетевой протокол, позволяющий реализовать надежную проверку подлинности в клиентских и серверных приложениях. Kerberos обеспечивает совместимость и в то же время повышает безопасность проверки подлинности в масштабе всей корпоративной сети. Можно использовать проверку подлинности Kerberos с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] изолированными экземплярами или экземплярами FCI AlwaysOn.|[Регистрация имя участника-службы для соединений Kerberos](../../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).|  
|Предоставляет ссылки на содержимое, которое описывает включение проверки подлинности Kerberos||  
|Описывает процедуру, используемую для восстановления после сбоя отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[Восстановление по журналу после сбоя экземпляра отказоустойчивого кластера](recover-from-failover-cluster-instance-failure.md)|  
|Описывает процедуру смены ресурса IP-адреса для экземпляра отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|[Изменение IP-адреса экземпляра отказоустойчивого кластера](change-the-ip-address-of-a-failover-cluster-instance.md)|  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров свойства HealthCheckTimeout](configure-healthchecktimeout-property-settings.md)   
 [Настройка параметров свойства FailureConditionLevel](configure-failureconditionlevel-property-settings.md)   
 [Просмотр и чтение журнала диагностики экземпляра отказоустойчивого кластера](view-and-read-failover-cluster-instance-diagnostics-log.md)  
  
  
