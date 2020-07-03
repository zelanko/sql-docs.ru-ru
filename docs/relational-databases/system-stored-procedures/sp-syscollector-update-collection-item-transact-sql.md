---
title: sp_syscollector_update_collection_item (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: efbdc613c641482df6b4dfe88a7f132124276578
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892813"
---
# <a name="sp_syscollector_update_collection_item-transact-sql"></a>sp_syscollector_update_collection_item (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
 Уникальный идентификатор, определяющий элемент коллекции. *collection_item_id* имеет **тип int** и значение по умолчанию NULL. *collection_item_id* должны иметь значение, если *Name* имеет значение null.  
  
 [ @name =] "*имя*"  
 Имя элемента сбора. Аргумент *Name* имеет тип **sysname** и значение по умолчанию NULL. *имя* должно иметь значение, если *collection_item_id* имеет значение null.  
  
 [ @new_name =] "*new_name*"  
 Новое имя для элемента сбора. Аргумент *new_name* имеет тип **sysname**и, если он используется, не может быть пустой строкой.  
  
 *new_name* должны быть уникальными. Чтобы получить список имен элементов текущего сбора, выполните запрос системного представления syscollector_collection_items.  
  
 [ @frequency =] *Частота*  
 Частота в секундах, с которой данные собираются этим элементом сбора. параметр *Frequency* имеет **тип int**и значение по умолчанию 5, которое может быть указано.  
  
 [ @parameters =] "*Parameters*"  
 Входные параметры для элемента сбора. *Параметры* имеют **Формат XML** и значение по умолчанию NULL. Схема *параметров* должна соответствовать схеме параметров типа сборщика.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или 1 (сбой)  
  
## <a name="remarks"></a>Комментарии  
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
 Следующие примеры основаны на элементе сбора, созданном в примере, определенном в [sp_syscollector_create_collection_item &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md).  
  
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
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [sp_syscollector_create_collection_item &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md)   
 [syscollector_collection_items (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)  
  
  
