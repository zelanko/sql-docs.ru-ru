---
title: sys.dm_hadr_cluster_networks (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_hadr_cluster_networks
- sys.dm_hadr_cluster_networks_TSQL
- sys.dm_hadr_cluster_networks
- dm_hadr_cluster_networks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_cluster_networks dynamic management view
ms.assetid: ece32b15-d63f-4f93-92b7-e2930333e97a
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b02faa8108154ae4efba474a01dac8edf5610ea6
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34466151"
---
# <a name="sysdmhadrclusternetworks-transact-sql"></a>sys.dm_hadr_cluster_networks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждого из элементов кластера WSFC, участвующего в конфигурации подсети группы доступности. Это динамическое административное представление можно использовать для проверки виртуального сетевого IP-адреса, настроенного для каждой из реплик доступности.  
  
 Первичный ключ: **member_name** + **network_subnet_IP** + **network_subnet_prefix_length**  
  
 > [!TIP]
 > Начиная с версии [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], это динамическое административное представление поддерживает всегда экземпляры отказоустойчивого кластера в дополнение к группы доступности AlwaysOn.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar(128)**|Имя компьютера, принадлежащее узлу в кластере WSFC.|  
|**network_subnet_ip**|**nvarchar(48)**|IP-адрес подсети, к которой принадлежит компьютер. Это может быть адрес IPv4 или IPv6.|  
|**network_subnet_ipv4_mask**|**nvarchar(45)**|Маска подсети, задающая подсеть, к которой принадлежит IP-адрес. **network_subnet_ipv4_mask** для указания параметров DHCP < network_subnet_option > в предложении DHCP с [CREATE AVAILABILITY GROUP](../../t-sql/statements/create-availability-group-transact-sql.md) или [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.<br /><br /> NULL = подсеть IPv6.|  
||||  
|**network_subnet_prefix_length**|**int**|Длина префикса сетевого IP-адреса, задающего подсеть, к которой принадлежит компьютер.|  
|**is_public**|**бит**|Является ли сеть в кластере WSFC общедоступной или закрытой, одно из следующих значений:<br /><br /> 0 = закрытая<br /><br /> 1 = общедоступная|  
|**is_ipv4**|**бит**|Тип подсети, одно из следующих значений:<br /><br /> 1 = IPv4<br /><br /> 0 = IPv6|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Отслеживание групп доступности & #40; Transact-SQL & #41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [sys.dm_os_cluster_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [Запросив системный каталог SQL Server часто задаваемые вопросы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
