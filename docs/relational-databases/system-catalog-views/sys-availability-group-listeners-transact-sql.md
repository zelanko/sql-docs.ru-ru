---
title: sys.availability_group_listeners (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_group_listeners_TSQL
- sys.availability_group_listeners
- sys.availability_group_listeners_TSQL
- availability_group_listeners
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_group_listeners catalog view
- Availability Groups [SQL Server], listeners
ms.assetid: b5e7d1fb-3ffb-4767-8135-604c575016b1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 839e471e8861f081762f6129dff731e66bed77a7
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52403489"
---
# <a name="sysavailabilitygrouplisteners-transact-sql"></a>sys.availability_group_listeners (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Для каждого AlwaysOn группы доступности возвращает либо ноль строк, указывающую, что имя сети не связана с группой доступности, или возвращает по строке для каждой конфигурации прослушивателя группы доступности в Windows Server отказоустойчивого кластера (WSFC) кластер. Это представление отображает получаемые из кластера в реальном времени сведения о конфигурации.  
  
> [!NOTE]  
>  В этом представлении каталога не описывается подробно конфигурация IP-адресов, заданная в кластере WSFC.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Идентификатор группы доступности (**group_id**) из [sys.availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md).|  
|**listener_id**|**nvarchar(36)**|Идентификатор GUID из идентификатора ресурса кластера.|  
|**dns_name**|**nvarchar(63)**|Настроенное сетевое имя (hostname) прослушивателя группы доступности.|  
|**port**|**int**|Номер TCP-порта, заданного для прослушивателя группы доступности.<br /><br /> NULL = прослушиватель настроен вне [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], его номер порта не был добавлен в группу доступности. Чтобы добавить порт, pleaseuse параметром MODIFY [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции.|  
|**is_conformant**|**bit**|Соответствует ли стандартам эта конфигурация IP-адресов, одно из следующих значений:<br /><br /> 1 = прослушиватель соответствует стандартам. Только отношения «Или» существует между его адреса протокола Интернета (IP). *Соответствующие стандарту* охватывает каждый IP-конфигурацию, которая была создана с [CREATE AVAILABILITY GROUP](../../t-sql/statements/create-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции. Кроме того, если конфигурация IP-адресов была создана вне [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например с помощью диспетчера отказоустойчивого кластера WSFC (но ее можно изменить с помощью инструкции ALTER AVAILABILITY GROUP), то конфигурация IP-адресов считается соответствующей стандартам.<br /><br /> 0 = прослушиватель не соответствует стандартам. Как правило, это указывает на наличие IP-адреса, который не удалось настроить с помощью команд [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и который вместо этого был определен непосредственно в кластере WSFC.|  
|**ip_configuration_string_from_cluster**|**nvarchar(max)**|Строки конфигурации IP-адресов кластера для этого прослушивателя, если они имеются. NULL = прослушиватель не имеет виртуальных IP-адресов. Пример:<br /><br /> IPv4-адрес: `65.55.39.10`.<br /><br /> IPv6-адрес:  `2001::4898:23:1002:20f:1fff:feff:b3a3`|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Динамические представления управления и функции, связанные с группами доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Представления каталога групп доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Отслеживание групп доступности (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Группы доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
