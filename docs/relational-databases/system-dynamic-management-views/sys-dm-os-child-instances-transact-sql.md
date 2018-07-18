---
title: sys.dm_os_child_instances (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_child_instances
- sys.dm_os_child_instances_TSQL
- dm_os_child_instances
- dm_os_child_instances_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server state information [SQL Server]
- sys.dm_os_child_instances dynamic management view
- monitoring server health
ms.assetid: 1bef3074-0ccc-48fa-8f3d-14f3d99df86b
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 66f4d8c770cc10c2ba47769576d8f9625edac0cf
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34463790"
---
# <a name="sysdmoschildinstances-transact-sql"></a>sys.dm_os_child_instances (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждого пользовательского экземпляра, созданного из родительского экземпляра сервера.  
  
> **ВАЖНО!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Возвращает сведения о **sys.dm_os_child_instances** можно использовать для определения состояния каждого пользовательского экземпляра (heart_beat) и получить имя канала (связи instance_pipe_name), который может использоваться для создания подключения для пользователя Экземпляр с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или SQLCmd. Подключиться к пользовательскому экземпляру можно сразу после того, как он был запущен внешним процессом, таким как клиентское приложение. Инструменты управления SQL не могут запустить пользовательский экземпляр.  
  
> **Примечание:** пользовательские экземпляры являются возможностью [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] только.  
  
> **Примечание** вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_child_instances**.  
  
|Столбец|Data type|Описание|  
|------------|---------------|-----------------|  
|**owning_principal_name**|**nvarchar(256)**|Имя пользователя, для которого был создан этот пользовательский экземпляр.|  
|owning_principal_sid|nvarchar(256)|Идентификатор безопасности основного сервера, которому принадлежит эта база данных. Он соответствует идентификатору безопасности Windows.|  
|owning_principal_sid_binary|varbinary(85)|Двоичная версия идентификатора безопасности пользователя, которому принадлежит пользовательский экземпляр|  
|**имя_экземпляра**|**nvarchar(128)**|Имя этого пользовательского экземпляра.|  
|**instance_pipe_name**|**nvarchar(260)**|При создании пользовательского экземпляра создается именованный канал для подключения приложений. Это имя можно использовать в строке подключения для соединения с соответствующим пользовательским экземпляром.|  
|**os_process_id**|**Int**|Номер процесса Windows для этого пользовательского экземпляра.|  
|**os_process_creation_date**|**DateTime**|Дата и время последнего запуска процесса этого пользовательского экземпляра.|  
|**heart_beat**|**nvarchar(5)**|Текущее состояние этого пользовательского экземпляра; либо ALIVE, либо DEAD.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о динамическом административном представлении см. в разделе [динамические административные представления и функции &#40;Transact-SQL&#41; ](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации.  
  
## <a name="see-also"></a>См. также  
 [Пользовательские экземпляры для администраторов](http://msdn.microsoft.com/en-us/85385aae-10fb-4f8b-9eeb-cce2ee7da019)  
  
  



