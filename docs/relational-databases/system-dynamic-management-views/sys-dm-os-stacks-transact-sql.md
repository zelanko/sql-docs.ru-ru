---
title: "sys.dm_os_stacks (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_stacks
- dm_os_stacks_TSQL
- sys.dm_os_stacks
- sys.dm_os_stacks_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_stacks dynamic management view
ms.assetid: a69b06c4-28f0-4535-8fa1-9f132db4d916
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e3e292fbafbee9586d377f133af7f9d3ee520d5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Это динамическое административное представление используется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для следующих внутренних целей.  
  
-   Отслеживание отладочных данных, например необработанных запросов на выделение памяти;  
  
-   Установление или проверка логики, применяющейся компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] там, где компонент предполагает определенный вызов.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary(8)**|Уникальный адрес для данного размещения в стеке. Не допускает значение NULL.|  
|**frame_index**|**int**|Каждая строка представляет собой вызов отсортированы в порядке возрастания по индексу фреймов для конкретного **stack_address**, возвращает полный стек вызова. Не допускает значение NULL.|  
|**frame_address**|**varbinary(8)**|Адрес вызова функции. Не допускает значение NULL.|  
  
## <a name="remarks"></a>Замечания  
 **sys.dm_os_stacks** требуется на сервере для корректного отображения сведений присутствие символов сервера и других компонентов.  
  
## <a name="permissions"></a>Permissions  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Premium необходимо `VIEW DATABASE STATE` разрешений в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровней Standard и Basic, требует **администратор сервера** или **администратора Azure Active Directory** учетной записи.  
  

## <a name="see-also"></a>См. также:  
  [Относящиеся к операционной системе SQL Server динамические административные представления &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
