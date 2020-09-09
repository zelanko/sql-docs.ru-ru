---
description: sys.dm_os_child_instances (Transact-SQL)
title: sys. dm_os_child_instances (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9c148c6d3bab448d89294eba4af7ebec8cd2cf6c
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89539372"
---
# <a name="sysdm_os_child_instances-transact-sql"></a>sys.dm_os_child_instances (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает строку для каждого пользовательского экземпляра, созданного из родительского экземпляра сервера.  
  
> **ВАЖНО!** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Сведения, возвращаемые из **sys. dm_os_child_instances** , можно использовать для определения состояния каждого пользовательского экземпляра (heart_beat) и получения имени канала (instance_pipe_name), которое можно использовать для создания соединения с пользовательским экземпляром с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или SQLCmd. Подключиться к пользовательскому экземпляру можно сразу после того, как он был запущен внешним процессом, таким как клиентское приложение. Инструменты управления SQL не могут запустить пользовательский экземпляр.  
  
> **Примечание.** Пользовательские экземпляры являются [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] только функцией.  
> 
> **Примечание** . Чтобы вызвать эту функцию из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , используйте имя **sys. dm_pdw_nodes_os_child_instances**.  
  
|Столбец|Тип данных|Описание|  
|------------|---------------|-----------------|  
|**owning_principal_name**|**nvarchar(256)**|Имя пользователя, для которого был создан этот пользовательский экземпляр.|  
|owning_principal_sid|nvarchar(256)|Идентификатор безопасности основного сервера, которому принадлежит эта база данных. Он соответствует идентификатору безопасности Windows.|  
|owning_principal_sid_binary|varbinary(85)|Двоичная версия идентификатора безопасности пользователя, которому принадлежит пользовательский экземпляр|  
|**instance_name**|**nvarchar(128)**|Имя этого пользовательского экземпляра.|  
|**instance_pipe_name**|**nvarchar(260)**|При создании пользовательского экземпляра создается именованный канал для подключения приложений. Это имя можно использовать в строке подключения для соединения с соответствующим пользовательским экземпляром.|  
|**os_process_id**|**Int**|Номер процесса Windows для этого пользовательского экземпляра.|  
|**os_process_creation_date**|**DateTime**|Дата и время последнего запуска процесса этого пользовательского экземпляра.|  
|**heart_beat**|**nvarchar (5)**|Текущее состояние этого пользовательского экземпляра; либо ALIVE, либо DEAD.|  
|**pdw_node_id**|**int**|**Применимо к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] , [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения о динамическом административном представлении см. в разделе [динамические административные представления и функции &#40;&#41;Transact-SQL ](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по.  
  
## <a name="see-also"></a>См. также  
 [Пользовательские экземпляры для тех, кто не обладает правами администратора](https://msdn.microsoft.com/85385aae-10fb-4f8b-9eeb-cce2ee7da019)  
  
  



