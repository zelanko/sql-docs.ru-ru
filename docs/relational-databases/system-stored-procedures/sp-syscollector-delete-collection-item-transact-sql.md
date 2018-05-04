---
title: sp_syscollector_delete_collection_item (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syscollector_delete_collection_item
- sp_syscollector_delete_collection_item_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_delete_collecton_item
- data collector [SQL Server], stored procedures
ms.assetid: 9c2b0990-1d3d-4a59-94a0-3cca6fef4681
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 087abae457246abee0e2ee884416367b7227cde6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="spsyscollectordeletecollectionitem-transact-sql"></a>sp_syscollector_delete_collection_item (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет элемент сбора из набора сбора.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_delete_collection_item [[ @collection_item_id = ] collection_item_id ]  
    , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @collection_item_id =] *collection_item_id*  
 Уникальный идентификатор элемента сбора. *collection_item_id* — **int** значение по умолчанию NULL. *collection_item_id* должно иметь значение, если *имя* имеет значение NULL.  
  
 [ @name =] '*имя*"  
 Имя элемента сбора. *имя* — **sysname** со значением по умолчанию NULL. *имя* должно иметь значение, если *collection_item_id* имеет значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Функция sp_syscollector_delete_collection_item должна выполняться в контексте системной базы данных msdb. Удалять элементы сбора из системных наборов сбора невозможно.  
  
 Во время этой операции набор сбора, содержащий элемент сбора, останавливается и перезапускается.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных dc_admin (с разрешением EXECUTE).  
  
## <a name="examples"></a>Примеры  
 В следующем примере удаляется элемент сбора с именем `MyCollectionItem1`.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_delete_collection_item @name = 'MyCollectionItem1';  
```  
  
## <a name="see-also"></a>См. также  
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [sp_syscollector_create_collection_item &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md)   
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [syscollector_collection_items (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)  
  
  
