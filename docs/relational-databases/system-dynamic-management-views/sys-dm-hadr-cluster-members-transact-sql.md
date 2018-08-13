---
title: sys.dm_hadr_cluster_members (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_cluster_members_TSQL
- sys.dm_hadr_cluster_members
- dm_hadr_cluster_members_TSQL
- dm_hadr_cluster_members
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_cluster_members catalog view
ms.assetid: feb20b3a-8835-41d3-9a1c-91d3117bc170
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 8bb7ad8870f4e139a00003fba0b17675eb629070
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39543594"
---
# <a name="sysdmhadrclustermembers-transact-sql"></a>sys.dm_hadr_cluster_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Если на узле WSFC, где размещен локальный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с включенной поддержкой [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], имеется кворум WSFC, то возвращаются по строке для каждого из составляющих кворум элементов и состояние каждого из них. Это включает все узлы в кластере (возвратил с типом CLUSTER_ENUM_NODE по **Clusterenum** функции) и диске или общую папку следящего сервера, если таковые имеются. Возвращаемая для определенного элемента строка содержит сведения о состоянии такого элемента. Например, для кластера из пяти узлов с кворумом по большинству узлов в котором один узел не работает, при **sys.dm_hadr_cluster_members** запрашивается от экземпляра сервера, которая включена для [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] , находится на узле с кворумом, **sys.dm_hadr_cluster_members** отражает состояние нерабочего узла отображается как «NODE_DOWN».  
  
 Если узел WSFC не набирает кворум, строки не возвращаются.  
  
 Воспользуйтесь этим динамическим административным представлением, чтобы ответить на следующие вопросы.  
  
-   Какие узлы в настоящий момент запущены в кластере WSFC?  
  
-   Сколько еще сбоев может выдержать кластер WSFC до потери кворума, когда кворум составляет большинство узлов?  

 > [!TIP]
 > Начиная с версии [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], это динамическое административное представление поддерживает всегда экземпляры отказоустойчивого кластера в дополнение к групп доступности AlwaysOn.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar(128)**|Имя элемента, которое может быть именем компьютера, буквой диска или путем к общей папке.|  
|**member_type**|**tinyint**|Тип элемента. Одно из следующих значений:<br /><br /> 0 = узел WSFC<br /><br /> 1 = следящий диск<br /><br /> 2 = следящая общая папка|  
|**member_type_desc**|**nvarchar(50)**|Описание **member_type**, используя один из:<br /><br /> CLUSTER_NODE<br /><br /> DISK_WITNESS<br /><br /> FILE_SHARE_WITNESS|  
|**member_state**|**tinyint**|Состояние элемента, одно из следующих значений:<br /><br /> 0 = вне сети<br /><br /> 1 = в сети|  
|**member_state_desc**|**nvarchar(60)**|Описание **member_state**, используя один из:<br /><br /> UP<br /><br /> ВНИЗ|  
|**number_of_quorum_votes**|**tinyint**|Число голосов, принадлежащих этому члену кворума. Отсутствие большинства — Только дисковых, это значение по умолчанию 0. Для других типов кворума это значение по умолчанию равно 1.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
  
## <a name="see-also"></a>См. также  
 [Динамические представления управления и функции, связанные с группами доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Представления каталога групп доступности AlwaysOn (Transact-SQL)](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Отслеживание групп доступности (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Группы доступности AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
