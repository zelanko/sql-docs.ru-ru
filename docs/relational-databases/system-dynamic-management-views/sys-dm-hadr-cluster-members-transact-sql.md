---
title: sys. dm_hadr_cluster_members (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/31/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ffa67137c4b7d99cd0aa394319e9415a72b73103
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829400"
---
# <a name="sysdm_hadr_cluster_members-transact-sql"></a>sys.dm_hadr_cluster_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Если на узле WSFC, где размещен локальный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с включенной поддержкой [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], имеется кворум WSFC, то возвращаются по строке для каждого из составляющих кворум элементов и состояние каждого из них. Сюда входят все узлы в кластере (возвращаемые функцией **клустеренум** с типом CLUSTER_ENUM_NODE), а также диск или файловый ресурс-свидетель, если таковые имеются. Возвращаемая для определенного элемента строка содержит сведения о состоянии такого элемента. Например, для кластера из пяти узлов с кворумом "Большинство узлов", когда один узел не работает, при запросе к **sys. dm_hadr_cluster_members** из экземпляра сервера, который включен для этого узла, расположенного [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] на узле с кворумом, **sys. dm_hadr_cluster_members** отражает состояние узла "NODE_DOWN".  
  
 Если узел WSFC не набирает кворум, строки не возвращаются.  
  
 Воспользуйтесь этим динамическим административным представлением, чтобы ответить на следующие вопросы.  
  
-   Какие узлы в настоящий момент запущены в кластере WSFC?  
  
-   Сколько еще сбоев может выдержать кластер WSFC до потери кворума, когда кворум составляет большинство узлов?  

 > [!TIP]
 > Начиная с версии [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , это динамическое административное представление поддерживает Always on экземпляры отказоустойчивого кластера в дополнение к группам доступности Always on.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar(128)**|Имя элемента, которое может быть именем компьютера, буквой диска или путем к общей папке.|  
|**member_type**|**tinyint**|Тип элемента. Одно из следующих значений:<br /><br /> 0 = узел WSFC<br /><br /> 1 = следящий диск<br /><br /> 2 = следящая общая папка<br /><br /> 3 = облачный следящий сервер|  
|**member_type_desc**|**nvarchar(50)**|Описание **MEMBER_TYPE**, одно из следующих:<br /><br /> CLUSTER_NODE<br /><br /> DISK_WITNESS<br /><br /> FILE_SHARE_WITNESS<br /><br /> CLOUD_WITNESS|  
|**member_state**|**tinyint**|Состояние элемента, одно из следующих значений:<br /><br /> 0 = вне сети<br /><br /> 1 = в сети|  
|**member_state_desc**|**nvarchar(60)**|Описание **member_state**, одно из следующих:<br /><br /> UP<br /><br /> СБОЙ|  
|**number_of_quorum_votes**|**tinyint**|Число голосов, принадлежащих этому члену кворума. Для отсутствия большинства: кворумов только на диск. по умолчанию используется значение 0. Для других типов кворума это значение по умолчанию равно 1.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
  
## <a name="see-also"></a>См. также:  
 [Always On динамические административные представления и функции групп доступности &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Always On представления каталога групп доступности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Мониторинг групп доступности &#40;&#41;Transact-SQL](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Группы доступности AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
