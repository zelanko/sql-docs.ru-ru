---
title: sp_syscollector_update_collection_item (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collection_item
- sp_syscollector_update_collection_item_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_update_collection_item
ms.assetid: 7a0d36c8-c6e9-431d-a5a4-6c1802bce846
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d94ce7762facb878e0e6d8deb60647ee2d05482e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spsyscollectorupdatecollectionitem-transact-sql"></a>sp_syscollector_update_collection_item (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Служит для изменения свойств или переименования определяемого пользователем элемента сбора.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_update_collection_item   
      [ [ @collection_item_id = ] collection_item_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @new_name = ] 'new_name' ]  
    , [ [ @frequency = ] frequency ]  
    , [ [ @parameters = ] 'parameters' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @collection_item_id =] *collection_item_id*  
 Уникальный идентификатор, определяющий элемент коллекции. *collection_item_id* — **int** со значением по умолчанию NULL. *collection_item_id* должно иметь значение, если *имя* имеет значение NULL.  
  
 [ @name =] '*имя*"  
 Имя элемента сбора. *имя* — **sysname** со значением по умолчанию NULL. *имя* должно иметь значение, если *collection_item_id* имеет значение NULL.  
  
 [ @new_name =] '*новое_имя*"  
 Новое имя для элемента сбора. *новое_имя* — **sysname**, и при использовании не может быть пустой строкой.  
  
 *новое_имя* должно быть уникальным. Чтобы получить список имен элементов текущего сбора, выполните запрос системного представления syscollector_collection_items.  
  
 [ @frequency =] *частота*  
 Частота в секундах, с которой данные собираются этим элементом сбора. *частота* — **int**, 5, минимальное значение, которое можно указать значение по умолчанию.  
  
 [ @parameters =] '*параметры*"  
 Входные параметры для элемента сбора. *Параметры* — **xml** значение по умолчанию NULL. *Параметры* схема должна совпадать со схемой параметров типа сборщика.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Если набор сбора настроен на режим без кэширования, изменение частоты не учитывается, поскольку этот режим предусматривает выполнение сбора данных и передачу по расписанию, указанному для набора сбора. Чтобы просмотреть состояние набора сбора, выполните следующий запрос. Замените `<collection_item_id>` идентификатором обновляемого элемента сбора.  
  
```  
USE msdb;  
GO  
SELECT cs.collection_set_id, collection_set_uid, cs.name   
    ,'is running' = CASE WHEN is_running =  0 THEN 'No' ELSE 'Yes' END  
    ,'cache mode' = CASE WHEN collection_mode = 0 THEN 'Cached mode' ELSE 'Non-cached mode' END  
FROM syscollector_collection_sets AS cs  
JOIN syscollector_collection_items AS ci   
ON ci.collection_set_id = cs.collection_set_id  
WHERE collection_item_id = <collection_item_id>;  
```  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных dc_admin или dc_operator (с разрешением EXECUTE). Хотя члены роли dc_operator могут выполнять эту хранимую процедуру, они могут менять не все свойства. Следующие свойства могут изменить только члены роли dc_admin:  
  
-   @new_name  
  
-   @parameters  
  
## <a name="examples"></a>Примеры  
 Следующие примеры основаны на элемент коллекции, созданной в примере, определенные в [sp_syscollector_create_collection_item &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md).  
  
### <a name="a-changing-the-collection-frequency"></a>A. Изменение частоты сбора  
 В следующем примере изменяется частота сбора для указанного элемента сбора.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collection_item   
@name = N'My custom TSQL query collector item',  
@frequency = 3000;  
GO  
```  
  
### <a name="b-renaming-a-collection-item"></a>Б. Переименование элемента сбора  
 В следующем примере производится переименование элемента сбора.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collection_item   
@name = N'My custom TSQL query collector item',  
@new_name = N'My modified TSQL item';  
GO  
```  
  
### <a name="c-changing-the-parameters-of-a-collection-item"></a>В. Изменение параметров элемента сбора  
 В следующем примере изменяются параметры, связанные с элементом сбора. Инструкция, определенная в атрибуте `<Value>`, изменяется, а атрибуту `UseSystemDatabases` задается значение false. Чтобы просмотреть текущие параметры для данного элемента, выполните запрос столбца параметров в системном представлении syscollector_collection_items. Может потребоваться изменить значение для аргумента `@collection_item_id`.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collection_item   
@collection_item_id = 9,   
@parameters = '  
    \<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
        <Query>  
            <Value>SELECT * FROM sys.dm_db_index_usage_stats</Value>  
            <OutputTable>MyOutputTable</OutputTable>  
        </Query>  
        <Databases>  
            <Database> UseSystemDatabases = "false"   
                       UseUserDatabases = "true"</Database>  
        </Databases>  
    \</ns:TSQLQueryCollector>';  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [sp_syscollector_create_collection_item &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md)   
 [syscollector_collection_items (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)  
  
  
