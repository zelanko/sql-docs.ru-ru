---
title: sys. dm_os_stacks (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_stacks
- dm_os_stacks_TSQL
- sys.dm_os_stacks
- sys.dm_os_stacks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_stacks dynamic management view
ms.assetid: a69b06c4-28f0-4535-8fa1-9f132db4d916
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8f287c548a7ebb71b1ebf3e1bce30e43b412c755
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265720"
---
# <a name="sysdm_os_stacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Это динамическое административное представление используется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для следующих внутренних целей.  
  
-   Отслеживание отладочных данных, например необработанных запросов на выделение памяти;  
  
-   Установление или проверка логики, применяющейся компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] там, где компонент предполагает определенный вызов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary(8)**|Уникальный адрес для данного размещения в стеке. Не допускает значение NULL.|  
|**frame_index**|**int**|Каждая строка представляет вызов функции, который при сортировке в возрастающем порядке по индексу кадра для конкретного **stack_address**возвращает полный стек вызовов. Не допускает значение NULL.|  
|**frame_address**|**varbinary(8)**|Адрес вызова функции. Не допускает значение NULL.|  
  
## <a name="remarks"></a>Remarks  
 **sys. dm_os_stacks** требует наличия на сервере символов сервера и других компонентов для правильного отображения информации.  
  
## <a name="permissions"></a>Разрешения

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   


## <a name="see-also"></a>См. также:  
  [SQL Server динамические административные представления, связанные с операционной системой &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
