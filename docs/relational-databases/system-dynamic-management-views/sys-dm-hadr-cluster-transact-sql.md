---
title: sys.dm_hadr_cluster (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_cluster
- dm_hadr_cluster_HADR
- sys.dm_hadr_cluster_TSQL
- dm_hadr_cluster
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_cluster catalog view
- Availability Groups [SQL Server], WSFC clusters
ms.assetid: 13ce70e4-9d43-4a80-a826-099e6213bf85
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2c4e66ed6471ec0959cfece477af4b939fb129c6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47748242"
---
# <a name="sysdmhadrcluster-transact-sql"></a>sys.dm_hadr_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Если узел сервера отказоустойчивой кластеризации Windows (WSFC), на котором размещается экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с поддержкой [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] имеет кворум WSFC, **sys.dm_hadr_cluster** возвращает строку, содержащую имя кластера и сведения о кворуме. Если узел WSFC не набирает кворума, строка не возвращается.  
 > [!TIP]
 > Начиная с версии [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], это динамическое административное представление поддерживает всегда экземпляры отказоустойчивого кластера в дополнение к групп доступности AlwaysOn.

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**cluster_name**|**nvarchar(128)**|Имя кластера WSFC, содержащего экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в которых включена поддержка [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].|  
|**quorum_type**|**tinyint**|Тип кворума, используемый этим кластером WSFC. Одно из следующих значений:<br /><br /> 0 = большинство узлов. Эта конфигурация кворума может выдержать отказ половины узлов (с округлением вверх) минус одного. Например, в кластере из семи узлов такая конфигурация кворума выдерживает отказ трех узлов.<br /><br /> 1 = большинство узлов и дисков. Если следящий диск остается доступным, то эта конфигурация кворума может выдержать отказ половины узлов (с округлением вверх). Например, кластер из шести узлов, в котором следящий диск остается в режиме «в сети», может выдержать отказы трех узлов. Если произошел отказ следящего диска или он оказался в режиме «вне сети», то такая конфигурация может выдержать отказ половины узлов (с округлением вверх) минус одного. Например, кластер из шести узлов, в котором произошел отказ следящего диска, может выдержать отказы двух (3-1=2) узлов.<br /><br /> 2 = большинство узлов и общих папок. Такая конфигурация кворума работает аналогично большинству дисков и узлов, но роль следящего диска в ней играет следящая общая папка.<br /><br /> 3 = без большинства: только диск. Если диск кворума доступен в сети, то такая конфигурация кворума может выдержать отказ всех узлов, кроме одного.|  
|**quorum_type_desc**|**varchar(50)**|Описание **quorum_type**, используя один из:<br /><br /> NODE_MAJORITY<br /><br /> NODE_AND_DISK_MAJORITY<br /><br /> NODE_AND_FILE_SHARE_MAJORITY<br /><br /> NO_MAJORITY:_DISK_ONLY|  
|**quorum_state**|**tinyint**|Состояние кворума WSFC, одно из следующих значений:<br /><br /> 0 = неизвестное состояние кворума<br /><br /> 1 = нормальный кворум<br /><br /> 2 = принудительный кворум|  
|**quorum_state_desc**|**varchar(50)**|Описание **quorum_state**, используя один из:<br /><br /> UNKNOWN_QUORUM_STATE<br /><br /> NORMAL_QUORUM<br /><br /> FORCED_QUORUM|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Динамические представления управления и функции, связанные с группами доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Представления каталога групп доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Отслеживание групп доступности (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [sys.dm_hadr_cluster_members (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql.md)  
  
  
